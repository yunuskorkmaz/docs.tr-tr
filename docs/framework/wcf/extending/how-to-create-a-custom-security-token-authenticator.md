---
title: "Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 4415edbe9f04cb56cefadcb3ae521994fac28ffb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma
Bu konuda bir özel güvenlik belirteci kimlik doğrulayıcı oluşturma ve bir özel güvenlik belirteci manager ile tümleştirerek gösterilmektedir. Bir güvenlik belirteci kimlik doğrulayıcı gelen ileti ile sağlanan bir güvenlik belirteci içeriğini doğrular. Doğrulama başarılı olursa, Doğrulayıcı koleksiyonunu döndürür <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , değerlendirildiğinde, örnekler talep kümesini döndürür.  
  
 İçinde bir özel güvenlik belirteci kimlik doğrulayıcı kullanmak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], önce özel kimlik bilgileri ve güvenlik belirteci Yöneticisi uygulamaları oluşturmanız gerekir. Özel kimlik bilgileri ve bir güvenlik belirteci yöneticisi oluşturma hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md). Kimlik bilgileri, güvenlik belirteci yöneticisi ve sağlayıcı ve Doğrulayıcı sınıfları hakkında daha fazla bilgi için bkz: [güvenlik mimarisi](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Özel güvenlik belirteci kimlik doğrulayıcısı oluşturmak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> sınıfı.  
  
2.  Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> yöntemi. Yöntem `true` veya `false` bağlı olup olmadığını özel Doğrulayıcı gelen belirteç türü veya doğrulayabilirsiniz.  
  
3.  Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> yöntemi. Belirteç içerikleri uygun şekilde doğrulamak bu yöntem gerekir. Belirteç doğrulama adımını geçerse, bir koleksiyonunu döndürür <xref:System.IdentityModel.Policy.IAuthorizationPolicy> örnekleri. Aşağıdaki örnek bir sonraki yordamda oluşturduğunuz özel yetkilendirme ilkesi uygulaması kullanır.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Önceki kod Yetkilendirme İlkeleri koleksiyonunu döndürür <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> yöntemi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu arabirimin ortak bir uygulama sağlamaz. Aşağıdaki yordamda, kendi gereksinimlerinizi için bunu gösterilmiştir.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Bir özel yetkilendirme ilkesi oluşturmak için  
  
1.  Yeni bir sınıf uygulama tanımlamak <xref:System.IdentityModel.Policy.IAuthorizationPolicy> arabirimi.  
  
2.  Uygulama <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> özelliği salt okunur. Bu özelliği uygulamak için bir sınıf oluşturucuda bir genel benzersiz tanımlayıcı (GUID) oluşturmak ve bu özellik için değer her istendiğinde dönmek için yoludur.  
  
3.  Uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> özelliği salt okunur. Bu özellik, bir veren belirtecinden elde edilen talep kümelerinin döndürmesi gerekir. Bu veren belirteç veya belirteç içerikleri doğrulamak için sorumlu olduğu bir yetki veren karşılık gelmelidir. Aşağıdaki örnek, önceki yordamda oluşturduğunuz özel güvenlik belirteci kimlik doğrulayıcı öğesinden bu sınıfa geçirilen verenin talep kullanır. Özel güvenlik belirteci kimlik doğrulayıcı sistem tarafından sağlanan talep kümesi kullanır (tarafından döndürülen <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özelliği) kullanıcıadı Belirteç Verenin temsil etmek için.  
  
4.  Uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yöntemi. Bu yöntem örneği doldurur <xref:System.IdentityModel.Policy.EvaluationContext> gelen güvenlik belirteci içeriğine göre taleplerle sınıfı (bağımsız değişken olarak geçirilen). Yöntem `true` zaman onu yapılır ile değerlendirme. Bu yöntemi uygulaması değerlendirme bağlam için ek bilgiler sağlayan diğer yetkilendirme ilkeleri varlığına bağımlıdır zaman durumlarda geri dönebilirsiniz `false` gerekli bilgiler yoksa, değerlendirme bağlamında henüz. Bu durumda, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu Yetkilendirme İlkeleri en az biri değerlendirme bağlamı değiştirilirse gelen ileti için oluşturulan tüm diğer yetkilendirme ilkeleri değerlendirdikten sonra yöntemi çağırır.  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
  
 [İzlenecek yol: Özel istemci ve hizmet kimlik bilgilerini oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md) özel kimlik bilgileri ve özel bir güvenlik belirteci yöneticisi nasıl oluşturulacağını açıklar. Oluşturulan özel güvenlik belirteci kimlik doğrulayıcı kullanmak için burada, güvenlik belirteci Yöneticisi uygulaması özel doğrulayıcıdan döndürecek şekilde değiştirilir <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> yöntemi. Yöntem uygun güvenlik belirteci gereksinimi geçirilen bir kimlik doğrulayıcı döndürür.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Özel güvenlik belirteci kimlik doğrulayıcı özel güvenlik belirteci yöneticisi ile tümleştirmek için  
  
1.  Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> özel güvenlik belirteci yöneticisi uygulamanızda yöntemi.  
  
2.  Temel, özel güvenlik belirteci kimlik doğrulayıcı döndürülecek etkinleştirmek için yöntemi mantık eklemek <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametresi. Belirteç gereksinimlerini belirteç türü bir kullanıcı adı aşağıdaki örnekte bir özel güvenlik belirteci kimlik doğrulayıcı döndürür (tarafından temsil edilen <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> özelliği) ve kendisi için güvenlik belirteci kimlik doğrulayıcı isteniyor ileti yönü giriş () tarafından temsil edilen <xref:System.ServiceModel.Description.MessageDirection.Input> alan).  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>  
 [İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Güvenlik mimarisi](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
