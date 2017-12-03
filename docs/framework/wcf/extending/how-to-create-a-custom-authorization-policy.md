---
title: "Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma"
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
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0086dc0c82fefad3cb1e5a73ddd9ced909f05453
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma
Kimlik modeli altyapısında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] talep tabanlı yetkilendirme modelini destekler. Talep belirteçlerinden ayıklanan, isteğe bağlı olarak özel yetkilendirme ilkesi tarafından işlenen ve içine yerleştirilen bir <xref:System.IdentityModel.Policy.AuthorizationContext> , sonra incelenmesi yetkilendirme kararları vermek için. Özel bir ilke, uygulama tarafından beklenen talep gelen belirteçleri talepleri dönüştürmek için kullanılabilir. Bu şekilde, uygulama katmanı tarafından sunulan farklı taleplerdeki ayrıntıları yalıtılmış farklı belirteç türleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekler. Bu konu, özel yetkilendirme ilkesi uygulama ve hizmet tarafından kullanılan ilkeleri koleksiyonunu o ilke eklemek nasıl gösterir.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Özel yetkilendirme ilkesi uygulamak için  
  
1.  Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Salt okunur uygulamak <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> özelliği erişildiğinde sınıfa ilişkin oluşturucuda benzersiz bir dize oluşturma ve bu dizeyi özelliği.  
  
3.  Salt okunur uygulamak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> döndürerek özelliği bir <xref:System.IdentityModel.Claims.ClaimSet> İlkesi veren temsil eden. Bunun bir `ClaimSet` uygulama veya yerleşik bir temsil eden `ClaimSet` (örneğin, `ClaimSet` statik tarafından döndürülen <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özelliği.  
  
4.  Uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> aşağıdaki yordamda açıklandığı gibi yöntemi.  
  
### <a name="to-implement-the-evaluate-method"></a>Evaluate yöntemi uygulamak için  
  
1.  İki parametre bu yönteme geçirilen: örneği <xref:System.IdentityModel.Policy.EvaluationContext> sınıf ve nesne başvurusu.  
  
2.  Özel yetkilendirme ilkesi eklerse <xref:System.IdentityModel.Claims.ClaimSet> geçerli içeriğini dikkate almaksızın örnekleri <xref:System.IdentityModel.Policy.EvaluationContext>, her ekleyin `ClaimSet` çağırarak <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemi ve return `true` gelen <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yöntemi. Döndürme `true` yetkilendirme altyapı yetkilendirme ilkesi çalışmasını yürüttü ve yeniden çağrılması gerekmez gösterir.  
  
3.  Yalnızca belirli talepler zaten varsa özel yetkilendirme ilkesi talep kümelerinin eklerse `EvaluationContext`, sonra bu talepleri için inceleyerek bakın `ClaimSet` tarafından döndürülen örnek <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> özelliği. Talep varsa, ardından yeni talep ayarlar çağırarak ekleyin <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemi ve kümeleridir eklenen, dönüş olması için daha fazla talep IF `true`, yetkilendirme ilkesini kendi çalışması tamamlandı yetkilendirme altyapısına belirten. Talep mevcut değilse, dönüş `false`, diğer yetkilendirme ilkeleri daha eklerseniz, Yetkilendirme İlkesi'nin yeniden adlandırılması gerektiğini belirten talep kümeleri için `EvaluationContext`.  
  
4.  Daha karmaşık işleme senaryolarında, ikinci parametresi, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi yetkilendirme altyapı geri her sonraki çağrı sırasında geçecek bir durum değişkeninin depolamak için kullanılan <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> belirli bir değerlendirme yöntemi.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Özel yetkilendirme ilkesini yapılandırma yoluyla belirtmek için  
  
1.  Özel yetkilendirme ilkesi türünü belirtin `policyType` özniteliğini `add` öğesinde `authorizationPolicies` öğesinde `serviceAuthorization` öğesi.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>         
            <add policyType="Samples.MyAuthorizationPolicy"  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Özel yetkilendirme ilkesi kodlarda belirtmek için  
  
1.  Oluşturma bir <xref:System.Collections.Generic.List%601> , <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Özel yetkilendirme ilkesi örneği oluşturun.  
  
3.  Yetkilendirme ilkesi örneği listesine ekleyin.  
  
4.  Her özel yetkilendirme ilkesi için 2 ve 3. adımları yineleyin.  
  
5.  Listeye salt okunur bir sürümünü atamak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> özelliği.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek eksiksiz gösterir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulaması.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Nasıl yapılır: Beyanları](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [Nasıl yapılır: bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Yetkilendirme İlkesi](../../../../docs/framework/wcf/samples/authorization-policy.md)
