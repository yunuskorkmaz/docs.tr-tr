---
title: "Nasıl yapılır: Özel Belirteç Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 476c28305935ec8930091d5c3700afe9dd6c2450
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-token"></a>Nasıl yapılır: Özel Belirteç Oluşturma
Bu konuda kullanarak bir özel güvenlik belirteci oluşturmak nasıl gösterilmektedir <xref:System.IdentityModel.Tokens.SecurityToken> sınıfı ve bir özel güvenlik belirteci sağlayıcısı ile authenticator ile tümleştirme. Tam kod örneği için bkz: [özel belirteç](../../../../docs/framework/wcf/samples/custom-token.md) örnek.  
  
 A *güvenlik belirteci* temelde tarafından kullanılan bir XML öğesi [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenlik framework SOAP iletisi içinde bir gönderici hakkında talepleri temsil eder. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Güvenlik sistem tarafından sağlanan kimlik doğrulama modları için çeşitli belirteçleri sağlar. Örnekler tarafından temsil edilen bir X.509 sertifikası güvenlik belirteci <xref:System.IdentityModel.Tokens.X509SecurityToken> sınıf veya bir kullanıcı adı güvenlik belirteci temsil ettiği <xref:System.IdentityModel.Tokens.UserNameSecurityToken> sınıfı.  
  
 Bazen bir kimlik doğrulama modu veya kimlik bilgileri sağlanan türleri tarafından desteklenmiyor. Bu durumda, bir XML temsili SOAP iletisi içinde özel kimlik bilgileri sağlamak için bir özel güvenlik belirteci oluşturmak gereklidir.  
  
 Bir özel güvenlik belirteci oluşturma ve nasıl ile tümleştirmek aşağıdaki yordamları gösteren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik altyapısı. Bu konuda istemcinin kredi kartı bilgilerini sunucuya geçirmek için kullanılan bir kredi kartı belirteci oluşturur.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Özel kimlik bilgileri ve güvenlik belirteci yöneticisi bkz [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Bkz: <xref:System.IdentityModel.Tokens> güvenlik belirteçlerini temsil eden daha fazla sınıflar için ad alanı.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kimlik bilgileri, güvenlik belirteci yöneticisi ve sağlayıcı ve Doğrulayıcı sınıfları, bkz: [güvenlik mimarisi](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Yordamlar  
 Bir istemci uygulaması, güvenlik altyapısı kredi kartı bilgilerini belirtmek için bir yol sağlanmalıdır. Bu bilgiler bir özel istemci kimlik bilgileri sınıf tarafından uygulamaya kullanılabilir hale getirilir. İlk adım, özel istemci kimlik bilgileri için kredi kartı bilgileri temsil eden bir sınıf oluşturmaktır.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>İstemci kimlik bilgileri içinde kredi kartı bilgilerini temsil eden bir sınıf oluşturmak için  
  
1.  Uygulama için kredi kartı bilgilerini temsil eden yeni bir sınıf tanımlayın. Aşağıdaki örnek sınıf adları `CreditCardInfo`.  
  
2.  Bir uygulama için özel belirteç gerekli bilgiler kümesi izin vermek için sınıfına uygun özellikleri ekleyin. Bu örnekte, üç özellik sınıfı vardır: `CardNumber`, `CardIssuer`, ve `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Ardından, özel güvenlik belirteci temsil eden bir sınıf oluşturulmalıdır. Bu sınıf güvenlik belirteci hakkında bilgi ve ondan iletmek için güvenlik belirteci sağlayıcısı, doğrulayıcı ve seri hale getirici sınıfları tarafından kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik altyapısı.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Özel güvenlik belirteci sınıfı oluşturmak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Tokens.SecurityToken> sınıfı. Bu örnek adlı bir sınıf oluşturur `CreditCardToken`.  
  
2.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> özelliği. Bu özellik, yerel güvenlik belirteci XML gösterimine SOAP iletisi içinde diğer öğelerden işaret etmek için kullanılan güvenlik belirteci tanıtıcısı almak için kullanılır. Bu örnekte, bir belirteç tanımlayıcı ya da ona Oluşturucusu parametre olarak geçirilebilir veya bir güvenlik belirteci örneği oluşturulan her zaman yeni rastgele bir oluşturulur.  
  
3.  Uygulama <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> özelliği. Bu özellik, bir güvenlik belirteci örneği temsil eden güvenlik anahtarların koleksiyonunu döndürür. Böyle anahtarların tarafından kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oturum veya SOAP iletisi bölümleri şifrelemek için. Bu örnekte, kredi kartı güvenlik belirteci herhangi bir güvenlik anahtarı içeremez; Bu nedenle, uygulama her zaman boş bir koleksiyon döndürür.  
  
4.  Geçersiz kılma <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> ve <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> özellikleri. Bu özellikler tarafından kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik belirteci örneği geçerliliğini belirlemek için. Bu örnekte, kredi kartı güvenlik belirteci yalnızca bir sona erme tarihi vardır. Bu nedenle `ValidFrom` özelliği döndürür bir <xref:System.DateTime> örnek oluşturma saat ve tarihi temsil eden.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Yeni bir güvenlik belirteci türü oluşturulduğunda, uygulaması gerektirir <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> sınıfı. Uygulama güvenlik bağlama öğesi Yapılandırması'nda, yeni belirteç türü temsil etmek için kullanılır. Güvenlik belirteci parametreleri sınıfı bir ileti işlenirken gerçek güvenlik belirteci örneğine eşleştirmek için kullanılan bir şablon olarak görev yapar. Şablon bir uygulama kullanılan ya da kimlik doğrulaması için güvenlik belirteci eşleşmelidir ölçütlerini belirtmek için kullanabileceğiniz ek özellikler sağlar. Aşağıdaki örnekte herhangi bir ek özellik, yalnızca belirteç türü eşleşir güvenlik eklemez zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir güvenlik belirteci örneği kullanmak için veya doğrulamak için altyapı arar.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Özel güvenlik belirteci parametreleri sınıfı oluşturmak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> sınıfı.  
  
2.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> yöntemi. Sınıfınızda, tanımlanan tüm iç alanlar varsa kopyalayın. Bu örnek ek alanlar tanımlamıyor.  
  
3.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> özelliği salt okunur. Bu özellik döndürür `true` Bu sınıf tarafından temsil edilen güvenlik belirteci türü bir hizmet için bir istemci kimlik doğrulaması için kullanılan durumunda. Bu örnekte, kredi kartı güvenlik belirteci, bir hizmet için bir istemci kimlik doğrulaması yapmak için kullanılabilir.  
  
4.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> özelliği salt okunur. Bu özellik döndürür `true` Bu sınıf tarafından temsil edilen güvenlik belirteci türü bir istemci bir hizmetin kimliğini kullanılabilir ise. Bu örnekte, kredi kartı güvenlik belirteci hizmeti istemci kimlik doğrulaması için kullanılamaz.  
  
5.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> özelliği salt okunur. Bu özellik döndürür `true` bir Windows hesabı eşlenebilir Bu sınıf tarafından temsil edilen güvenlik belirteci türü. Bu nedenle, kimlik doğrulaması sonucu olarak gösteriliyorsa bir <xref:System.Security.Principal.WindowsIdentity> sınıf örneği. Bu örnekte, bir Windows hesabı belirteç eşlenemez.  
  
6.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> yöntemi. Bu yöntem tarafından çağrılır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu güvenlik belirteci parametreleri sınıfı tarafından temsil edilen güvenlik belirteci örneğine başvuru gerektirdiğinde security çerçevesi. Her iki gerçek güvenlik belirteci örneği ve <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> belirtir istenen başvuru türü bu yöntem bağımsız değişken olarak geçirilir. Bu örnekte, yalnızca iç başvurular kredi kartı güvenlik belirteci tarafından desteklenir. <xref:System.IdentityModel.Tokens.SecurityToken> Sınıfı iç başvuruları oluşturmak için işlevselliği vardır; bu nedenle, uygulama ek kod gerektirmez.  
  
7.  Uygulama <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> yöntemi. Bu yöntem tarafından çağrılır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik dönüştürmek için belirteci parametreleri örneği örneğine sınıfı <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> sınıfı. Sonuç uygun güvenlik belirteci örneğini oluşturmak için güvenlik belirteci sağlayıcıları tarafından kullanılır.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Güvenlik belirteçleri, bellek içi güvenlik belirteci gösterimini ve üzerinde hat gösterimine arasında çeviri mekanizması gerektirir SOAP iletilerine içine aktarılır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu görevi gerçekleştirmek için bir güvenlik belirteci seri hale getirici kullanır. Her özel belirteci seri hale getirmek ve SOAP iletisi özel güvenlik belirteci seri durumdan özel güvenlik belirteci seri hale getirici tarafından eklenmelidir.  
  
> [!NOTE]
>  Türetilen anahtarları varsayılan olarak etkinleştirilir. Özel güvenlik belirteci oluştur ve birincil belirteç olarak kullanırsanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir anahtarı buradan türetilir. Bunu yaparken yazmak için özel güvenlik belirteci seri hale getirici çağırır <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> özel güvenlik belirteci seri hale getirme sırasında `DerivedKeyToken` kablo için. Alan uçta kablo kapalı belirteci seri durumdan çıkarılırken `DerivedKeyToken` seri hale getirici bekliyor bir `SecurityTokenReference` kendisini altında en üst düzey alt öğe. Özel güvenlik belirteci seri hale getirici eklemediğiniz varsa bir `SecurityTokenReference` yan tümcesi türü seri hale getirme sırasında öğesi, bir özel durum oluşur.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Özel güvenlik belirteci seri hale getirici oluşturmak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> sınıfı.  
  
2.  Geçersiz kılma <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> dayanan yöntemi bir <xref:System.Xml.XmlReader> XML akışı okunamıyor. Yöntem `true` seri hale getirici uygulama tabanlı güvenlik belirteci seri durumdan çıkarabiliyorsa geçerli öğe verilen. Bu örnekte, bu yöntem, XML okuyucusu geçerli olup olmadığını doğru öğe adı ve ad alanı XML öğesi sahip olmadığını denetler. Yoksa, XML öğesi işlemek için bu yöntemi temel sınıf uygulamasını çağırır.  
  
3.  Geçersiz kılma <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> yöntemi. Bu yöntem güvenlik belirteci XML içeriğini okur ve onun için uygun bellek içi gösterimini oluşturur. Geçilen XML okuyucusu duran XML öğesi tanımazsa, sistem tarafından sağlanan belirteç türleri işlemek için temel sınıf uygulamasını çağırır.  
  
4.  Geçersiz kılma <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> yöntemi. Bu yöntem `true` XML gösterimine (bağımsız değişken olarak geçirilen) bellek içi belirteci gösterimi dönüştürebilirsiniz durumunda. Dönüştüremezse, temel sınıf uygulamasını çağırır.  
  
5.  Geçersiz kılma <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> yöntemi. Bu yöntem bir bellek içi güvenlik belirteci temsili bir XML gösterimine dönüştürür. Yöntem dönüştüremiyorsa, temel sınıf uygulamasını çağırır.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Özel güvenlik belirteci, dört önceki yordamları tamamladıktan sonra güvenlik belirteci sağlayıcısı, Doğrulayıcı, Yöneticisi ve hizmet ve istemci kimlik bilgileri ile tümleştirin.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Özel güvenlik belirteci bir güvenlik belirteci sağlayıcısı ile tümleştirmek için  
  
1.  Güvenlik belirteci sağlayıcısı oluşturur, (gerekirse) değiştirir ve belirteç örneğini döndürür. Özel güvenlik belirteci için özel bir sağlayıcı oluşturmak için öğesinden devralınan bir sınıf oluşturun <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı. Aşağıdaki örnekte geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> örneği döndürülecek yöntemi `CreditCardToken`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel güvenlik belirteci sağlayıcıları Bkz [nasıl yapılır: özel bir güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Özel güvenlik belirteci bir güvenlik belirteci kimlik doğrulayıcı ile tümleştirmek için  
  
1.  Güvenlik belirteci kimlik doğrulayıcı iletiden ayıklandığında güvenlik belirteci içeriğini doğrular. Özel güvenlik belirteci için özel bir kimlik doğrulayıcısı oluşturmak için öğesinden devralınan bir sınıf oluşturun <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> sınıfı. Aşağıdaki örnekte geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> yöntemi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel güvenlik belirteci Doğrulayıcı bkz [nasıl yapılır: bir özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Özel güvenlik belirteci bir güvenlik belirteci yöneticisi ile tümleştirmek için  
  
1.  Güvenlik belirteci yöneticisi uygun belirteç sağlayıcısı, güvenlik kimlik doğrulayıcısı ve belirteci seri hale getirici örneklerini oluşturur. Özel bir belirteci yöneticisi oluşturmak için öğesinden devralınan bir sınıf oluşturun <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı. Sınıf kullanım birincil yöntemleri bir <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> istemci veya hizmet kimlik bilgilerini ve uygun sağlayıcısı oluşturmak için. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özel güvenlik belirteci yöneticileri Bkz [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Özel güvenlik belirteci özel istemci ve hizmet kimlik bilgileri ile tümleştirmek için  
  
1.  Özel istemci ve hizmet kimlik bilgilerini sağlayın ve özel güvenlik kimlik doğrulaması yapmak için daha önce oluşturduğunuz özel güvenlik belirteci altyapısı tarafından kullanılan özel belirteç bilgileri belirtme izin vermek üzere uygulama için bir API sağlamak için eklenmesi gerekir belirteç içeriği. Aşağıdaki örnekler, bu nasıl yapılabilir gösterir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Özel istemci ve hizmet kimlik bilgilerini görmek [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Oluşturulan özel güvenlik belirteci parametreleri sınıfı daha önce bildirmek için kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir özel güvenlik belirteci olmalıdır güvenlik framework hizmeti ile iletişim kurarken kullanılan. Aşağıdaki yordam bu nasıl yapılabilir gösterir.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Özel güvenlik belirteci bağlama ile tümleştirmek için  
  
1.  Özel güvenlik belirteci parametreleri sınıfı üzerinde gösterilen belirteci parametreleri koleksiyonları birinde belirtilmelidir <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. Aşağıdaki örnek, tarafından döndürülen koleksiyon kullanır `SignedEncrypted`. Kod istemciden hizmete otomatik olarak İmzalanabilir ve şifrelenebilir içeriği ile gönderilen her ileti kredi kartı özel simgesi ekler.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 Bu konu özel belirteç kullanın ve uygulanması için gerekli çeşitli kod parçalarını gösterir. Nasıl tam bir örnek görmek için bkz: tüm bu kod parçalarını bir araya getireceğinizi [özel belirteç](../../../../docs/framework/wcf/samples/custom-token.md).  
  
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
 [İzlenecek yol: Özel istemci ve hizmet kimlik bilgileri oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Nasıl yapılır: özel güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Güvenlik mimarisi](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
