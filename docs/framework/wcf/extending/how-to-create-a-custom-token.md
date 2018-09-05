---
title: 'Nasıl yapılır: Özel Belirteç Oluşturma'
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
ms.openlocfilehash: fd168bf2e5233d9119872b267aea466a7af07041
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672807"
---
# <a name="how-to-create-a-custom-token"></a>Nasıl yapılır: Özel Belirteç Oluşturma
Bu konuda, kullanarak bir özel güvenlik belirteci oluşturma işlemi gösterilmektedir <xref:System.IdentityModel.Tokens.SecurityToken> sınıfı ve bir özel güvenlik belirteci sağlayıcı ve authenticator ile tümleştirmeyi öğreneceksiniz. Tam kod örneği için bkz. [özel belirteç](../../../../docs/framework/wcf/samples/custom-token.md) örnek.  
  
 A *güvenlik belirteci* temelde Windows Communication Foundation (WCF) güvenlik çerçevesi tarafından SOAP iletisi içinde bir gönderici talepleri belirtmek için kullanılan bir XML öğesi. WCF güvenlik sistem tarafından sağlanan kimlik doğrulama modları için çeşitli belirteçleri sağlar. Örnekler tarafından temsil edilen bir X.509 sertifikası güvenlik belirteci <xref:System.IdentityModel.Tokens.X509SecurityToken> sınıf veya bir kullanıcı adı güvenlik belirteci temsil ettiği <xref:System.IdentityModel.Tokens.UserNameSecurityToken> sınıfı.  
  
 Bazen bir kimlik doğrulama modu veya kimlik bilgisi sağlanan türleri tarafından desteklenmiyor. Bu durumda, özel kimlik bilgisi SOAP iletisi içinde bir XML temsilini sağlamak için bir özel güvenlik belirteci oluşturmak gereklidir.  
  
 Aşağıdaki yordamlar, bir özel güvenlik belirteci oluşturma ve WCF güvenlik altyapı ile tümleştirmek nasıl gösterir. Bu konuda, müşterinin kredi kartı bilgilerini sunucuya geçirmek için kullanılan bir kredi kartı belirteci oluşturur.  
  
 Özel kimlik bilgileri ve güvenlik belirteci Yöneticisi hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Bkz: <xref:System.IdentityModel.Tokens> güvenlik belirteçlerini temsil eden daha fazla sınıflar için ad alanı.  
  
 Kimlik bilgileri, güvenlik belirteci yöneticisi ve sağlayıcısı ve authenticator sınıfları hakkında daha fazla bilgi için bkz: [güvenlik mimarisi](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Yordamlar  
 Bir istemci uygulaması, güvenlik altyapısı için kredi kartı bilgilerini belirtmek için bir yol sağlanmalıdır. Bu bilgiler, özel istemci kimlik bilgileri sınıfı tarafından uygulamaya kullanılabilir hale getirilir. İlk adım, özel istemci kimlik bilgileri için kredi kartı bilgilerini temsil etmek için bir sınıf oluşturmaktır.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>İstemci kimlik bilgileri içinde kredi kartı bilgilerini temsil eden bir sınıf oluşturmak için  
  
1.  Uygulama için kredi kartı bilgilerini temsil eden yeni bir sınıf tanımlar. Aşağıdaki örnek, sınıf adları `CreditCardInfo`.  
  
2.  Özel belirteç için gereken bilgileri bir uygulama kümesi izin vermek için sınıfa uygun özellikler ekleyin. Bu örnekte, sınıf üç özelliğe sahiptir: `CardNumber`, `CardIssuer`, ve `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Ardından, özel güvenlik belirteci temsil eden bir sınıf oluşturulmalıdır. Bu sınıf, WCF güvenlik altyapısı gelen ve giden güvenlik belirteci bilgilerini geçirmek için güvenlik belirteci sağlayıcı, authenticator ve seri hale getirici sınıfları tarafından kullanılır.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Özel güvenlik belirteci sınıfı oluşturmak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.IdentityModel.Tokens.SecurityToken> sınıfı. Bu örnek adlı bir sınıf oluşturur `CreditCardToken`.  
  
2.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> özelliği. Bu özellik, yerel tanımlayıcısını SOAP iletisi içinde diğer öğelerden güvenlik belirteci XML gösterimine işaret etmek için kullanılan güvenlik belirteci almak için kullanılır. Bu örnekte, bir belirteç tanımlayıcı ya da ona bir oluşturucu parametresi geçirilebilir veya bir güvenlik belirteci örneği oluşturulduğunda yeni rastgele bir oluşturulur.  
  
3.  Uygulama <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> özelliği. Bu özellik, bir güvenlik belirteci örneği temsil eden güvenlik anahtarların koleksiyonunu döndürür. Bu anahtarları WCF tarafından oturum veya SOAP iletisi bölümleri şifrelemek için kullanılabilir. Bu örnekte, kredi kartı güvenlik belirteci herhangi bir güvenlik anahtarı içeremez; Bu nedenle, uygulama her zaman boş bir koleksiyon döndürür.  
  
4.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> ve <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> özellikleri. Bu özellikler, güvenlik belirteci örneği geçerliliğini belirlemek için WCF tarafından kullanılır. Bu örnekte, kredi kartı güvenlik belirteci yalnızca bir sona erme tarihi vardır. Bu nedenle `ValidFrom` özelliği döndürür bir <xref:System.DateTime> örnek oluşturma saat ve tarihi temsil eden.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Yeni bir güvenlik belirteci türü oluşturulduğunda, uygulaması gerektirir. <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> sınıfı. Uygulama, güvenlik bağlama öğesi Yapılandırması'nda, yeni belirteç türü temsil etmek için kullanılır. Güvenlik belirteci parametreleri sınıfı bir ileti işlenirken gerçek güvenlik belirteci örneğine eşleştirmek için kullanılan bir şablon olarak görev yapar. Şablon uygulama kullanılan ya da kimlik doğrulaması için güvenlik belirteci eşleşmelidir ölçütlerini belirtmek için kullanabileceğiniz ek özellikler sağlar. Aşağıdaki örnek, herhangi bir ek özellik, yalnızca bir güvenlik belirteci örneği için kullanılacak veya doğrulamak için WCF altyapısı ararken belirteç türü eşleşen güvenlik eklemez.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Özel güvenlik belirteci parametreleri sınıfı oluşturmak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> sınıfı.  
  
2.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> yöntemi. Varsa, bir sınıf içinde tanımlanan tüm iç alanların kopyalayın. Bu örnek, herhangi bir ek alan tanımlamıyor.  
  
3.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> salt okunur özelliği. Bu özellik döndürür `true` Bu sınıf tarafından temsil edilen güvenlik belirteci türü bir hizmete istemcinin kimliğini doğrulamak için kullanılabilir. Bu örnekte, kredi kartı güvenlik belirteci, bir hizmete istemcinin kimliğini doğrulamak için kullanılabilir.  
  
4.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> salt okunur özelliği. Bu özellik döndürür `true` Bu sınıf tarafından temsil edilen güvenlik belirteci türü bir hizmete istemcinin kimliğini doğrulamak için kullanılabilir. Bu örnekte, kredi kartı güvenlik belirteci, bir hizmete istemcinin kimliğini doğrulamak için kullanılamaz.  
  
5.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> salt okunur özelliği. Bu özellik döndürür `true` için bir Windows hesabı eşlenebilir Bu sınıf tarafından temsil edilen güvenlik belirteç türü. Bu nedenle, kimlik doğrulaması sonucu olarak gösteriliyorsa bir <xref:System.Security.Principal.WindowsIdentity> sınıfı örneği. Bu örnekte, bir Windows hesabı için belirteç eşlenemez.  
  
6.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> yöntemi. Bu yöntem bu güvenlik belirteci parametreleri sınıfı tarafından temsil edilen güvenlik belirteci örneğe bir başvuru gerektirir WCF güvenlik çerçevesi tarafından çağrılır. Her ikisi de gerçek güvenlik belirteci örnek ve <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> belirten istenen başvuru türü, bu yönteme bağımsız değişken olarak geçirilir. Bu örnekte, yalnızca iç başvuruları kredi kartı güvenlik belirteci tarafından desteklenir. <xref:System.IdentityModel.Tokens.SecurityToken> İç başvuru oluşturmak için İşlevler sınıfında; bu nedenle, uygulama, ek kod gerektirmez.  
  
7.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> yöntemi. Bu yöntem, örneğini güvenlik belirteci parametreleri sınıf örneği dönüştürmek için WCF tarafından çağrılır <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> sınıfı. Sonuç, uygun güvenlik belirteci örneği oluşturmak için güvenlik belirteci sağlayıcıları tarafından kullanılır.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Güvenlik belirteçleri, bellek içi güvenlik belirteci gösterimi ve -hat üzerinde gösterimi arasında bir çeviri mekanizması gerektiren SOAP iletilerini içine aktarılır. WCF güvenlik belirteci serileştiriciye bu görevi gerçekleştirmek için kullanır. Seri hale getirmek ve seri durumdan SOAP iletisi özel güvenlik belirteci özel güvenlik belirteci serileştiriciye tarafından her özel bir belirteç bulunmalıdır.  
  
> [!NOTE]
>  Türetilen anahtarlar varsayılan olarak etkindir. WCF bir anahtarı bir özel güvenlik belirteci oluşturmak ve birincil belirteç olarak kullanın, ondan türetilen. Bunu yaparken yazmak için özel güvenlik belirteci serileştiriciye çağırır <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> seri hale getirme sırasında özel güvenlik belirteci `DerivedKeyToken` kablo için. Alan uçta kablo kapatma belirteci işlenirken `DerivedKeyToken` seri hale getirici bekliyor bir `SecurityTokenReference` olarak kendi altına en üst düzey alt öğesi. Özel güvenlik belirteci serileştiriciye eklemediğiniz varsa bir `SecurityTokenReference` yan tümcesi türü seri hale getirme sırasında öğesi, bir özel durumu oluşturulur.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Özel güvenlik belirteci serileştiriciye oluşturmak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> sınıfı.  
  
2.  Geçersiz kılma <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> dayanan yöntemi, bir <xref:System.Xml.XmlReader> XML akışı okunamadı. Yöntem döndürür `true` seri hale getirici uygulama tabanlı bir güvenlik belirteci seri durumdan çıkarabiliyorsa, geçerli öğe verilen. Bu örnekte, bu yöntem, XML okuyucusu geçerli olup olmadığını, doğru öğe adı ve ad alanı XML öğesi sahip olmadığını denetler. Kullanmıyorsa, temel sınıf uygulamasına XML öğesini işlemek için bu yöntemi çağırır.  
  
3.  Geçersiz kılma <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> yöntemi. Bu yöntem, güvenlik belirteci XML içeriğini okur ve onun için uygun bellek içi gösterimi oluşturur. XML öğesi üzerinde Geçilen XML okuyucusu duran tanımazsa sistem tarafından sağlanan belirteç türleri işlemek için taban sınıf uygulamasını çağırır.  
  
4.  Geçersiz kılma <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> yöntemi. Bu yöntem döndürür `true` , XML gösterimine (bağımsız değişken olarak geçirilen) bellekteki belirteci gösterimine dönüştürebilirsiniz. Dönüştüremezse, temel sınıf uygulamasına çağırır.  
  
5.  Geçersiz kılma <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> yöntemi. Bu yöntem, bir bellek içi güvenlik belirteci temsili bir XML gösterimine dönüştürür. Yöntem dönüştüremezse, temel sınıf uygulamasına çağırır.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Özel güvenlik belirteci, dört önceki yordamı tamamladıktan sonra güvenlik belirteci sağlayıcı, kimlik doğrulayıcı, Yöneticisi ve hizmet ve istemci kimlik bilgileri ile tümleştirin.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Özel güvenlik belirteci bir güvenlik belirteci sağlayıcısı ile tümleştirme  
  
1.  Güvenlik belirteci sağlayıcı oluşturur (gerekirse) değiştirir ve belirteç örneğini döndürür. Özel güvenlik belirteci için özel bir sağlayıcı oluşturmak için devralınan bir sınıf oluşturma <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı. Aşağıdaki örnek geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> örneği döndürülecek yöntemi `CreditCardToken`. Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel bir güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Özel güvenlik belirteci ile bir güvenlik belirteci kimlik doğrulayıcı tümleştirmek için  
  
1.  İleti ayıklandığında güvenlik belirteci kimlik doğrulayıcı içeriği güvenlik belirteci doğrular. Özel güvenlik belirteci için özel bir kimlik doğrulayıcısı oluşturmak için devralınan bir sınıf oluşturma <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> sınıfı. Aşağıdaki örnek geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> yöntemi. Özel güvenlik belirteci kimlik doğrulayıcılar hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Özel güvenlik belirteci bir güvenlik belirteci yöneticisi ile tümleştirmek için  
  
1.  Güvenlik belirteci yöneticisi, uygun bir belirteç sağlayıcısı, güvenlik kimlik doğrulayıcı ve belirteci serileştiriciye örneklerini oluşturur. Özel bir belirteci yöneticisi oluşturmak için devralınan bir sınıf oluşturma <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı. Birincil sınıf kullanımı yöntemlerinin bir <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> istemci veya hizmet kimlik bilgilerini ve uygun bir sağlayıcı oluşturmak için. Özel güvenlik belirteci yöneticileri hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Özel güvenlik belirteci özel istemci ve hizmet kimlik bilgileri ile tümleştirmek için  
  
1.  Bir API ve özel güvenlik kimlik doğrulaması sağlamak için daha önce oluşturduğunuz özel güvenlik belirteci altyapısı tarafından kullanılan özel belirteç bilgilerini belirtmeye izin vermek üzere uygulama sağlamak için özel istemci ve hizmet kimlik bilgilerini eklenmelidir belirteç içeriği. Aşağıdaki örnekler, bu nasıl yapılabilir gösterir. Özel istemci ve hizmet kimlik bilgileri hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Oluşturulan özel güvenlik belirteci parametreleri sınıfı, daha önce bir özel güvenlik belirteci hizmeti ile iletişim kurarken kullanılmalıdır WCF güvenlik çerçevesi bildirmek için kullanılır. Aşağıdaki yordam bu nasıl yapılabileceğini gösterir.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Özel güvenlik belirteci bağlama ile tümleştirmek için  
  
1.  Özel güvenlik belirteci parametreleri sınıfı üzerinde kullanıma sunulan belirteci parametreleri koleksiyonlardan biri belirtilmelidir <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. Aşağıdaki örnekte tarafından döndürülen bir koleksiyonda `SignedEncrypted`. İstemciden hizmete otomatik olarak imzalanmış ve şifrelenmiş içeriği ile gönderilen her ileti için kredi kartı özel belirteç kodu ekler.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 Bu konuda, uygulamak ve özel bir belirteç kullanmak gerekli kod çeşitli parçaları gösterilmektedir. İlişkin eksiksiz bir örnek görmek için bkz: Bu kod tüm parçaları bir araya getireceğinizi [özel belirteç](../../../../docs/framework/wcf/samples/custom-token.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.SecurityToken>  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>  
 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Güvenlik mimarisi](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
