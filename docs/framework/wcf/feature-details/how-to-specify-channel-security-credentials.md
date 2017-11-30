---
title: "Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 2a1b2ba0ab49ebf470c0245f0827f82e1fe20ce8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-channel-security-credentials"></a>Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmet bilinen adı verir çağırmak COM uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri. Çoğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri istemci kimlik doğrulaması ve yetkilendirme kimlik bilgilerini belirtmenizi gerektirir. Çağrılırken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelen hizmet bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bu kimlik bilgileri yönetilen kod veya uygulama yapılandırma dosyası belirtebilirsiniz. Çağrılırken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti bir COM uygulamasından kullandığınız <xref:System.ServiceModel.ComIntegration.IChannelCredentials> kimlik bilgilerini belirtmek için arabirim. Bu konuda kullanarak kimlik bilgilerini belirtmek için çeşitli şekillerde gösterecektir <xref:System.ServiceModel.ComIntegration.IChannelCredentials> arabirimi.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials>IDispatch tabanlı bir arabirim ve Visual Studio ortamında IntelliSense işlevselliği almazsınız.  
  
 Bu makalede kullanacağı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tanımlanan hizmet [ileti güvenliği örneği](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>Bir istemci sertifikasını belirtmek için  
  
1.  Setup.bat dosya oluşturmak ve gerekli test sertifikaları yüklemek için ileti güvenliği dizininde çalıştırın.  
  
2.  İleti güvenliği projesini açın.  
  
3.  Ekleme `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` için `ICalculator` arabirim tanımı.  
  
4.  Ekleme `bindingNamespace=``http://Microsoft.ServiceModel.Samples` App.config hizmeti için uç nokta etiketinde için.  
  
5.  İleti güvenliği örneği oluşturun ve Service.exe çalıştırın. Internet Explorer'ı kullanın ve hizmetin çalıştığından emin olmak için hizmetin URI (8000/ServiceModelSamples/hizmet) göz atın.  
  
6.  Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun. Aşağıdaki kod tıklatın işleyicisine eklemek için düğmesini çift tıklayın ve forma düğme ekleme:  
  
    ```  
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
  
7.  Visual Basic uygulamasını çalıştırın ve sonuçları doğrulayın.  
  
     Visual Basic uygulama Ekle (3, 4) çağırma gelen sonuç içeren bir ileti kutusu görüntüler. <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>veya <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> de yerine kullanılabilir <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> istemci sertifikasını ayarlamak için:  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  Bu çağrı çalışması istemci sertifikası istemci çalıştıran makinede güvenilir olması gerekir.  
  
> [!NOTE]
>  Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi." bildiren bir hata döndürür Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.  
  
### <a name="to-specify-user-name-and-password"></a>Kullanıcı adı ve parola belirtmek için  
  
1.  Kullanılacak hizmet App.config dosyasını değiştirmek `wsHttpBinding`. Bu, kullanıcı adı ve parola doğrulamasını gereklidir:  
  
  
  
2.  Ayarlama `clientCredentialType` kullanıcı adı için:  
  
  
  
3.  Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun. Aşağıdaki kod tıklatın işleyicisine eklemek için düğmesini çift tıklayın ve forma düğme ekleme:  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4.  Visual Basic uygulamasını çalıştırın ve sonuçları doğrulayın. Visual Basic uygulama Ekle (3, 4) çağırma gelen sonuç içeren bir ileti kutusu görüntüler.  
  
    > [!NOTE]
    >  Bu örnekte hizmet bilinen adı belirtilen bağlama için WSHttpBinding_ICalculator değiştirildi. Geçerli bir kullanıcı adı ve parola çağrısında sağlamanız gerektiğini de unutmayın <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.  
  
### <a name="to-specify-windows-credentials"></a>Windows kimlik bilgilerini belirtmek için  
  
1.  Ayarlama `clientCredentialType` Windows hizmeti App.config dosyasında:  
  
  
  
2.  Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun. Aşağıdaki kod tıklatın işleyicisine eklemek için düğmesini çift tıklayın ve forma düğme ekleme:  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3.  Visual Basic uygulamasını çalıştırın ve sonuçları doğrulayın. Visual Basic uygulama Ekle (3, 4) çağırma gelen sonuç içeren bir ileti kutusu görüntüler.  
  
    > [!NOTE]
    >  "Etki alanı", "userID" ve "parola" geçerli değerlerle değiştirmelisiniz.  
  
### <a name="to-specify-an-issue-token"></a>Bir sorun belirteci belirtmek için  
  
1.  Sorunu belirteçleri federe güvenlik kullanan uygulamalar için kullanılır. Federasyon güvenliği hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) ve [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     Aşağıdaki Visual Basic kod örneği nasıl çağrılacağını gösterir <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> yöntemi:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Bu yöntem için parametreler hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Nasıl yapılır: federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [İleti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Bağlamalar ve güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
