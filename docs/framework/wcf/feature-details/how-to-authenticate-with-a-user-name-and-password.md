---
title: 'Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 11a146e387171d6af95a7710fe96d6f35f6c611f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321048"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama

Bu konu, Windows etki alanı adı ve parola ile bir istemci kimlik doğrulaması bir Windows Communication Foundation (WCF) hizmetini etkinleştirmek gösterilmektedir. Bu, bir çalışma, kendini barındıran WCF hizmetinde olduğunu varsayar. Bir temel şirket içinde barındırılan WCF hizmet bkz oluşturma örneği için [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md). Bu konuda, kod içinde hizmet yapılandırılmış varsayılır. Bir yapılandırma dosyası kullanarak benzer bir hizmet yapılandırma örneği görmek istiyorsanız bkz [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 İstemcileri Windows etki alanı kullanıcı adı ve parolaları kullanarak kimlik doğrulaması için bir hizmeti yapılandırmak için <xref:System.ServiceModel.WSHttpBinding> ve kendi `Security.Mode` özelliğini `Message`. Buna ek olarak, x X509 belirtmelisiniz, istemciden hizmete gönderilen kullanıcı adı ve parola şifrelemek için kullanılan sertifika.  
  
 İstemcide, kullanıcı adı ve parola girmesini ve WCF istemci proxy kullanıcının kimlik bilgilerini belirtmeniz gerekir.  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Windows etki alanı kullanıcı adı ve parola kullanarak kimlik doğrulaması için bir WCF hizmeti yapılandırmak için
  
1. Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding>, bağlamanın güvenlik modunu ayarlama <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>ayarlayın `ClientCredentialType` bağlamanın <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarı için yapılandırılmış bağlama kullanarak bir hizmet uç noktası ekleyin:  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2. Kullanıcı adı şifrelemek için kullanılan sunucu sertifikası ve kablo üzerinden gönderilen parola bilgilerini belirtin. Bu kod, yukarıdaki kod hemen izlemelidir. Aşağıdaki örnek setup.bat dosyasından oluşturulan sertifikayı kullandığını [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md) örnek:  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Sertifikanızı kullanabilir, yalnızca sertifikanıza başvurmak için kodu değiştirin. Oluşturma ve sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Sertifika, yerel makinede güvenilir kişiler sertifika deposunda olduğundan emin olun. Mmc.exe çalıştıran ve seçerek bunu yapabilirsiniz **dosya**, **Ekle/Kaldır ek bileşenini...**  menü öğesi. İçinde **ek bileşenler Ekle / Kaldır** iletişim kutusunda **Sertifikalar ek bileşenini** tıklatıp **Ekle**. Sertifikalar ek bileşenini iletişim kutusunda seçin **bilgisayar hesabı**. Varsayılan ileti güvenliği kullanıcı adı örnekten oluşturulan sertifika Kişisel/Sertifikalar klasöründe bulunur.  Verilen sütun MMC penceresinde altında "localhost" olarak listelenir. Sürükle ve bırak sertifikayı **güvenilir kişiler** klasör. Bu, sertifikayı güvenilen bir sertifika kimlik doğrulaması yapılırken değerlendirilecek WCF olanak tanır.  
  
## <a name="to-call-the-service-passing-username-and-password"></a>Kullanıcı adı ve parola geçirme hizmeti çağırmak için  
  
1. İstemci uygulaması için kullanıcı adı ve parola girmesini gerekir. Aşağıdaki kod, kullanıcı adı ve parola için kullanıcıya sorar.  
  
    > [!WARNING]
    >  Bu kod, parola girilmesini sırasında görüntülenen üretim ortamında kullanılmamalıdır.  
  
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
  
2. Aşağıdaki kodda gösterildiği gibi istemcinin kimlik bilgilerinin belirtilmesi istemci proxy örneği oluşturun:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [Temel Kimlik Doğrulama ile Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [Dağıtılan Uygulama Güvenliği](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
