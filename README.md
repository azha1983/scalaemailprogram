# scalaemailprogram
Simple Program using Scala with html 


%addjar file:email_jar/mail.jar
%addjar file:email_jar/smtp.jar

 def buildInternetAddressArray(address: String): Array[InternetAddress] = {
                  return InternetAddress.parse(address)
                }
              
              var message: Message = null
              val properties = new Properties()
              properties.put("mail.smtp.host", "smtp.xxx")
              properties.put("mail.smtp.auth", "false")
              //properties.get("mail.smtp.port", "25")
              val session = Session.getDefaultInstance(properties, null)
              message = new MimeMessage(session)
              message.setFrom(new InternetAddress("anomaly@xxx"))
              
              val mailAddressTo = Array("aa@xxx","bb@xxx")

              for(tos <- mailAddressTo)
              message.addRecipient(Message.RecipientType.TO, new InternetAddress (tos))
              
              message.setSentDate(new Date())
              message.setSubject("Title")
              
              var  high1 = ""
              var  med1 = ""
              var  low1 = ""
              
              
              
val htmlheadtabl1 = "<table border=1><tbody><tr align='center' bgcolor='#FDDFEA'><td colspan='3'><h5>Total TT : "+ novatt.count +"</h5></td></tr><tr align='center' bgcolor='#FEF6F9'><td><h5>High Cluster Anomaly</h5></td><td><h5>Medium Cluster Anomaly</h5></td><td><h5>Low Cluster Anomaly</h5></td></tr>"
              
              
              valH.printSchema()
              
                
               if(highTT_check){

                high1= valH.orderBy("exchange").select("exchange", String.valueOf("total")).collect().mkString("<br>")
                
                }
              if(mediumTT_check){
                
                
                med1= valM.orderBy("exchange").select("exchange", String.valueOf("total")).collect().mkString("<br>")
                
                }
              if(lowTT_check){
                
               low1= valL.orderBy("exchange").select("exchange", String.valueOf("total")).collect().mkString("<br>")
                }
              
              var middle = "<tr align='center'><td>"+high1.replaceAll("[\\[\\]]","") + "</td><td>"+med1.replaceAll("[\\[\\]]","") + "</td><td>"+low1.replaceAll("[\\[\\]]","") + " </td></tr>"              
              var dpDetails = "<tr align='center'><td>"+hDetail1.replaceAll("[\\[\\]]","") + "</td><td>"+mDetail1.replaceAll("[\\[\\]]","") + "</td><td>"+lDetail1.replaceAll("[\\[\\]]","") + " </td></tr>"
              val htmlfoottabl1 = "</tbody></table>"
              message.setContent(htmlheadtabl1+middle+dpDetails+htmlfoottabl1, "text/html");
                     

              
              Transport.send(message);
