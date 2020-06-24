---
title: 'Nasıl yapılır: Özel Belirteç Oluşturma'
description: SecurityToken kullanarak WCF 'de özel bir güvenlik belirteci oluşturmayı ve bunu bir güvenlik belirteci sağlayıcısıyla ve bir doğrulayıcı ile tümleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
ms.openlocfilehash: a95d663c2669186fcb3eb1fb2f0c426ade945f1c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247539"
---
# <a name="how-to-create-a-custom-token"></a>Nasıl yapılır: Özel Belirteç Oluşturma
Bu konuda, sınıfını kullanarak özel bir güvenlik belirtecinin nasıl oluşturulacağı <xref:System.IdentityModel.Tokens.SecurityToken> ve özel bir güvenlik belirteci sağlayıcısı ve Authenticator ile nasıl tümleştirileceği gösterilmektedir. Tüm kod örneği için bkz. [özel belirteç](../samples/custom-token.md) örneği.  
  
 Bir *güvenlik belirteci* temelde, soap iletisindeki bir gönderici hakkındaki talepleri temsil etmek için WINDOWS COMMUNICATION FOUNDATION (WCF) güvenlik çerçevesi tarafından kullanılan bir XML öğesidir. WCF güvenliği, sistem tarafından sağlanan kimlik doğrulama modları için çeşitli belirteçler sağlar. Örnek olarak sınıf tarafından temsil edilen bir X. 509.440 sertifika güvenlik belirteci <xref:System.IdentityModel.Tokens.X509SecurityToken> veya sınıf tarafından temsil edilen bir Kullanıcı adı güvenlik belirteci bulunur <xref:System.IdentityModel.Tokens.UserNameSecurityToken> .  
  
 Bazen bir kimlik doğrulama modu veya kimlik bilgisi, belirtilen türler tarafından desteklenmez. Bu durumda, SOAP iletisi içinde özel kimlik bilgisinin XML gösterimini sağlamak için özel bir güvenlik belirteci oluşturulması gerekir.  
  
 Aşağıdaki yordamlarda, özel bir güvenlik belirtecinin nasıl oluşturulduğu ve WCF güvenlik altyapısıyla nasıl tümleştirileceği gösterilmektedir. Bu konu, istemcinin kredi kartı hakkındaki bilgileri sunucusuna iletmek için kullanılan bir kredi kartı belirteci oluşturur.  
  
 Özel kimlik bilgileri ve güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için bkz. [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md).  
  
 <xref:System.IdentityModel.Tokens>Güvenlik belirteçlerini temsil eden daha fazla sınıf için bkz. ad alanı.  
  
## <a name="procedures"></a>Yordamlar  
 Güvenlik altyapısına ilişkin kredi kartı bilgilerini belirtmek için bir yol ile birlikte bir istemci uygulaması sağlanmalıdır. Bu bilgiler, özel bir istemci kimlik bilgileri sınıfı tarafından uygulamaya sunulur. İlk adım, özel istemci kimlik bilgileri için kredi kartı bilgilerini temsil eden bir sınıf oluşturmaktır.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>İstemci kimlik bilgileri içindeki kredi kartı bilgilerini temsil eden bir sınıf oluşturmak için  
  
1. Uygulama için kredi kartı bilgilerini temsil eden yeni bir sınıf tanımlayın. Aşağıdaki örnek, sınıfını adlandırır `CreditCardInfo` .  
  
2. Bir uygulamanın özel belirteç için gerekli bilgileri ayarlamaya izin vermek için sınıfa uygun özellikleri ekleyin. Bu örnekte, sınıfının üç özelliği vardır: `CardNumber` , `CardIssuer` ve `ExpirationDate` .  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Ardından, özel güvenlik belirtecini temsil eden bir sınıfın oluşturulması gerekir. Bu sınıf, WCF güvenlik altyapısına ve bu sınıftan güvenlik belirteci hakkında bilgi geçirmek için güvenlik belirteci sağlayıcısı, Authenticator ve seri hale getirici sınıfları tarafından kullanılır.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Özel bir güvenlik belirteci sınıfı oluşturmak için  
  
1. Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.IdentityModel.Tokens.SecurityToken> . Bu örnek adlı bir sınıf oluşturur `CreditCardToken` .  
  
2. Özelliği geçersiz kılın <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> . Bu özellik SOAP iletisi içindeki diğer öğelerden güvenlik belirteci XML gösterimini işaret etmek için kullanılan güvenlik belirtecinin yerel tanımlayıcısını almak için kullanılır. Bu örnekte, bir belirteç tanımlayıcısı kendisine bir oluşturucu parametresi olarak geçirilebilir veya bir güvenlik belirteci örneği her oluşturulduğunda yeni bir rastgele bir oluşturulur.  
  
3. Özelliğini uygulayın <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> . Bu özellik, güvenlik belirteci örneğinin temsil ettiği güvenlik anahtarlarının bir koleksiyonunu döndürür. Bu anahtarlar, WCF tarafından SOAP iletisinin parçalarını imzalamak veya şifrelemek için kullanılabilir. Bu örnekte, kredi kartı güvenlik belirteci herhangi bir güvenlik anahtarı içeremez; Bu nedenle, uygulama her zaman boş bir koleksiyon döndürür.  
  
4. <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A>Ve özelliklerini geçersiz kılın <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> . Bu özellikler, güvenlik belirteci örneğinin geçerliliğini belirlemede WCF tarafından kullanılır. Bu örnekte, kredi kartı güvenlik belirtecinin yalnızca bir sona erme tarihi vardır. bu nedenle `ValidFrom` özellik, <xref:System.DateTime> örnek oluşturmanın tarih ve saatini temsil eden bir döndürür.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Yeni bir güvenlik belirteci türü oluşturulduğunda, sınıfının bir uygulamasını gerektirir <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> . Uygulama, güvenlik bağlama öğesi yapılandırmasında yeni belirteç türünü temsil etmek için kullanılır. Güvenlik belirteci parametreleri sınıfı, bir iletinin işlendiği zaman gerçek güvenlik belirteci örneğiyle eşleştirmek için kullanılan bir şablon görevi görür. Şablon, bir uygulamanın güvenlik belirtecinin kullanılması veya kimliği doğrulanmış olarak eşleşmesi gereken ölçütleri belirtmek için kullanabileceği ek özellikler sağlar. Aşağıdaki örnek ek özellikler eklemez, bu nedenle, WCF altyapısı kullanılacak bir güvenlik belirteci örneğini aradığında veya doğrulamak için yalnızca güvenlik belirteci türü eşleştirilir.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Özel bir güvenlik belirteci parametreleri sınıfı oluşturmak için  
  
1. Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> .  
  
2. Yöntemini uygulayın <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> . Varsa, sınıfınıza tanımlanmış tüm iç alanları kopyalayın. Bu örnek hiçbir ek alan tanımlamaz.  
  
3. <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A>Salt okunurdur özelliğini uygulayın. Bu özellik, `true` Bu sınıf tarafından temsil edilen güvenlik belirteci türü bir hizmette istemcinin kimliğini doğrulamak için kullanılabilir ise ' i döndürür. Bu örnekte, kredi kartı güvenlik belirteci bir hizmette istemcinin kimliğini doğrulamak için kullanılabilir.  
  
4. <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A>Salt okunurdur özelliğini uygulayın. Bu özellik, `true` Bu sınıf tarafından temsil edilen güvenlik belirteci türünün bir istemciye bir hizmetin kimliğini doğrulamak için kullanılabilir olup olmadığını döndürür. Bu örnekte, kredi kartı güvenlik belirteci bir istemciye bir hizmetin kimliğini doğrulamak için kullanılamaz.  
  
5. <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A>Salt okunurdur özelliğini uygulayın. Bu özellik `true` , bu sınıf tarafından temsil edilen güvenlik belirteci türünün bir Windows hesabına eşlenip eşlenmeyeceği bir değer döndürür. Bu durumda, kimlik doğrulama sonucu bir sınıf örneği tarafından temsil edilir <xref:System.Security.Principal.WindowsIdentity> . Bu örnekte, belirteç bir Windows hesabıyla eşlenemez.  
  
6. Yöntemini uygulayın <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> . Bu yöntem, bu güvenlik belirteci parametreleri sınıfı tarafından temsil edilen güvenlik belirteci örneğine bir başvuru gerektirdiğinde WCF güvenlik çerçevesi tarafından çağrılır. Hem gerçek güvenlik belirteci örneği hem de <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> istenen başvurunun türünü belirten bağımsız değişken olarak Bu metoda geçirilir. Bu örnekte, kredi kartı güvenlik belirteci tarafından yalnızca iç başvurular desteklenir. <xref:System.IdentityModel.Tokens.SecurityToken>Sınıfında iç başvurular oluşturma işlevselliği vardır; bu nedenle, uygulama ek kod gerektirmez.  
  
7. Yöntemini uygulayın <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> . Bu yöntem, güvenlik belirteci parametreleri sınıf örneğini sınıfının bir örneğine dönüştürmek için WCF tarafından çağırılır <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> . Sonuç, uygun güvenlik belirteci örneğini oluşturmak için güvenlik belirteci sağlayıcıları tarafından kullanılır.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Güvenlik belirteçleri, bellek içi güvenlik belirteci gösterimi ve hat üzeri gösterimi arasında bir çeviri mekanizması gerektiren SOAP iletileri içinde iletilir. WCF bu görevi gerçekleştirmek için bir güvenlik belirteci serileştirici kullanır. Her özel belirteç, SOAP iletisinden özel güvenlik belirtecini seri hale getirmek ve serisini kaldırmak için özel bir güvenlik belirteci seri hale getirme ile birlikte kullanılmalıdır.  
  
> [!NOTE]
> Türetilmiş anahtarlar varsayılan olarak etkindir. Özel bir güvenlik belirteci oluşturur ve bunu birincil belirteç olarak kullanırsanız, WCF ondan bir anahtar türetir. Bunu yaparken özel güvenlik belirteci seri hale getiricisini çağırarak <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> özel güvenlik belirteci için ' ni, Tel olarak serileştirirken yazmak için çağırır `DerivedKeyToken` . Alma sonunda, belirtecin tel dışı olması `DerivedKeyToken` halinde seri hale getirici, `SecurityTokenReference` kendi altındaki en üst düzey alt öğe olarak bir öğesi bekler. Özel güvenlik belirteci seri hale getirici `SecurityTokenReference` yan tümce türünü serileştirirken bir öğe eklememediyseniz, bir özel durum oluşturulur.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Özel bir güvenlik belirteci seri hale getirici oluşturmak için  
  
1. Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> .  
  
2. <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> <xref:System.Xml.XmlReader> XML akışını okumak için öğesine bağımlı olan yöntemini geçersiz kılın. Yöntemi, `true` seri hale getirici uygulamasının geçerli öğesine göre güvenlik belirtecinin serisini kaldıramıyor durumunda döndürür. Bu örnekte, bu yöntem XML okuyucunun geçerli XML öğesinde doğru öğe adı ve ad alanına sahip olup olmadığını denetler. Değilse, XML öğesini işlemek için bu yöntemin temel sınıf uygulamasını çağırır.  
  
3. Yöntemini geçersiz kılın <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> . Bu yöntem, güvenlik belirtecinin XML içeriğini okur ve bunun için uygun bellek içi gösterimi oluşturur. Geçirilen XML okuyucusu üzerinde duran XML öğesini tanımazsa, sistem tarafından sağlanmış belirteç türlerini işlemek için temel sınıf uygulamasını çağırır.  
  
4. Yöntemini geçersiz kılın <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> . Bu yöntem, `true` bellek içi belirteç gösterimini (bağımsız değişken olarak geçirilmiş) xml gösterimine dönüştürebiliyorsanız döndürür. Dönüştüremediğinden, temel sınıf uygulamasını çağırır.  
  
5. Yöntemini geçersiz kılın <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> . Bu yöntem, bellek içi güvenlik belirteci temsilini bir XML gösterimine dönüştürür. Yöntem dönüştürülemez, temel sınıf uygulamasını çağırır.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Önceki dört yordamı tamamladıktan sonra, özel güvenlik belirtecini güvenlik belirteci sağlayıcısı, kimlik doğrulayıcı, yönetici ve istemci ve hizmet kimlik bilgileriyle tümleştirin.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Özel güvenlik belirtecini bir güvenlik belirteci sağlayıcısıyla bütünleştirmek için  
  
1. Güvenlik belirteci sağlayıcısı oluşturur, (gerekliyse) ve belirtecinin bir örneğini döndürür. Özel güvenlik belirteci için özel bir sağlayıcı oluşturmak üzere sınıfından devralan bir sınıf oluşturun <xref:System.IdentityModel.Selectors.SecurityTokenProvider> . Aşağıdaki örnek <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> , bir örneğini döndürmek için yöntemini geçersiz kılar `CreditCardToken` . Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel güvenlik belirteci sağlayıcısı oluşturma](how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Özel güvenlik belirtecini bir güvenlik belirteci kimlik doğrulayıcısı ile tümleştirme  
  
1. Güvenlik belirteci kimlik doğrulayıcısı, iletiden ayıklandığında güvenlik belirtecinin içeriğini doğrular. Özel güvenlik belirteci için özel bir Authenticator oluşturmak üzere sınıfından devralan bir sınıf oluşturun <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> . Aşağıdaki örnek, yöntemini geçersiz kılar <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> . Özel güvenlik belirteci kimlik doğrulayıcılar hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcısı oluşturma](how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Özel güvenlik belirtecini bir güvenlik belirteci yöneticisiyle tümleştirme  
  
1. Güvenlik belirteci Yöneticisi uygun belirteç sağlayıcısını, güvenlik Authenticator ve belirteç seri hale getirici örneklerini oluşturur. Özel bir belirteç Yöneticisi oluşturmak için sınıfından devralan bir sınıf oluşturun <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> . Sınıfının birincil yöntemleri, <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> uygun sağlayıcıyı ve istemci ya da hizmet kimlik bilgilerini oluşturmak için bir kullanır. Özel güvenlik belirteci yöneticileri hakkında daha fazla bilgi için bkz. [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Özel güvenlik belirtecini özel istemci ve hizmet kimlik bilgileriyle tümleştirme  
  
1. Özel güvenlik belirteci içeriğini sağlamak ve kimliğini doğrulamak için daha önce oluşturulan özel güvenlik belirteci altyapısı tarafından kullanılan özel belirteç bilgilerinin belirtilmesine izin vermek üzere uygulamanın bir API sağlaması için özel istemci ve hizmet kimlik bilgileri eklenmelidir. Aşağıdaki örnekler bunun nasıl yapılacağını göstermektedir. Özel istemci ve hizmet kimlik bilgileri hakkında daha fazla bilgi için bkz. [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Daha önce oluşturulan özel güvenlik belirteci parametreleri sınıfı, WCF güvenlik çerçevesine bir hizmetle iletişim kurulurken özel bir güvenlik belirtecinin kullanılması gerektiğini bildirmek için kullanılır. Aşağıdaki yordamda bunun nasıl yapılabileceği gösterilmektedir.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Özel güvenlik belirtecini bağlama ile tümleştirme  
  
1. Özel güvenlik belirteci parametreleri sınıfı, sınıfta gösterilen belirteç parametreleri koleksiyonlarından birinde belirtilmelidir <xref:System.ServiceModel.Channels.SecurityBindingElement> . Aşağıdaki örnek tarafından döndürülen koleksiyonu kullanır `SignedEncrypted` . Kod, kredi kartı özel belirtecini istemciden hizmete gönderilen her iletiye, içeriği otomatik olarak imzalanmış ve şifreli olarak ekler.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 Bu konu, özel bir belirteci uygulamak ve kullanmak için gereken çeşitli kod parçalarını gösterir. Tüm bu kod parçalarının nasıl birlikte uyduğunu gösteren tüm bir örnek görmek için bkz. [özel belirteç](../samples/custom-token.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.SecurityToken>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>
- <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>
- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)
- [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](how-to-create-a-custom-security-token-authenticator.md)
- [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](how-to-create-a-custom-security-token-provider.md)
