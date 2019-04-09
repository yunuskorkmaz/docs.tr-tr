---
title: 'İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: 4a69cf01519ea21f61e0c142039e4d2fe9a3c0e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191698"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma
Bu konu nasıl uygulanacağı özel istemci ve hizmet kimlik bilgilerini ve uygulama kodundan özel kimlik bilgilerini kullanmayı gösterir.  
  
## <a name="credentials-extensibility-classes"></a>Kimlik bilgileri genişletilebilirlik sınıfları  
 <xref:System.ServiceModel.Description.ClientCredentials> Ve <xref:System.ServiceModel.Description.ServiceCredentials> Windows Communication Foundation (WCF) güvenlik genişletilebilirliği için ana giriş noktaları sınıflardır. Bu kimlik bilgilerini sınıfları uygulama kodu kimlik bilgilerini ayarlamak ve güvenlik belirteçleri şeklinde kimlik bilgisi türü dönüştürmeye olanak tanıyan API'ler sağlar. (*Güvenlik belirteçleri* SOAP iletilerini içindeki kimlik bilgileri iletmek için kullanılan biçimindedir.) Bu kimlik bilgilerini sınıfların sorumlulukları iki alana ayrılabilir:  
  
-   Kimlik bilgilerini ayarlamak uygulamalar için API'ler sağlar.  
  
-   İçin bir üreteci olarak gerçekleştirmek <xref:System.IdentityModel.Selectors.SecurityTokenManager> uygulamaları.  
  
 Hem <xref:System.ServiceModel.Description.ClientCredentials> ve <xref:System.ServiceModel.Description.ServiceCredentials> devralınan soyut sınıfları <xref:System.ServiceModel.Security.SecurityCredentialsManager> döndürmek için sözleşmeyi tanımlayan sınıf <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 WCF'de sağlanan varsayılan uygulamaları, sistem tarafından sağlanan kimlik bilgisi türlerini desteklemek ve güvenlik kimlik bilgileri türlerine işleyebilir belirteci yöneticisi oluşturun.  
  
## <a name="reasons-to-customize"></a>Özelleştirme için nedenler  
 İstemci veya hizmet kimlik bilgisi sınıfları özelleştirmeye yönelik birden çok neden vardır. Özellikle sistem tarafından sağlanan kimlik bilgisi türlerinin, özellikle aşağıdaki nedenlerden dolayı işleme ilişkin varsayılan WCF güvenlik davranışı değiştirmek için gereklidir:  
  
-   Diğer genişletilebilirlik noktaları kullanarak mümkün olmayan değişiklikler.  
  
-   Yeni kimlik bilgisi türlerinin ekleniyor.  
  
-   Yeni özel güvenlik belirteci türleri ekleniyor.  
  
 Bu konu nasıl uygulanacağı özel istemci ve hizmet kimlik bilgilerini ve bunların uygulama kodunu nasıl kullanılacağını açıklar.  
  
## <a name="first-in-a-series"></a>Serideki ilk  
 Kimlik bilgileri özelleştirme nedenini kimlik bilgileri sağlama, güvenlik belirteci serileştirme veya kimlik doğrulaması ile ilgili WCF davranışı değiştirmek için özel kimlik bilgilerini sınıfı oluşturma yalnızca ilk adım, olduğundan. Bu bölümdeki diğer konulara özel seri hale getiricileri genişletme ve Doğrulayıcı nasıl oluşturulacağını açıklar. Bu bağlamda, özel kimlik bilgisi sınıfını oluşturmak, serideki ilk konu olur. Özel kimlik bilgileri yalnızca oluşturduktan sonra sonraki eylemleri (özel seri hale getiricileri genişletme ve Doğrulayıcı oluşturma) yapılabilir. Bu konu yapı ek konular şunlardır:  
  
-   [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   [Nasıl yapılır: Özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-implement-custom-client-credentials"></a>Özel istemci kimlik bilgileri uygulamak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.ServiceModel.Description.ClientCredentials> sınıfı.  
  
2.  İsteğe bağlı. Yeni yöntemleri veya yeni kimlik bilgisi türlerinin özelliklerini ekleyin. Yeni kimlik bilgisi türlerinin eklemezseniz, bu adımı atlayın. Aşağıdaki örnek ekler bir `CreditCardNumber` özelliği.  
  
3.  Geçersiz kılma <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> yöntemi. Bu yöntem WCF güvenlik altyapısı tarafından özel istemci kimlik bilgileri kullanılan otomatik olarak çağrılır. Bu yöntem, oluşturma ve uygulaması örneği döndüren sorumludur <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfı.  
  
    > [!IMPORTANT]
    >  Dikkat etmeniz önemlidir <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> yöntemi bir özel güvenlik belirteci yöneticisi oluşturmak için geçersiz kılınmıştır. Güvenlik belirteci yöneticisi, türetilen <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, türetilmiş bir özel güvenlik belirteci sağlayıcı döndürmelidir <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, gerçek güvenlik belirteci oluşturmak için. Uygulamanız güvenlik belirteçleri oluşturmak için bu düzeni uygulamazsanız yanlış çalışabilir, <xref:System.ServiceModel.ChannelFactory> nesneleri (olan WCF istemci proxy'leri için varsayılan davranış), önbelleğe alınır bir ayrıcalık yükseltme saldırısı potansiyel olarak ortaya çıkan. Özel kimlik bilgisi nesnesinin bir parçası olarak önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory>. Ancak, özel <xref:System.IdentityModel.Selectors.SecurityTokenManager> belirteci oluşturma mantığı yerleştirilir sürece, bir güvenlik tehdidi azaltır her çağırma oluşturulan <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4.  Geçersiz kılma <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> yöntemi.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a>Özel istemci güvenlik belirteci yöneticisi uygulamak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> yöntem özel ise <xref:System.IdentityModel.Selectors.SecurityTokenProvider> uygulama oluşturulmalıdır. Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: Özel güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> yöntem özel ise <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> uygulama oluşturulmalıdır. Özel güvenlik belirteci kimlik doğrulayıcılar hakkında daha fazla bilgi için bkz: [nasıl yapılır: Özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> yöntem özel ise <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> oluşturulması gerekir. Özel güvenlik belirteçleri ve özel güvenlik belirteci seri hale getiricileri genişletme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Bir özel istemci kimlik bilgileri uygulama kodundan kullanmak için  
  
1.  Hizmet arabirimi temsil eden oluşturulan istemci örneği oluşturabilir veya bir örneğini oluşturmak <xref:System.ServiceModel.ChannelFactory> ile iletişim kurmak istediğiniz hizmetine işaret eden.  
  
2.  Sistem tarafından sağlanan istemci kimlik bilgileri davranış kaldırmak <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> aracılığıyla erişilebilen koleksiyonuna <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> özelliği.  
  
3.  Bir özel istemci kimlik bilgileri sınıfının yeni bir örneğini oluşturmak ve eklemek <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> aracılığıyla erişilebilen koleksiyonuna <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> özelliği.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 Önceki yordamı, uygulama kodundan istemci kimlik bilgileri kullanma işlemini gösterir. WCF kimlik bilgileri, uygulama yapılandırma dosyası kullanarak de yapılandırılabilir. Uygulama yapılandırması kullanarak genellikle kaynak, yeniden derlemeden ve yeniden dağıtma işlemi değiştirmek zorunda kalmadan uygulama parametreleri değiştirilmesine olanak sağladığından kodlamak için tercih edilir.  
  
 Sonraki yordamda desteklemek için özel kimlik bilgileri yapılandırmasını açıklar.  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Bir yapılandırma işleyicisi özel istemci kimlik bilgileri oluşturma  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2.  İsteğe bağlı. Uygulama yapılandırması kullanıma sunmak istediğiniz tüm ek yapılandırma parametreleri için özellikler ekleyin. Aşağıdaki örnekte adlı bir özellik ekler `CreditCardNumber`.  
  
3.  Geçersiz kılma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> dönüş türü özel bir istemci özelliğini yapılandırma öğesi ile oluşturulan sınıf kimlik bilgileri.  
  
4.  Geçersiz kılma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> yöntemi. Yöntemi, oluşturma ve yapılandırma dosyasından yüklenen ayarlara dayanan özel kimlik bilgileri sınıfının bir örneğini döndüren sorumludur. Temel arama <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> sistem tarafından sağlanan kimlik bilgileri ayarlarını almak için bu yöntem yöntemi, özel istemci kimlik bilgileri örneğine yüklendi.  
  
5.  İsteğe bağlı. 2. adımda eklediğiniz ek özelliklerini geçersiz kılmak gerekirse <xref:System.Configuration.ConfigurationElement.Properties%2A> tanıması için yapılandırma çerçevesi için ek yapılandırma ayarlarını kaydetmek için özellik. Sistem tarafından sağlanan ayarların bu özel istemci kimlik bilgileri yapılandırma öğesi yapılandırılması için izin vermek için temel sınıf özelliklere sahip özelliklerinizi birleştirin.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Yapılandırma işleyici sınıf aldıktan sonra WCF yapılandırma altyapısına tümleştirilebilir. Sonraki yordamda gösterildiği gibi istemci uç nokta davranışı öğelerinde kullanılacak özel bir istemci kimlik bilgileri sağlar.  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Özel bir istemci kullanın ve kaydetmek için uygulama yapılandırmasında yapılandırma işleyicisi kimlik bilgileri  
  
1.  Ekleme bir <`extensions`> öğesi ve bir <`behaviorExtensions`> yapılandırma dosyası öğesi.  
  
2.  Ekleme bir <`add`> öğesi <`behaviorExtensions`> öğesi ve set `name` özniteliği için uygun bir değer.  
  
3.  Ayarlama `type` özniteliği için tam nitelikli tür adı. Derleme adı ve diğer derleme özniteliklerini de içerir.  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4.  Yapılandırma işleyicinizi kaydolduktan sonra özel kimlik öğesi sistem tarafından sağlanan yerine aynı yapılandırma dosyası içinde kullanılabilir <`clientCredentials`> öğesi. Hem sistem tarafından sağlanan özellikleri hem de yapılandırma işleyici uygulamanızı eklediğiniz tüm yeni özellikleri kullanabilirsiniz. Aşağıdaki örneği kullanarak bir özel özellik değerini ayarlar `creditCardNumber` özniteliği.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a>Özel hizmet kimlik bilgilerini uygulamak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2.  İsteğe bağlı. API'leri eklenmekte olan yeni kimlik bilgileri değerlerini sağlamak için yeni özellikler ekleyin. Yeni kimlik bilgileri değerlerini eklemek, bu adımı atlayın. Aşağıdaki örnek ekler bir `AdditionalCertificate` özelliği.  
  
3.  Geçersiz kılma <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> yöntemi. Bu yöntem WCF altyapısı tarafından özel istemci kimlik bilgileri kullanılan otomatik olarak çağrılır. Oluşturma ve uygulaması örneği döndüren yöntem sorumludur <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfı (bir sonraki yordamda açıklanmıştır).  
  
4.  İsteğe bağlı. Geçersiz kılma <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> yöntemi. Bu, yalnızca yeni özellikler veya iç alanları için özel istemci kimlik bilgileri uygulama ekliyorsanız gereklidir.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a>Bir özel hizmet güvenlik belirteci yöneticisi uygulamak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfı.  
  
2.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> yöntem özel ise <xref:System.IdentityModel.Selectors.SecurityTokenProvider> uygulama oluşturulmalıdır. Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: Özel güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> yöntem özel ise <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> uygulama oluşturulmalıdır. Özel güvenlik belirteci kimlik doğrulayıcılar hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) konu.  
  
4.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> yöntem özel ise <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> oluşturulması gerekir. Özel güvenlik belirteçleri ve özel güvenlik belirteci seri hale getiricileri genişletme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a>Uygulama kodu özel hizmet kimlik bilgilerini kullanmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost>.  
  
2.  Sistem tarafından sağlanan hizmet kimlik bilgilerini davranış kaldırmak <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonu.  
  
3.  Özel hizmet kimlik bilgilerini sınıfının yeni bir örneğini oluşturmak ve eklemek <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonu.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Bu yordamda daha önce açıklanan adımları kullanarak yapılandırması desteği eklendi "`To create a configuration handler for custom client credentials`"ve"`To register and use a custom client credentials configuration handler in the application configuration`." Tek fark kullanmaktır <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> sınıfı yerine <xref:System.ServiceModel.Configuration.ClientCredentialsElement> yapılandırma işleyicisi için temel sınıf olarak sınıf. Özel hizmet kimlik bilgisi öğesinin ardından olabilir yerde kullanılan sistem tarafından sağlanan `<serviceCredentials>` öğe kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Nasıl yapılır: Özel Belirteç Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
