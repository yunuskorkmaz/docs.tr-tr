---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcısı oluşturma'
title: 'Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcısı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
ms.openlocfilehash: dd1dbd413638ab8693ec5ac3454d9fac9b26565b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780758"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcısı oluşturma

Bu konu, özel bir güvenlik belirteci kimlik doğrulayıcısı oluşturmayı ve bunu özel bir güvenlik belirteci Yöneticisi ile tümleştirmeyi gösterir. Bir güvenlik belirteci kimlik doğrulayıcısı, gelen bir iletiyle birlikte sunulan bir güvenlik belirtecinin içeriğini doğrular. Doğrulama başarılı olursa, Authenticator, <xref:System.IdentityModel.Policy.IAuthorizationPolicy> değerlendirildiğinde bir talepler kümesi döndüren bir örnek koleksiyonu döndürür.  
  
 Windows Communication Foundation (WCF) içinde özel bir güvenlik belirteci kimlik doğrulayıcısı kullanmak için, önce özel kimlik bilgileri ve güvenlik belirteci Yöneticisi uygulamaları oluşturmanız gerekir. Özel kimlik bilgileri ve bir güvenlik belirteci Yöneticisi oluşturma hakkında daha fazla bilgi için bkz. [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md).
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Özel bir güvenlik belirteci kimlik doğrulayıcısı oluşturmak için  
  
1. Sınıfından türetilmiş yeni bir sınıf tanımlayın <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> .  
  
2. Yöntemini geçersiz kılın <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> . Yöntemi, `true` `false` özel Doğrulayıcı 'nın gelen belirteç türünü doğrulayıp doğrulamadığına bağlı olarak veya ' i döndürür.  
  
3. Yöntemini geçersiz kılın <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> . Bu yöntemin, belirteç içeriğini uygun şekilde doğrulaması gerekir. Belirteç doğrulama adımını geçerse, bir örnek koleksiyonu döndürür <xref:System.IdentityModel.Policy.IAuthorizationPolicy> . Aşağıdaki örnek, bir sonraki yordamda oluşturulacak özel bir yetkilendirme ilkesi uygulamasını kullanır.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Önceki kod, yönteminde bir yetkilendirme ilkeleri koleksiyonu döndürür <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> . WCF bu arabirimin genel bir uygulamasını sağlamıyor. Aşağıdaki yordamda, kendi gereksinimleriniz için bunun nasıl yapılacağı gösterilmektedir.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Özel bir yetkilendirme ilkesi oluşturmak için  
  
1. Arabirimi uygulayan yeni bir sınıf tanımlayın <xref:System.IdentityModel.Policy.IAuthorizationPolicy> .  
  
2. <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A>Salt okunurdur özelliğini uygulayın. Bu özelliği uygulamak için bir yol, sınıf oluşturucusunda bir genel benzersiz tanımlayıcı (GUID) oluşturmak ve bu özelliğin değeri her istendiğinde geri döndürmesidir.  
  
3. <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A>Salt okunurdur özelliğini uygulayın. Bu özelliğin, belirteçten elde edilen talep kümelerini veren bir veren döndürmesi gerekir. Bu veren, belirtecin vereni veya belirteç içeriğini doğrulamaktan sorumlu bir yetkiyi karşımalıdır. Aşağıdaki örnek, önceki yordamda oluşturulan özel güvenlik belirteci kimlik doğrulayıcısından bu sınıfa geçirilen veren talebini kullanır. Özel güvenlik belirteci kimlik doğrulayıcısı, <xref:System.IdentityModel.Claims.ClaimSet.System%2A> Kullanıcı adı belirtecinin vereni temsil etmek için sistem tarafından belirtilen talep kümesini (özelliği tarafından döndürülen) kullanır.  
  
4. Yöntemini uygulayın <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> . Bu yöntem, bir <xref:System.IdentityModel.Policy.EvaluationContext> sınıfın örneğini (bağımsız değişken olarak geçirilmiş), gelen güvenlik belirteci içeriğine dayalı taleplerle doldurur. Yöntemi, `true` değerlendirmede tamamlandığında döndürür. Uygulamanın, değerlendirme bağlamına ek bilgi sağlayan diğer yetkilendirme ilkelerinin varlığını temel aldığı durumlarda, bu yöntem, `false` gerekli bilgiler henüz değerlendirme bağlamında mevcut değilse dönebilir. Bu durumda, bu yetkilendirme ilkelerinden en az biri değerlendirme bağlamını değiştirmemişse, WCF, gelen ileti için oluşturulan diğer tüm yetkilendirme ilkelerini değerlendirdikten sonra yöntemi yeniden çağırır.  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [Izlenecek yol: özel istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md) , özel kimlik bilgileri ve özel bir güvenlik belirteci Yöneticisi oluşturma işlemini açıklar. Burada oluşturulan özel güvenlik belirteci kimlik doğrulamasını kullanmak için, güvenlik belirteci Yöneticisi 'nin bir uygulama, yöntemden özel kimlik doğrulayıcı döndürecek şekilde değiştirilir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> . Yöntemi, uygun bir güvenlik belirteci gereksinimi geçirildiğinde bir Authenticator döndürür.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Özel bir güvenlik belirteci kimlik doğrulamasını özel bir güvenlik belirteci Yöneticisi ile tümleştirme  
  
1. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A>Özel güvenlik belirteci Yöneticisi uygulamanızda yöntemi geçersiz kılın.  
  
2. Metoda göre özel güvenlik belirteci kimlik doğrulayıcıınızı döndürmesini sağlamak için yöntemine mantık ekleyin <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> . Aşağıdaki örnek, belirteç gereksinimleri belirteç türü bir Kullanıcı adı (özelliği tarafından temsil edilir <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> ) ve güvenlik belirteci kimlik doğrulayıcısı istenen ileti yönü (alana göre temsil edilir) ise özel bir güvenlik belirteci kimlik doğrulayıcısı döndürür <xref:System.ServiceModel.Description.MessageDirection.Input> .  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.UserNameSecurityToken>
- [İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)
- [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](how-to-create-a-custom-security-token-provider.md)
