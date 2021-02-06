---
description: 'Daha fazla bilgi edinin: Izlenecek yol: özel Istemci ve hizmet kimlik bilgileri oluşturma'
title: 'İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: 75313defafaf0d0d558c100f1e86df9e2415d993
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643962"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma

Bu konu, özel istemci ve hizmet kimlik bilgilerinin nasıl uygulanacağını ve uygulama kodundan özel kimlik bilgilerinin nasıl kullanılacağını gösterir.

## <a name="credentials-extensibility-classes"></a>Kimlik bilgileri genişletilebilirlik sınıfları

<xref:System.ServiceModel.Description.ClientCredentials>Ve <xref:System.ServiceModel.Description.ServiceCredentials> sınıfları, WINDOWS COMMUNICATION FOUNDATION (WCF) güvenlik genişletilebilirliği için ana giriş noktalarıdır. Bu kimlik bilgileri sınıfları, uygulama kodunun kimlik bilgileri ayarlaması ve kimlik bilgisi türlerini güvenlik belirteçlerine dönüştürmesine imkan tanıyan API 'Leri sağlar. (*Güvenlik belirteçleri* , kimlik BILGISI bilgilerini SOAP iletileri içinde aktarmak için kullanılan formdur.) Bu kimlik bilgileri sınıflarının sorumlulukları iki alana ayrılabilir:

- Kimlik bilgileri ayarlamak için uygulamalara yönelik API 'Leri belirtin.

- Uygulamalar için fabrika olarak gerçekleştirin <xref:System.IdentityModel.Selectors.SecurityTokenManager> .

WCF 'de belirtilen varsayılan uygulamalar sistem tarafından belirtilen kimlik bilgisi türlerini destekler ve bu kimlik bilgileri türlerini işleyebilen bir güvenlik belirteci Yöneticisi oluşturur.

## <a name="reasons-to-customize"></a>Özelleştirme nedenleri

İstemci veya hizmet kimlik bilgisi sınıflarını özelleştirmek için birden çok neden vardır. Foremost, varsayılan WCF güvenlik davranışını sistem tarafından belirtilen kimlik bilgisi türlerini işlemeye ilişkin olarak değiştirme gereksinimidir, özellikle aşağıdaki nedenlerden dolayı:

- Diğer genişletilebilirlik noktaları kullanılarak mümkün olmayan değişiklikler.

- Yeni kimlik bilgisi türleri ekleniyor.

- Yeni özel güvenlik belirteci türleri ekleniyor.

Bu konu, özel istemci ve hizmet kimlik bilgilerinin nasıl uygulanacağını ve uygulama kodundan nasıl kullanılacağını açıklamaktadır.

## <a name="first-in-a-series"></a>Bir seride ilk olarak

Özel kimlik bilgileri sınıfının oluşturulması, kimlik bilgilerini özelleştirme nedeni kimlik bilgileri sağlama, güvenlik belirteci serileştirme veya kimlik doğrulama ile ilgili WCF davranışını değiştirmek olduğu için yalnızca ilk adımdır. Bu bölümdeki diğer konular, özel serileştiriciler ve kimlik doğrulayıcılar oluşturmayı açıklamaktadır. Bu konuda, serinin ilk konusu olan özel kimlik bilgisi sınıfı oluşturma işlemi. Sonraki eylemler (özel serileştiriciler ve kimlik doğrulayıcılar oluşturma), yalnızca özel kimlik bilgileri oluşturulduktan sonra yapılabilir. Bu konu başlığı altında yer alan ek Konular şunları içerir:

- [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](how-to-create-a-custom-security-token-provider.md)

- [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](how-to-create-a-custom-security-token-authenticator.md)

- [Nasıl yapılır: özel belirteç oluşturma](how-to-create-a-custom-token.md).

## <a name="procedures"></a>Yordamlar

#### <a name="to-implement-custom-client-credentials"></a>Özel istemci kimlik bilgilerini uygulamak için

1. Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.ServiceModel.Description.ClientCredentials> .

2. İsteğe bağlı. Yeni kimlik bilgisi türleri için yeni yöntemler veya özellikler ekleyin. Yeni kimlik bilgisi türleri eklemedıysanız, bu adımı atlayın. Aşağıdaki örnek bir özellik ekler `CreditCardNumber` .

3. Yöntemini geçersiz kılın <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> . Bu yöntem, özel istemci kimlik bilgileri kullanıldığında WCF güvenlik altyapısı tarafından otomatik olarak çağırılır. Bu yöntem, sınıfının bir uygulamasının bir örneğini oluşturup döndürmekten sorumludur <xref:System.IdentityModel.Selectors.SecurityTokenManager> .

    > [!IMPORTANT]
    > <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A>Özel bir güvenlik belirteci Yöneticisi oluşturmak için yönteminin geçersiz kılındığına dikkat edin. ' Dan türetilen güvenlik belirteci Yöneticisi, <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> <xref:System.IdentityModel.Selectors.SecurityTokenProvider> gerçek güvenlik belirtecini oluşturmak için öğesinden türetilmiş özel bir güvenlik belirteci sağlayıcısı döndürmelidir. Güvenlik belirteçleri oluşturmak için bu kalıbı izlemeseniz, <xref:System.ServiceModel.ChannelFactory> nesneler önbelleğe alındığında (WCF istemci proxy 'leri için varsayılan davranış), büyük olasılıkla ayrıcalık yükselmesine neden olabilecek uygulamanız yanlış çalışabilir. Özel kimlik bilgisi nesnesi öğesinin bir parçası olarak önbelleğe alınır <xref:System.ServiceModel.ChannelFactory> . Ancak, özel, <xref:System.IdentityModel.Selectors.SecurityTokenManager> belirteç oluşturma mantığı içinde yerleştirildiği sürece güvenlik tehditlerinin etkisini azaltır ve her çağrılışında oluşturulur <xref:System.IdentityModel.Selectors.SecurityTokenManager> .

4. Yöntemini geçersiz kılın <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> .

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>Özel bir istemci güvenlik belirteci Yöneticisi uygulamak için

1. Öğesinden türetilmiş yeni bir sınıf tanımlayın <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> .

2. İsteğe bağlı. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29>Özel bir uygulama oluşturulması gerekiyorsa, yöntemi geçersiz kılın <xref:System.IdentityModel.Selectors.SecurityTokenProvider> . Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel güvenlik belirteci sağlayıcısı oluşturma](how-to-create-a-custom-security-token-provider.md).

3. İsteğe bağlı. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29>Özel bir uygulama oluşturulması gerekiyorsa, yöntemi geçersiz kılın <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> . Özel güvenlik belirteci kimlik doğrulayıcılar hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcısı oluşturma](how-to-create-a-custom-security-token-authenticator.md).

4. İsteğe bağlı. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A>Özel bir oluşturulması gerekiyorsa yöntemi geçersiz kılın <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> . Özel güvenlik belirteçleri ve özel güvenlik belirteci serileştiricileri hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel belirteç oluşturma](how-to-create-a-custom-token.md).

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Uygulama kodundan özel istemci kimlik bilgilerini kullanmak için

1. Hizmet arabirimini temsil eden oluşturulan istemcinin bir örneğini oluşturun ya da <xref:System.ServiceModel.ChannelFactory> iletişim kurmak istediğiniz bir hizmete işaret eden bir örnek oluşturun.

2. Sistem tarafından sağlanmış istemci kimlik bilgileri davranışını, <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliği aracılığıyla erişilebilen koleksiyondan kaldırın <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> .

3. Özel istemci kimlik bilgileri sınıfının yeni bir örneğini oluşturun ve bunu, <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliği aracılığıyla erişilebilen koleksiyona ekleyin <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> .

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

Önceki yordamda, uygulama kodundan istemci kimlik bilgilerinin nasıl kullanılacağı gösterilmektedir. WCF kimlik bilgileri, uygulama yapılandırma dosyası kullanılarak da yapılandırılabilir. Uygulama yapılandırmasının kullanılması, kaynak, yeniden derleme ve yeniden dağıtmayı değiştirmeden uygulama parametrelerinin değiştirilmesini sağladığından, genellikle sabit kodlamaya göre tercih edilir.

Sonraki yordamda özel kimlik bilgileri yapılandırması desteğinin nasıl sağlanacağı açıklanmaktadır.

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Özel istemci kimlik bilgileri için yapılandırma işleyicisi oluşturma

1. Öğesinden türetilmiş yeni bir sınıf tanımlayın <xref:System.ServiceModel.Configuration.ClientCredentialsElement> .

2. İsteğe bağlı. Uygulama yapılandırması aracılığıyla göstermek istediğiniz tüm ek yapılandırma parametreleri için özellikler ekleyin. Aşağıdaki örnek adlı bir özellik ekler `CreditCardNumber` .

3. <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A>Yapılandırma öğesiyle oluşturulan özel istemci kimlik bilgileri sınıfının türünü döndürmek için özelliği geçersiz kılın.

4. Yöntemini geçersiz kılın <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> . Yöntemi, yapılandırma dosyasından yüklenen ayarlara bağlı olarak özel kimlik bilgisi sınıfının bir örneğini oluşturup döndürmekten sorumludur. <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29>Özel istemci kimlik bilgileri örneğinize yüklenen sistem tarafından belirtilen kimlik bilgileri ayarlarını almak için bu yöntemden temel yöntemi çağırın.

5. İsteğe bağlı. 2. adımda ek özellikler eklediyseniz, <xref:System.Configuration.ConfigurationElement.Properties%2A> yapılandırma çerçevesini tanımak üzere ek yapılandırma ayarlarınızı kaydetmek için özelliği geçersiz kılmanız gerekir. Bu özel istemci kimlik bilgileri yapılandırma öğesi aracılığıyla sistem tarafından sağlanmış ayarların yapılandırılmasına izin vermek için özelliklerinizi temel sınıf özellikleriyle birleştirin.

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

Yapılandırma işleyicisi sınıfına sahip olduktan sonra, WCF yapılandırma çerçevesiyle tümleştirilebilir. Bu, bir sonraki yordamda gösterildiği gibi, istemci uç noktası davranış öğelerinde özel istemci kimlik bilgilerinin kullanılmasını sağlar.

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Uygulama yapılandırmasında özel istemci kimlik bilgileri yapılandırma işleyicisini kaydetmek ve kullanmak için

1. `extensions`Yapılandırma dosyasına bir <> öğesi ve bir <`behaviorExtensions`> öğesi ekleyin.

2. `add`<> öğesine bir <> öğesi ekleyin `behaviorExtensions` ve `name` özniteliği uygun bir değere ayarlayın.

3. `type`Özniteliği tam nitelikli tür adı olarak ayarlayın. Ayrıca, derleme adı ve diğer derleme özniteliklerini de içerir.

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    </system.serviceModel>
    ```

4. Yapılandırma işleyicinizi kaydettikten sonra, özel kimlik bilgileri öğesi sistem tarafından sağlanmış <> öğesi yerine aynı yapılandırma dosyası içinde kullanılabilir `clientCredentials` . Hem sistem tarafından belirtilen özellikleri hem de yapılandırma işleyicisi uygulamanıza eklediğiniz tüm yeni özellikleri kullanabilirsiniz. Aşağıdaki örnek, özniteliğini kullanarak özel bir özelliğin değerini ayarlar `creditCardNumber` .

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

1. Öğesinden türetilmiş yeni bir sınıf tanımlayın <xref:System.ServiceModel.Description.ServiceCredentials> .

2. İsteğe bağlı. Eklenmekte olan yeni kimlik bilgisi değerleri için API sağlamak üzere yeni özellikler ekleyin. Yeni kimlik bilgisi değerleri eklemedıysanız, bu adımı atlayın. Aşağıdaki örnek bir özellik ekler `AdditionalCertificate` .

3. Yöntemini geçersiz kılın <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> . Bu yöntem, özel istemci kimlik bilgileri kullanıldığında WCF altyapısı tarafından otomatik olarak çağrılır. Yöntemi, sınıfının bir uygulamasının <xref:System.IdentityModel.Selectors.SecurityTokenManager> (bir sonraki yordamda açıklanmıştır) bir örneğinin oluşturulması ve döndürülmesinden sorumludur.

4. İsteğe bağlı. Yöntemini geçersiz kılın <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> . Bu yalnızca özel istemci kimlik bilgileri uygulamasına yeni özellikler veya iç alanlar eklendiğinde gereklidir.

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>Özel bir hizmet güvenlik belirteci Yöneticisi uygulamak için

1. Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> .

2. İsteğe bağlı. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A>Özel bir uygulama oluşturulması gerekiyorsa, yöntemi geçersiz kılın <xref:System.IdentityModel.Selectors.SecurityTokenProvider> . Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel güvenlik belirteci sağlayıcısı oluşturma](how-to-create-a-custom-security-token-provider.md).

3. İsteğe bağlı. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A>Özel bir uygulama oluşturulması gerekiyorsa, yöntemi geçersiz kılın <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> . Özel güvenlik belirteci kimlik doğrulayıcılar hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcısı oluşturma](how-to-create-a-custom-security-token-authenticator.md) konusu.

4. İsteğe bağlı. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29>Özel bir oluşturulması gerekiyorsa yöntemi geçersiz kılın <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> . Özel güvenlik belirteçleri ve özel güvenlik belirteci serileştiricileri hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel belirteç oluşturma](how-to-create-a-custom-token.md).

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>Uygulama kodundan özel hizmet kimlik bilgilerini kullanmak için

1. <xref:System.ServiceModel.ServiceHost> nesnesinin bir örneğini oluşturun.

2. Sistem tarafından belirtilen hizmet kimlik bilgileri davranışını <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyondan kaldırın.

3. Özel hizmet kimlik bilgileri sınıfının yeni bir örneğini oluşturun ve <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyona ekleyin.

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

Daha önce "" ve "yordamlarında açıklanan adımları kullanarak yapılandırma desteği ekleyin `To create a configuration handler for custom client credentials` `To register and use a custom client credentials configuration handler in the application configuration` . Tek fark, sınıfının <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> <xref:System.ServiceModel.Configuration.ClientCredentialsElement> yapılandırma işleyicisi için temel sınıf olarak yerine sınıfını kullanmaktır. Özel hizmet kimlik bilgisi öğesi, sistem tarafından belirtilen öğenin kullanıldığı her yerde kullanılabilir `<serviceCredentials>` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](how-to-create-a-custom-security-token-provider.md)
- [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](how-to-create-a-custom-security-token-authenticator.md)
- [Nasıl yapılır: Özel Belirteç Oluşturma](how-to-create-a-custom-token.md)
