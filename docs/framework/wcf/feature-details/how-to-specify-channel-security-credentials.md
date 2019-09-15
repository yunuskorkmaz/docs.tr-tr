---
title: 'Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: e5b2b56da1989b9a7110a1ad3eee814560942c89
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972439"
---
# <a name="how-to-specify-channel-security-credentials"></a>Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme
Windows Communication Foundation (WCF) hizmet bilinen adı, COM uygulamalarının WCF hizmetlerini çağırmasını sağlar. Çoğu WCF hizmeti, istemcinin kimlik doğrulama ve yetkilendirme için kimlik bilgilerini belirtmesini gerektirir. WCF istemcisinden bir WCF hizmetini çağırırken bu kimlik bilgilerini yönetilen kodda veya bir uygulama yapılandırma dosyasında belirtebilirsiniz. Bir WCF hizmetini bir com uygulamasından çağırırken, kimlik bilgilerini belirtmek için <xref:System.ServiceModel.ComIntegration.IChannelCredentials> arabirimini kullanabilirsiniz. Bu konu, <xref:System.ServiceModel.ComIntegration.IChannelCredentials> arabirimi kullanarak kimlik bilgilerini belirtmek için çeşitli yollar gösterir.  
  
> [!NOTE]
> <xref:System.ServiceModel.ComIntegration.IChannelCredentials>, IDispatch tabanlı bir arabirimdir ve Visual Studio ortamında IntelliSense işlevselliği almaz.  
  
 Bu makalede [Ileti güvenliği örneğinde](../../../../docs/framework/wcf/samples/message-security-sample.md)tanımlanan WCF hizmeti kullanılacaktır.  
  
### <a name="to-specify-a-client-certificate"></a>İstemci sertifikası belirtmek için  
  
1. Gerekli test sertifikalarını oluşturmak ve yüklemek için Ileti güvenlik dizininde Setup. bat dosyasını çalıştırın.  
  
2. Ileti güvenliği projesini açın.  
  
3. Arabirim tanımına ekleyin `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]`. `ICalculator`  
  
4. Hizmetin `bindingNamespace="http://Microsoft.ServiceModel.Samples"` App. config dosyasındaki Endpoint etiketine ekleyin.  
  
5. Ileti güvenlik örneğini oluşturun ve Service. exe ' yi çalıştırın. Internet Explorer 'ı kullanın ve hizmetin URI 'sine gidin (http://localhost:8000/ServiceModelSamples/Service) hizmetin çalıştığından emin olmak için).  
  
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
  
     Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler. <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>Ayrıca, istemci sertifikasını ayarlamak <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> için yerinde de kullanılabilir: <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29>  
  
    ```vb  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> Bu çağrının çalışması için, istemci sertifikasının, istemcinin üzerinde çalıştığı makinede güvenilir olması gerekir.  
  
> [!NOTE]
> Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür. Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.  
  
### <a name="to-specify-user-name-and-password"></a>Kullanıcı adı ve parola belirtmek için  
  
1. Kullanmak için Service App. config dosyasını değiştirin `wsHttpBinding`. Bu, Kullanıcı adı ve parola doğrulaması için gereklidir:  

2. Şunu Kullanıcı adı olarak ayarla: `clientCredentialType`  

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
    > Bu örnekteki hizmet takma adı 'nda belirtilen bağlama WSHttpBinding_ICalculator olarak değiştirilmiştir. Ayrıca, çağrısına, için <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>geçerli bir Kullanıcı adı ve parola belirtmeniz gerektiğini unutmayın.  
  
### <a name="to-specify-windows-credentials"></a>Windows kimlik bilgilerini belirtmek için  
  
1. Service `clientCredentialType` App. config dosyasında Windows olarak ayarlayın:  

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
  
1. Sorun belirteçleri yalnızca Federe güvenlik kullanan uygulamalar için kullanılır. Federasyon güvenliği hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) ve [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     Aşağıdaki Visual Basic kod örneği, <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> yönteminin nasıl çağrılacağını göstermektedir:  
  
    ```vb
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Bu yöntemin parametreleri hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)
- [Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: Federe Istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
