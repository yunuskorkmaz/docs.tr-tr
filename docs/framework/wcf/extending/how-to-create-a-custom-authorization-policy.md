---
title: 'Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: fef7aa531c946ecacef30bb79f2362bad4d375ed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256033"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma

Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, talep tabanlı bir yetkilendirme modelini destekler. Talepler belirteçlerden ayıklanır, isteğe bağlı olarak özel yetkilendirme ilkesi tarafından işlenir ve ardından, <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları almak için incelenebilir bir öğesine yerleştirildi. Özel bir ilke, gelen belirteçlerdeki talepleri uygulama tarafından beklenen talebe dönüştürmek için kullanılabilir. Bu şekilde, uygulama katmanı, WCF 'nin desteklediği farklı belirteç türleri tarafından sunulan farklı talepler hakkında ayrıntılardan ayrı olabilir. Bu konu, özel bir yetkilendirme ilkesinin nasıl uygulanacağını ve bu ilkenin bir hizmet tarafından kullanılan ilkeler koleksiyonuna nasıl ekleneceğini gösterir.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Özel bir yetkilendirme ilkesi uygulamak için  
  
1. Öğesinden türetilen yeni bir sınıf tanımlayın <xref:System.IdentityModel.Policy.IAuthorizationPolicy> .  
  
2. <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A>Sınıf için oluşturucuda benzersiz bir dize oluşturup salt okunurdur ve özelliğe her erişildiğinde bu dizeyi döndürür.  
  
3. <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A>İlke vereni temsil eden bir döndüren salt okunurdur özelliğini uygulayın <xref:System.IdentityModel.Claims.ClaimSet> . Bu, `ClaimSet` uygulamayı veya yerleşik bir `ClaimSet` Özelliği (örneğin, `ClaimSet` statik özellik tarafından döndürülen) temsil eden bir olabilir <xref:System.IdentityModel.Claims.ClaimSet.System%2A> .  
  
4. <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>Yöntemini aşağıdaki yordamda açıklandığı gibi uygulayın.  
  
### <a name="to-implement-the-evaluate-method"></a>Değerlendir metodunu uygulamak için  
  
1. Bu yönteme iki parametre geçirilir: sınıfın bir örneği <xref:System.IdentityModel.Policy.EvaluationContext> ve bir nesne başvurusu.  
  
2. Özel yetkilendirme ilkesi <xref:System.IdentityModel.Claims.ClaimSet> , öğesinin geçerli içeriğiyle ilgili olmayan örnekler eklerse <xref:System.IdentityModel.Policy.EvaluationContext> , `ClaimSet` <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemini çağırarak ve yönteminden geri dönerek her birini ekleyin `true` <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> . Döndürme, yetkilendirme `true` ilkesinin işini gerçekleştirdiği yetkilendirme altyapısına ve yeniden çağrılması gerekmediğini gösterir.  
  
3. Özel yetkilendirme ilkesi yalnızca içinde belirli talepler zaten mevcutsa talep kümelerini eklerse `EvaluationContext` , `ClaimSet` özelliği tarafından döndürülen örnekleri inceleyerek bu talepler için arama yapın <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> . Talepler varsa, yöntemini çağırarak yeni talep kümelerini ekleyin <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> ve daha fazla talep kümesi eklenmek için, geri dönüş `true` , yetkilendirme ilkesinin işini tamamladığı yetkilendirme altyapısını gösterir. Talepler yoksa, `false` diğer yetkilendirme ilkeleri öğesine daha fazla talep kümesi ekse, yetkilendirme ilkesinin tekrar çağrılması gerektiğini belirten döndürün `EvaluationContext` .  
  
4. Daha karmaşık işleme senaryolarında, yöntemin ikinci parametresi, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> belirli bir değerlendirme için yönteme yapılan her bir çağrı sırasında yetkilendirme altyapısının geri geçidizin olacağı bir durum değişkenini depolamak için kullanılır.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Yapılandırma yoluyla özel bir yetkilendirme ilkesi belirtmek için  
  
1. Öğe içindeki öğesindeki öğesinde bulunan özniteliğinde özel yetkilendirme ilkesi türünü belirtin `policyType` `add` `authorizationPolicies` `serviceAuthorization` .  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Kodla özel bir yetkilendirme ilkesi belirtmek için  
  
1. ' A <xref:System.Collections.Generic.List%601> oluşturun <xref:System.IdentityModel.Policy.IAuthorizationPolicy> .  
  
2. Özel yetkilendirme ilkesinin bir örneğini oluşturun.  
  
3. Yetkilendirme ilkesi örneğini listeye ekleyin.  
  
4. Her özel yetkilendirme ilkesi için adım 2 ve 3 ' ü yineleyin.  
  
5. Özelliğe, listenin salt okunurdur bir sürümünü atayın <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> .  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, tüm bir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulamayı göstermektedir.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Nasıl yapılır: Talepleri Karşılaştırma](how-to-compare-claims.md)
- [Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Yetkilendirme İlkesi](../samples/authorization-policy.md)
