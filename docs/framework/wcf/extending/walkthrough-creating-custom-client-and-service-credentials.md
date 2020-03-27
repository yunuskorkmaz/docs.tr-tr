---
title: 'İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: ddd9f03e26f7a8345f1070715e4877c533c361fb
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345260"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma

Bu konu, özel istemci ve hizmet kimlik bilgilerinin nasıl uygulanacağını ve uygulama kodundan özel kimlik bilgilerinin nasıl kullanılacağını gösterir.

## <a name="credentials-extensibility-classes"></a>Kimlik Bilgileri Genişletilebilirlik Sınıfları

Ve <xref:System.ServiceModel.Description.ClientCredentials> <xref:System.ServiceModel.Description.ServiceCredentials> sınıflar Windows Communication Foundation (WCF) güvenlik genişletilebilirliğinin ana giriş noktalarıdır. Bu kimlik bilgileri sınıfları, uygulama kodunun kimlik bilgilerini ayarlamasını ve kimlik bilgileri türlerini güvenlik belirteçlerine dönüştürmesini sağlayan API'leri sağlar. (*Güvenlik belirteçleri* SOAP iletileri içinde kimlik bilgilerini iletmek için kullanılan formdur.) Bu kimlik bilgileri sınıflarının sorumlulukları iki alana ayrılabilir:

- Kimlik bilgileri ayarlamak için uygulamalar için API'ler sağlayın.

- Uygulamalar için <xref:System.IdentityModel.Selectors.SecurityTokenManager> bir fabrika olarak gerçekleştirin.

WCF'de sağlanan varsayılan uygulamalar, sistem tarafından sağlanan kimlik bilgisi türlerini destekler ve bu kimlik bilgileri türlerini işleyebilen bir güvenlik belirteç yöneticisi oluşturur.

## <a name="reasons-to-customize"></a>Özelleştirme Nedenleri

İstemci veya hizmet kimlik bilgisi sınıflarını özelleştirmenin birden çok nedeni vardır. En önemlisi, özellikle aşağıdaki nedenlerle, sistem tarafından sağlanan kimlik bilgileri türlerini işleme yle ilgili varsayılan WCF güvenlik davranışını değiştirme gereksinimidir:

- Diğer genişletilebilirlik noktalarını kullanarak mümkün olmayan değişiklikler.

- Yeni kimlik bilgisi türleri ekleme.

- Yeni özel güvenlik belirteç türleri ekleme.

Bu konu, özel istemci ve hizmet kimlik bilgilerinin nasıl uygulanacağını ve uygulama kodundan nasıl kullanılacağını açıklar.

## <a name="first-in-a-series"></a>Bir Dizide İlk

Kimlik bilgilerini özelleştirmenin nedeni kimlik bilgileri sağlama, güvenlik belirteç serileştirme veya kimlik doğrulama ile ilgili WCF davranışını değiştirmek olduğundan, özel kimlik bilgileri sınıfı oluşturmak yalnızca ilk adımdır. Bu bölümdeki diğer konular, özel serializers ve kimlik doğrulayıcıları oluşturmak için nasıl açıklayabilirsiniz. Bu bağlamda, özel kimlik bilgisi sınıfı oluşturma serisinin ilk konudur. Sonraki eylemler (özel serializers ve kimlik doğrulayıcıları oluşturma) yalnızca özel kimlik bilgileri oluşturduktan sonra yapılabilir. Bu konu üzerine inşa ek konular şunlardır:

- [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](how-to-create-a-custom-security-token-provider.md)

- [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](how-to-create-a-custom-security-token-authenticator.md)

- [Nasıl?](how-to-create-a-custom-token.md)

## <a name="procedures"></a>Yordamlar

#### <a name="to-implement-custom-client-credentials"></a>Özel istemci kimlik bilgilerini uygulamak için

1. Sınıftan türetilen yeni <xref:System.ServiceModel.Description.ClientCredentials> bir sınıf tanımlayın.

2. İsteğe bağlı. Yeni kimlik bilgisi türleri için yeni yöntemler veya özellikler ekleyin. Yeni kimlik bilgisi türleri eklemezseniz, bu adımı atlayın. Aşağıdaki örnekbir `CreditCardNumber` özellik ekler.

3. <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> Yöntemi geçersiz kılın. Bu yöntem, özel istemci kimlik bilgileri kullanıldığında WCF güvenlik altyapısı tarafından otomatik olarak çağrılır. Bu yöntem, <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfın bir uygulama örneği oluşturmak ve döndürmek ten sorumludur.

    > [!IMPORTANT]
    > Özel bir güvenlik belirteç yöneticisi oluşturmak için yöntemin <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> geçersiz kılındığını unutmayın. Türetilen <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>güvenlik belirteci yöneticisi, gerçek güvenlik belirteci <xref:System.IdentityModel.Selectors.SecurityTokenProvider>oluşturmak için türetilen özel bir güvenlik belirteci sağlayıcısı döndürmelidir. Güvenlik belirteçleri oluşturmak için bu deseni izlemezseniz, <xref:System.ServiceModel.ChannelFactory> nesneler önbelleğe alındığında (WCF istemci vekilleri için varsayılan davranış) uygulamanız yanlış çalışabilir ve bu da ayrıcalık saldırısının yükseltilmesine neden olabilir. Özel kimlik bilgisi <xref:System.ServiceModel.ChannelFactory>nesnesi, 'nin bir parçası olarak önbelleğe alınmış. Ancak, belirteç oluşturma mantığı yerleştirildiği sürece güvenlik tehdidini azaltan her çağrıda özel <xref:System.IdentityModel.Selectors.SecurityTokenManager> <xref:System.IdentityModel.Selectors.SecurityTokenManager>oluşturulur.

4. <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> Yöntemi geçersiz kılın.

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>Özel istemci güvenlik belirteç yöneticisi uygulamak için

1. Türetilen yeni bir <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>sınıf tanımlayın.

2. İsteğe bağlı. Özel <xref:System.IdentityModel.Selectors.SecurityTokenProvider> bir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> uygulama oluşturulması gerekiyorsa yöntemi geçersiz kılın. Özel güvenlik belirteç sağlayıcıları hakkında daha fazla bilgi için [bkz: Özel Güvenlik Belirteç Sağlayıcısı oluşturun.](how-to-create-a-custom-security-token-provider.md)

3. İsteğe bağlı. Özel <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> bir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> uygulama oluşturulması gerekiyorsa yöntemi geçersiz kılın. Özel güvenlik belirteç kimlik doğrulayıcıları hakkında daha fazla bilgi için [bkz.](how-to-create-a-custom-security-token-authenticator.md)

4. İsteğe bağlı. Özel bir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> yöntem <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> oluşturulması gerekiyorsa yöntemi geçersiz kılın. Özel güvenlik belirteçleri ve özel güvenlik belirteçleri hakkında daha fazla bilgi için [bkz.](how-to-create-a-custom-token.md)

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Uygulama kodundan özel istemci kimlik bilgilerini kullanmak için

1. Hizmet arabirimini temsil eden oluşturulan istemcinin bir örneğini <xref:System.ServiceModel.ChannelFactory> oluşturun veya iletişim kurmak istediğiniz bir hizmete işaret etme örneğini oluşturun.

2. Sistem tarafından sağlanan istemci kimlik <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> bilgilerini koleksiyondan kaldırın ve bu davranışa özellik üzerinden erişilebilmektedir. <xref:System.ServiceModel.ChannelFactory.Endpoint%2A>

3. Özel istemci kimlik bilgileri sınıfının yeni bir <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> örneğini oluşturun ve <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> bu özelliği üzerinden erişilebilen koleksiyona ekleyin.

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

Önceki yordam, uygulama kodundan istemci kimlik bilgilerinin nasıl kullanılacağını gösterir. WCF kimlik bilgileri, uygulama yapılandırma dosyası kullanılarak da yapılandırılabilir. Kaynak, yeniden derleme ve yeniden dağıtım değiştirmeye gerek kalmadan uygulama parametrelerinin değiştirilmesine olanak sağladığından, uygulama yapılandırmasını kullanmak genellikle zor kodlamaya tercih edilir.

Sonraki yordam, özel kimlik bilgilerinin yapılandırması için destek sağlamak için nasıl açıklanır.

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Özel istemci kimlik bilgileri için yapılandırma işleyicisi oluşturma

1. Türetilen yeni bir <xref:System.ServiceModel.Configuration.ClientCredentialsElement>sınıf tanımlayın.

2. İsteğe bağlı. Uygulama yapılandırması aracılığıyla ortaya çıkarmak istediğiniz tüm ek yapılandırma parametreleri için özellikler ekleyin. Aşağıdaki örnekte . `CreditCardNumber`

3. Yapılandırma öğesi <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> ile oluşturulan özel istemci kimlik bilgileri sınıfının türünü döndürmek için özelliği geçersiz kılın.

4. <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> Yöntemi geçersiz kılın. Yöntem, yapılandırma dosyasından yüklenen ayarlara göre özel kimlik bilgisi sınıfının bir örneğini oluşturmak ve döndürmekten sorumludur. Özel istemci <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> kimlik bilgileri örneğinize yüklenen sistem tarafından sağlanan kimlik bilgilerini almak için bu yöntemden temel yöntemi arayın.

5. İsteğe bağlı. Adım 2'ye ek özellikler eklediyseniz, bunları <xref:System.Configuration.ConfigurationElement.Properties%2A> tanımak için ek yapılandırma ayarlarınızı yapılandırma çerçevesine kaydetmek için özelliği geçersiz kılmanız gerekir. Sistem tarafından sağlanan ayarların bu özel istemci kimlik bilgileri yapılandırma öğesi aracılığıyla yapılandırılabilmesi için özelliklerinizi taban sınıf özellikleriyle birleştirin.

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

Yapılandırma işleyicisi sınıfına sahip olduktan sonra, WCF yapılandırma çerçevesine entegre edilebilir. Bu, bir sonraki yordamda gösterildiği gibi, istemci uç nokta davranış öğelerinde özel istemci kimlik bilgilerinin kullanılmasını sağlar.

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Uygulama yapılandırmasında özel bir istemci kimlik bilgileri yapılandırma işleyicisini kaydetmek ve kullanmak için

1. Yapılandırma dosyasına <`extensions` bir `behaviorExtensions`> öğesi ve <bir> öğesi ekleyin.

2. <`add` `behaviorExtensions`> öğesine <> öğesi `name` ekleyin ve özniteliği uygun bir değere ayarlayın.

3. `type` Özniteliği tam nitelikli tür adına ayarlayın. Ayrıca derleme adı ve diğer derleme öznitelikleri içerir.

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    </system.serviceModel>
    ```

4. Yapılandırma işleyicinizi kaydettikten sonra, özel kimlik bilgileri öğesi sistem tarafından sağlanan <`clientCredentials`> öğesi yerine aynı yapılandırma dosyasıiçinde kullanılabilir. Hem sistem tarafından sağlanan özellikleri hem de yapılandırma işleyicisi uygulamanıza eklediğiniz yeni özellikleri kullanabilirsiniz. Aşağıdaki örnek, özniteliği kullanarak özel `creditCardNumber` bir özelliğin değerini ayarlar.

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

1. Türetilen yeni bir <xref:System.ServiceModel.Description.ServiceCredentials>sınıf tanımlayın.

2. İsteğe bağlı. Eklenen yeni kimlik bilgileri değerleri için API'ler sağlamak için yeni özellikler ekleyin. Yeni kimlik bilgisi değerleri eklemezseniz, bu adımı atlayın. Aşağıdaki örnekbir `AdditionalCertificate` özellik ekler.

3. <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> Yöntemi geçersiz kılın. Bu yöntem, özel istemci kimlik bilgileri kullanıldığında WCF altyapısı tarafından otomatik olarak çağrılır. Yöntem, <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfın bir uygulamasının örneğini oluşturmak ve döndürmekten sorumludur (sonraki yordamda açıklanmıştır).

4. İsteğe bağlı. <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> Yöntemi geçersiz kılın. Bu, yalnızca özel istemci kimlik bilgileri uygulamasına yeni özellikler veya iç alanlar eklemek için gereklidir.

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>Özel hizmet güvenliği belirteç yöneticisi uygulamak için

1. Sınıftan türetilen yeni <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> bir sınıf tanımlayın.

2. İsteğe bağlı. Özel <xref:System.IdentityModel.Selectors.SecurityTokenProvider> bir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> uygulama oluşturulması gerekiyorsa yöntemi geçersiz kılın. Özel güvenlik belirteç sağlayıcıları hakkında daha fazla bilgi için [bkz: Özel Güvenlik Belirteç Sağlayıcısı oluşturun.](how-to-create-a-custom-security-token-provider.md)

3. İsteğe bağlı. Özel <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> bir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> uygulama oluşturulması gerekiyorsa yöntemi geçersiz kılın. Özel güvenlik belirteç kimlik doğrulayıcıları hakkında daha fazla bilgi için [bkz.](how-to-create-a-custom-security-token-authenticator.md)

4. İsteğe bağlı. Özel bir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> yöntem <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> oluşturulması gerekiyorsa yöntemi geçersiz kılın. Özel güvenlik belirteçleri ve özel güvenlik belirteçleri hakkında daha fazla bilgi için [bkz.](how-to-create-a-custom-token.md)

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>Uygulama kodundan özel hizmet kimlik bilgilerini kullanmak için

1. <xref:System.ServiceModel.ServiceHost> nesnesinin bir örneğini oluşturun.

2. <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> Sistem tarafından sağlanan hizmet kimlik bilgilerini koleksiyondan kaldırın.

3. Özel hizmet kimlik bilgileri sınıfının yeni bir <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> örneğini oluşturun ve koleksiyona ekleyin.

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

" ve "`To create a configuration handler for custom client credentials``To register and use a custom client credentials configuration handler in the application configuration`yordamlarında daha önce açıklanan adımları kullanarak yapılandırma desteği ekleyin." Tek fark, yapılandırma <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> işleyicisi <xref:System.ServiceModel.Configuration.ClientCredentialsElement> için taban sınıf olarak sınıf yerine sınıf kullanmaktır. Özel hizmet kimlik bilgileri, sistem tarafından sağlanan `<serviceCredentials>` öğenin kullanıldığı her yerde kullanılabilir.

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
