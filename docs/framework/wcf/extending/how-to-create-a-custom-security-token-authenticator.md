---
title: 'Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
author: BrucePerlerMS
ms.openlocfilehash: cbedab4064173186251defead8394735de033cf7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111808"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcı oluşturma
Bu konu, bir özel güvenlik belirteci kimlik doğrulayıcı oluşturma ve bir özel güvenlik belirteci yöneticisi ile tümleştirmek nasıl gösterir. Bir güvenlik belirteci kimlik doğrulayıcı içeriği gelen bir ileti ile sağlanan bir güvenlik belirteci doğrular. Doğrulama başarılı olursa, kimlik doğrulayıcı koleksiyonunu döndürür. <xref:System.IdentityModel.Policy.IAuthorizationPolicy> değerlendirildiğinde, örnekler, talepler kümesi döndürür.  
  
 Windows Communication Foundation (WCF) bir özel güvenlik belirteci kimlik doğrulayıcı kullanmak için öncelikle belirteci Yöneticisi uygulamaları özel kimlik bilgileri ve güvenlik oluşturmanız gerekir. Özel kimlik bilgileri ve güvenlik belirteci yöneticisi oluşturma hakkında daha fazla bilgi için bkz. [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md). Kimlik bilgileri, güvenlik belirteci yöneticisi ve sağlayıcısı ve authenticator sınıfları hakkında daha fazla bilgi için bkz: [güvenlik mimarisi](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Özel güvenlik belirteci kimlik doğrulayıcısı oluşturmak için  
  
1.  Türetilmiş yeni bir sınıf tanımlama <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> sınıfı.  
  
2.  Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> yöntemi. Yöntem döndürür `true` veya `false` bağlı olup olmadığını özel authenticator gelen belirteç türü olmadığını doğrulayabilirsiniz.  
  
3.  Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> yöntemi. Bu yöntem, belirteç içeriği uygun şekilde doğrulamak gerekir. Belirteç doğrulama adımını geçerse, koleksiyonunu döndürür. <xref:System.IdentityModel.Policy.IAuthorizationPolicy> örnekleri. Aşağıdaki örnek, bir sonraki yordamda oluşturulan bir özel yetkilendirme ilkesi uygulaması kullanır.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Önceki kod, Yetkilendirme İlkeleri koleksiyonunu döndürür <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> yöntemi. WCF bu arabirimin genel bir uygulama sağlamaz. Aşağıdaki yordam, kendi gereksinimleriniz için bunu nasıl gösterir.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Özel yetkilendirme ilkesi oluşturmak için  
  
1.  Yeni bir sınıf uygulamak tanımlamak <xref:System.IdentityModel.Policy.IAuthorizationPolicy> arabirimi.  
  
2.  Uygulama <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> salt okunur özelliği. Bu özelliği uygulamak için bir sınıf oluşturucuda bir genel benzersiz tanıtıcısı (GUID) oluşturur ve bu özellik için değer her istendiğinde döndürün yöntemdir.  
  
3.  Uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> salt okunur özelliği. Bu özellik, bir veren belirteçten elde edilen talep kümelerinin döndürülecek gerekir. Bu veren belirteci veya belirteç içeriği doğrulamak için sorumlu olduğu bir yetki veren karşılık gelmelidir. Aşağıdaki örnek önceki yordamda oluşturduğunuz özel güvenlik belirteci kimlik doğrulayıcı öğesinden bu sınıfa geçirilen verenin talep kullanır. Özel güvenlik belirteci kimlik doğrulayıcı sistem tarafından sağlanan talep kümesi kullanır (tarafından döndürülen <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özelliği) kullanıcı adı belirteci veren temsil etmek için.  
  
4.  Uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yöntemi. Bu yöntem bir örneğini doldurur <xref:System.IdentityModel.Policy.EvaluationContext> gelen güvenlik belirteci içeriğine göre talep sınıfı (bağımsız değişken olarak geçirilen). Yöntem döndürür `true` ile değerlendirme tamamlandığında. Durumlarda uygulama varlığını değerlendirme bağlamı için ek bilgiler sağlayan diğer yetkilendirme ilkelerini kullanır, bu yöntem döndürebilir `false` gerekli bilgiler yoksa değerlendirme bağlamında henüz. Bu durumda, WCF, bu Yetkilendirme İlkeleri en az biri değerlendirme bağlamı değiştirilirse gelen ileti için oluşturulan diğer yetkilendirme ilkeleri değerlendirdikten sonra yöntemini çağıracaksınız.  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [İzlenecek yol: Özel istemci ve hizmet kimlik bilgilerini oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md) özel kimlik bilgileri ve özel bir güvenlik belirteci yöneticisi oluşturmayı açıklar. Oluşturulan özel güvenlik belirteci kimlik doğrulayıcı kullanmak için burada, güvenlik belirteci Yöneticisi uygulaması özel kimlik doğrulayıcıdan döndürecek şekilde değiştirilir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> yöntemi. Uygun güvenlik belirteç gereksinimi geçirildiğinde yöntem bir kimlik doğrulayıcı döndürür.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Bir özel güvenlik belirteci kimlik doğrulayıcı özel güvenlik belirteci yöneticisi ile tümleştirmek için  
  
1.  Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> özel güvenlik belirteci yöneticisi uygulamanızda yöntemi.  
  
2.  Temel, özel güvenlik belirteci kimlik doğrulayıcı döndürülecek etkinleştirmek için yöntemi mantık eklemek <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametresi. Bir kullanıcı adı belirteci gereksinimleri belirteç türü ise, aşağıdaki örnek bir özel güvenlik belirteci kimlik doğrulayıcı döndürür (tarafından temsil edilen <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> özelliği) ve kendisi için güvenlik belirteci kimlik doğrulayıcı istenen ileti yönü giriş () tarafından temsil edilen <xref:System.ServiceModel.Description.MessageDirection.Input> alan).  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
 
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>  
 [İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Güvenlik mimarisi](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
