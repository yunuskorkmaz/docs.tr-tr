---
title: 'Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: b37d296312be4c7694a2db55d85dd618e3252f14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama

Bu konuda, bir Windows etki alanı kullanıcı adı ve parola ile bir istemci kimlik doğrulaması bir Windows Communication Foundation (WCF) hizmetini etkinleştirmek gösterilmiştir. Bu, bir çalışma, kendi kendini barındıran WCF Hizmeti varsayar. Bir temel kendini barındıran WCF Hizmeti bakın, oluşturmanın bir örneği için [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md). Bu konu, hizmet kodunda yapılandırılan varsayar. Bir yapılandırma dosyası kullanarak benzer bir hizmet yapılandırma bir örnek görmek istiyorsanız bkz [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Windows etki alanı kullanıcı adı ve parola kullanarak, istemcilerin kimliğini doğrulamak için bir hizmeti yapılandırmak için <xref:System.ServiceModel.WSHttpBinding> ve kendi `Security.Mode` özelliğine `Message`. Ayrıca, bir X509 belirtmelisiniz istemciden hizmete gönderildiğinde kullanıcı adı ve parola şifrelemek için kullanılan sertifika.  
  
 İstemcide, kullanıcıdan kullanıcı adı ve parola ve WCF istemci proxy kullanıcının kimlik bilgilerini belirtmeniz gerekir.  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Windows etki alanı kullanıcı adı ve parola kullanarak kimlik doğrulaması için bir WCF hizmeti yapılandırmak için
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding>, bağlamanın güvenlik modunu ayarlama `SecurityMode.Message`ayarlayın `ClientCredentialType` bağlamanın `MessageCredentialType.UserName`, aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarı için yapılandırılmış bağlamayı kullanarak hizmet uç noktası ekleyin:  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  Kullanıcı adı şifrelemek için kullanılan sunucu sertifikası ve kablo üzerinden gönderilen parola bilgilerini belirtin. Bu kod, yukarıdaki kod hemen izlemelisiniz. Aşağıdaki örnek, setup.bat dosyasından tarafından oluşturulan sertifika kullanır. [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md) örnek:  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Yalnızca sertifikanızı başvurmak için kodu değiştirin, kendi sertifika kullanın. Oluşturma ve sertifikaları kullanma hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Sertifikayı yerel makinede güvenilir kişiler sertifika deposunda olduğundan emin olun. Mmc.exe çalıştırmak ve seçmek bu yapabilirsiniz **dosya**, **Ekle/Kaldır ek bileşenini...**  menü öğesi. İçinde **Ekle veya Kaldır ek bileşenler** iletişim kutusunda **Sertifikalar ek bileşenini** tıklatıp **Ekle**. Sertifikalar ek bileşenini iletişim kutusunda seçin **bilgisayar hesabı**. Varsayılan ileti güvenliği kullanıcı adı örnekten oluşturulan sertifika Kişisel/Sertifikalar klasöründe yer alır.  Verilen sütun MMC penceresinde altında "localhost" olarak listelenir. Sürükleme ve bırakma içine sertifika **güvenilir kişiler** klasör. Bu, sertifika kimlik doğrulaması yapılırken bir güvenilen sertifika olarak işlemek WCF olanak tanır.  
  
## <a name="to-call-the-service-passing-username-and-password"></a>Kullanıcı adı ve parola geçirme hizmetini çağırmak için  
  
1.  İstemci uygulaması kullanıcı adı ve parola kullanıcıdan gerekir. Aşağıdaki kod, kullanıcı adı ve parola için kullanıcıya sorar.  
  
    > [!WARNING]
    >  Girilen sırasında parola gösterildiği bu kodu üretimde kullanılmamalıdır.  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2.  Aşağıdaki kodda gösterildiği gibi istemcinin kimlik bilgilerini belirtme istemci proxy örneği oluşturun:  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [Temel Kimlik Doğrulama ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [Dağıtılan Uygulama Güvenliği](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
