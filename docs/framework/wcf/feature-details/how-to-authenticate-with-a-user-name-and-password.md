---
title: 'Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: e1db413dfdcfa18403e1b67361cea710b203fe5d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045949"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama

Bu konu başlığı altında, bir Windows etki alanı Kullanıcı adı ve parolasıyla bir istemcinin kimliğini doğrulamak için bir Windows Communication Foundation (WCF) hizmetinin nasıl etkinleştirileceği gösterilmektedir. Çalışan, kendine barındırılan bir WCF hizmetiniz olduğunu varsayar. Temel bir şirket içinde barındırılan WCF hizmeti oluşturma hakkında bir örnek için bkz. [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md). Bu konuda, hizmetin kodda yapılandırıldığı varsayılır. Yapılandırma dosyası kullanarak benzer bir hizmetin yapılandırılmasına ilişkin bir örnek görmek isterseniz bkz. [Ileti güvenliği Kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md)

Windows etki alanı Kullanıcı adı ve parolaları kullanarak istemcilerinin kimliğini doğrulamak üzere bir hizmeti yapılandırmak için <xref:System.ServiceModel.WSHttpBinding> öğesini kullanın ve `Security.Mode` özelliğini olarak `Message`ayarlayın. Ayrıca, istemciden hizmete gönderilirken Kullanıcı adı ve parola şifrelemek için kullanılacak bir x509 sertifikası belirtmeniz gerekir.

İstemcide, kullanıcıdan Kullanıcı adı ve parola istemek ve WCF istemci proxy 'sinde kullanıcının kimlik bilgilerini belirtmeniz gerekir.

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Windows etki alanı Kullanıcı adı ve parolasını kullanarak kimlik doğrulaması yapacak bir WCF hizmetini yapılandırmak için

1. Öğesinin <xref:System.ServiceModel.WSHttpBinding>bir örneğini oluşturun, bağlamanın güvenlik modunu olarak <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>ayarlayın, bağlama <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>' `ClientCredentialType` nın ' i ayarlayın ve aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarına yapılandırılmış bağlamayı kullanarak bir hizmet uç noktası ekleyin:

    ```csharp
    // ...
    WSHttpBinding userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. Kablo üzerinden gönderilen Kullanıcı adı ve parola bilgilerini şifrelemek için kullanılan sunucu sertifikasını belirtin. Bu kod, yukarıdaki kodu hemen izlemelidir. Aşağıdaki örnek, [Ileti güvenliği Kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md) örneğindeki Setup. bat dosyası tarafından oluşturulan sertifikayı kullanır:

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    Kendi sertifikanızı kullanabilirsiniz, kodunuzu yalnızca sertifikanıza başvuracak şekilde değiştirirsiniz. Sertifika oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Sertifikanın, yerel makine için güvenilir kişiler sertifika deposunda olduğundan emin olun. Bunu, MMC. exe ' yi çalıştırarak ve **Dosya**, **ek bileşen Ekle/Kaldır...** menü öğesini seçerek yapabilirsiniz. **Ek bileşenleri Ekle veya Kaldır** Iletişim kutusunda **Sertifikalar ek bileşenini** seçin ve **Ekle**' ye tıklayın. Sertifikalar ek bileşeni iletişim kutusunda **bilgisayar hesabı**' nı seçin. Varsayılan olarak, Ileti güvenliği Kullanıcı adı örneğinden oluşturulan sertifika Kişisel/Sertifikalar klasöründe yer alır.  Bu işlem, MMC penceresindeki verilen sütununda "localhost" olarak listelenecektir. Sertifikayı sürükleyip **güvenilir kişiler** klasörüne bırakın. Bu, WCF 'nin kimlik doğrulama gerçekleştirirken sertifikayı güvenilir bir sertifika olarak ele almasını sağlar.

## <a name="to-call-the-service-passing-username-and-password"></a>Kullanıcı adını ve parolayı geçen hizmeti çağırmak için

1. İstemci uygulama kullanıcıdan Kullanıcı adı ve parola istemelidir. Aşağıdaki kod kullanıcıdan Kullanıcı adı ve parola ister.

    > [!WARNING]
    > Parola girildiğinde görüntülenirken bu kod üretimde kullanılmamalıdır.

    ```csharp
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

2. Aşağıdaki kodda gösterildiği gibi istemcinin kimlik bilgilerini belirten istemci proxy 'sinin bir örneğini oluşturun:

    ```csharp
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
