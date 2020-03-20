---
title: Nasıl?
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
ms.openlocfilehash: 7bbe59958f59f76046c0a112463cfa64d09c14d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185584"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Nasıl?
Bu konu, özel güvenlik belirteci kimlik doğrulayıcısını nasıl oluşturacağımı ve özel güvenlik belirteç yöneticisiyle nasıl tümleştirilebildiğini gösterir. Güvenlik belirteci kimlik doğrulayıcısı, gelen iletiyle sağlanan bir güvenlik belirteci içeriğini doğrular. Doğrulama başarılı olursa, kimlik doğrulayıcısı değerlendirildiğinde <xref:System.IdentityModel.Policy.IAuthorizationPolicy> bir dizi talep döndüren bir örnek koleksiyonunu döndürür.  
  
 Windows Communication Foundation'da (WCF) özel güvenlik belirteç kimlik doğrulayıcısı kullanmak için önce özel kimlik bilgileri ve güvenlik belirteç yöneticisi uygulamaları oluşturmanız gerekir. Özel kimlik bilgileri ve güvenlik belirteç yöneticisi oluşturma hakkında daha fazla bilgi için [Bkz. Walkthrough: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma.](walkthrough-creating-custom-client-and-service-credentials.md)
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Özel güvenlik belirteci kimlik doğrulayıcısı oluşturmak için  
  
1. Sınıftan türetilen yeni <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> bir sınıf tanımlayın.  
  
2. <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> Yöntemi geçersiz kılın. Yöntem döner `true` `false` veya özel kimlik doğrulayıcıgelen belirteç türünü doğrulayabilir veya doğrulayabilir bağlı olarak.  
  
3. <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> Yöntemi geçersiz kılın. Bu yöntemin belirteç içeriğini uygun şekilde doğrulanması gerekir. Belirteç doğrulama adımını geçerse, bir örnek <xref:System.IdentityModel.Policy.IAuthorizationPolicy> koleksiyonu döndürür. Aşağıdaki örnek, sonraki yordamda oluşturulacak özel bir yetkilendirme ilkesi uygulaması kullanır.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Önceki kod <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> yöntemde yetkilendirme ilkeleri koleksiyonunu döndürür. WCF bu arabirimin genel bir uygulamasını sağlamaz. Aşağıdaki yordam, kendi gereksinimleriniz için bunu nasıl yapacağınızı gösterir.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Özel yetkilendirme ilkesi oluşturmak için  
  
1. Arabirimi uygulayan yeni <xref:System.IdentityModel.Policy.IAuthorizationPolicy> bir sınıf tanımlayın.  
  
2. Salt <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> okunur özelliği uygulayın. Bu özelliği uygulamanın bir yolu, sınıf oluşturucuda genel olarak benzersiz bir tanımlayıcı (GUID) oluşturmak ve bu özelliğin değeri istendiğinde onu iade etmektir.  
  
3. Salt <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> okunur özelliği uygulayın. Bu özelliğin belirteçten elde edilen talep kümelerinin verenini döndürmesi gerekir. Bu veren belirteç veya belirteç içeriğini doğrulamak için sorumlu bir makam veren karşılık etmelidir. Aşağıdaki örnek, önceki yordamda oluşturulan özel güvenlik belirteç kimlik doğrulayıcısından bu sınıfa geçen veren iddiasını kullanır. Özel güvenlik belirteci kimlik doğrulayıcısı, kullanıcı adı belirtecinin verenini temsil etmek için sistem tarafından sağlanan talep kümesini <xref:System.IdentityModel.Claims.ClaimSet.System%2A> (özellik tarafından döndürülür) kullanır.  
  
4. Yöntemi <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> uygulayın. Bu yöntem, gelen güvenlik <xref:System.IdentityModel.Policy.EvaluationContext> belirteci içeriğini temel alan sahiplerle sınıfın (bağımsız değişken olarak geçirilen) bir örneğini doldurur. Yöntem, `true` değerlendirme ile yapıldığında geri döner. Uygulamanın değerlendirme bağlamına ek bilgi sağlayan diğer yetkilendirme ilkelerinin varlığına dayandığı durumlarda, gerekli bilgiler değerlendirme bağlamında henüz mevcut değilse bu yöntem döndürülebilir. `false` Bu durumda, bu yetkilendirme ilkelerinden en az biri değerlendirme bağlamını değiştirmişse, WCF gelen ileti için oluşturulan diğer tüm yetkilendirme ilkelerini değerlendirdikten sonra yöntemi yeniden arayacaktır.  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [Walkthrough: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma,](walkthrough-creating-custom-client-and-service-credentials.md) özel kimlik bilgileri ve özel güvenlik belirteç yöneticisi nasıl oluşturulacak açıklanır. Burada oluşturulan özel güvenlik belirteç kimlik doğrulayıcısını kullanmak için, güvenlik belirteci yöneticisinin <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> uygulanması, özel kimlik doğrulayıcısını yöntemden döndürmek için değiştirilir. Uygun bir güvenlik belirteci gereksinimi geçirildiğinde yöntem bir kimlik doğrulayıcı döndürür.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Özel güvenlik belirteç doğrulayıcısını özel güvenlik belirteç yöneticisiyle tümleştirmek için  
  
1. Özel güvenlik <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> belirteç yöneticisi uygulamasında yöntemi geçersiz kılın.  
  
2. Parametreye göre özel güvenlik belirteci kimlik doğrulayıcınızı döndürmesini sağlamak için yönteme <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> mantık ekleyin. Aşağıdaki örnek, belirteç gereksinimleri belirteç türü bir kullanıcı adı <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> (özellik tarafından temsil edilir) ve güvenlik belirteci kimlik doğrulaması istenen ileti yönü giriş <xref:System.ServiceModel.Description.MessageDirection.Input> (alan tarafından temsil edilir) ise, özel bir güvenlik belirteci kimlik doğrulaması döndürür.  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.UserNameSecurityToken>
- [İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)
- [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](how-to-create-a-custom-security-token-provider.md)
