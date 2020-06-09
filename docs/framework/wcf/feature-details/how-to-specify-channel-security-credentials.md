---
title: 'Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 45a13460ce94cbacae0465fede4b455a2833ce81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596948"
---
# <a name="how-to-specify-channel-security-credentials"></a>Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme
Windows Communication Foundation (WCF) hizmet bilinen adı, COM uygulamalarının WCF hizmetlerini çağırmasını sağlar. Çoğu WCF hizmeti, istemcinin kimlik doğrulama ve yetkilendirme için kimlik bilgilerini belirtmesini gerektirir. WCF istemcisinden bir WCF hizmetini çağırırken bu kimlik bilgilerini yönetilen kodda veya bir uygulama yapılandırma dosyasında belirtebilirsiniz. Bir WCF hizmetini bir COM uygulamasından çağırırken, <xref:System.ServiceModel.ComIntegration.IChannelCredentials> kimlik bilgilerini belirtmek için arabirimini kullanabilirsiniz. Bu konu, arabirimi kullanarak kimlik bilgilerini belirtmek için çeşitli yollar gösterir <xref:System.ServiceModel.ComIntegration.IChannelCredentials> .  
  
> [!NOTE]
> <xref:System.ServiceModel.ComIntegration.IChannelCredentials>, IDispatch tabanlı bir arabirimdir ve Visual Studio ortamında IntelliSense işlevselliği almaz.  
  
 Bu makalede [Ileti güvenliği örneğinde](../samples/message-security-sample.md)tanımlanan WCF hizmeti kullanılacaktır.  
  
### <a name="to-specify-a-client-certificate"></a>İstemci sertifikası belirtmek için  
  
1. Gerekli test sertifikalarını oluşturmak ve yüklemek için Ileti güvenlik dizininde Setup. bat dosyasını çalıştırın.  
  
2. Ileti güvenliği projesini açın.  
  
3. `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` `ICalculator` Arabirim tanımına ekleyin.  
  
4. `bindingNamespace="http://Microsoft.ServiceModel.Samples"`Hizmetin App. config dosyasındaki Endpoint etiketine ekleyin.  
  
5. Ileti güvenlik örneğini oluşturun ve Service. exe ' yi çalıştırın. Hizmetin çalıştığından emin olmak için Internet Explorer 'ı kullanın ve hizmetin URI 'sine ( `http://localhost:8000/ServiceModelSamples/Service` ) gidin.  
  
6. Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun. Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:  
  
    ```vb  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7. Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın.  
  
     Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler. <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29>Ayrıca, <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> istemci sertifikasını ayarlamak için yerinde de kullanılabilir:  
  
    ```vb  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> Bu çağrının çalışması için, istemci sertifikasının, istemcinin üzerinde çalıştığı makinede güvenilir olması gerekir.  
  
> [!NOTE]
> Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
### <a name="to-specify-user-name-and-password"></a>Kullanıcı adı ve parola belirtmek için  
  
1. Kullanmak için Service App. config dosyasını değiştirin `wsHttpBinding` . Bu, Kullanıcı adı ve parola doğrulaması için gereklidir:  

2. Şunu `clientCredentialType` Kullanıcı adı olarak ayarla:  

3. Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun. Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4. Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın. Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler.  
  
    > [!NOTE]
    > Bu örnekteki hizmet takma adı 'nda belirtilen bağlama WSHttpBinding_ICalculator olarak değiştirildi. Ayrıca, çağrısına, için geçerli bir Kullanıcı adı ve parola belirtmeniz gerektiğini unutmayın <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> .  
  
### <a name="to-specify-windows-credentials"></a>Windows kimlik bilgilerini belirtmek için  
  
1. `clientCredentialType`Service App. config dosyasında Windows olarak ayarlayın:  

2. Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun. Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3. Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın. Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler.  
  
    > [!NOTE]
    > "Domain", "UserID" ve "Password" değerlerini geçerli değerlerle değiştirmelisiniz.  
  
### <a name="to-specify-an-issue-token"></a>Bir sorun belirteci belirtmek için  
  
1. Sorun belirteçleri yalnızca Federe güvenlik kullanan uygulamalar için kullanılır. Federasyon güvenliği hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](federation-and-issued-tokens.md) ve [Federasyon örneği](../samples/federation-sample.md).  
  
     Aşağıdaki Visual Basic kod örneği, yönteminin nasıl çağrılacağını göstermektedir <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> :  
  
    ```vb
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Bu yöntemin parametreleri hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](federation.md)
- [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Federe İstemci Oluşturma](how-to-create-a-federated-client.md)
- [İleti Güvenliği](message-security-in-wcf.md)
- [Bağlamalar ve Güvenlik](bindings-and-security.md)
