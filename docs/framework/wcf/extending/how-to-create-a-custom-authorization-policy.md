---
title: 'Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 5d5268cd2171bdccc3885cd599fdc8c277e61aa4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795704"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma
Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, talep tabanlı bir yetkilendirme modelini destekler. Talepler belirteçlerden ayıklanır, isteğe bağlı olarak özel yetkilendirme ilkesi tarafından işlenir ve ardından, yetkilendirme kararları <xref:System.IdentityModel.Policy.AuthorizationContext> almak için incelenebilir bir öğesine yerleştirildi. Özel bir ilke, gelen belirteçlerdeki talepleri uygulama tarafından beklenen talebe dönüştürmek için kullanılabilir. Bu şekilde, uygulama katmanı, WCF 'nin desteklediği farklı belirteç türleri tarafından sunulan farklı talepler hakkında ayrıntılardan ayrı olabilir. Bu konu, özel bir yetkilendirme ilkesinin nasıl uygulanacağını ve bu ilkenin bir hizmet tarafından kullanılan ilkeler koleksiyonuna nasıl ekleneceğini gösterir.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Özel bir yetkilendirme ilkesi uygulamak için  
  
1. Öğesinden <xref:System.IdentityModel.Policy.IAuthorizationPolicy>türetilen yeni bir sınıf tanımlayın.  
  
2. Sınıf için oluşturucuda benzersiz bir <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> dize oluşturup salt okunurdur ve özelliğe her erişildiğinde bu dizeyi döndürür.  
  
3. İlke vereni temsil eden bir <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> <xref:System.IdentityModel.Claims.ClaimSet> döndüren salt okunurdur özelliğini uygulayın. Bu, uygulamayı veya `ClaimSet` yerleşik `ClaimSet` bir özelliği `ClaimSet` (örneğin, statik <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özellik tarafından döndürülen) temsil eden bir olabilir.  
  
4. <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> Yöntemini aşağıdaki yordamda açıklandığı gibi uygulayın.  
  
### <a name="to-implement-the-evaluate-method"></a>Değerlendir metodunu uygulamak için  
  
1. Bu yönteme iki parametre geçirilir: <xref:System.IdentityModel.Policy.EvaluationContext> sınıfın bir örneği ve bir nesne başvurusu.  
  
2. Özel yetkilendirme <xref:System.IdentityModel.Claims.ClaimSet> ilkesi, <xref:System.IdentityModel.Policy.EvaluationContext>öğesinin geçerli içeriğiyle ilgili olmayan örnekler eklerse, <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemini çağırarak ve <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yönteminden geri dönerek `true` her `ClaimSet` birini ekleyin. Döndürme `true` , yetkilendirme ilkesinin işini gerçekleştirdiği yetkilendirme altyapısına ve yeniden çağrılması gerekmediğini gösterir.  
  
3. Özel yetkilendirme ilkesi yalnızca içinde `EvaluationContext`belirli talepler zaten mevcutsa talep kümelerini eklerse, <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> özelliği tarafından döndürülen `ClaimSet` örnekleri inceleyerek bu talepler için arama yapın. Talepler varsa, <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemini çağırarak yeni talep kümelerini ekleyin ve daha fazla talep kümesi eklenmek için, geri dönüş `true`, yetkilendirme ilkesinin işini tamamladığı yetkilendirme altyapısını gösterir. Talepler yoksa, diğer yetkilendirme ilkeleri `false` `EvaluationContext`öğesine daha fazla talep kümesi ekse, yetkilendirme ilkesinin tekrar çağrılması gerektiğini belirten döndürün.  
  
4. Daha karmaşık işleme senaryolarında, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemin ikinci parametresi, belirli bir değerlendirme için <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yönteme yapılan her bir çağrı sırasında yetkilendirme altyapısının geri geçidizin olacağı bir durum değişkenini depolamak için kullanılır.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Yapılandırma yoluyla özel bir yetkilendirme ilkesi belirtmek için  
  
1. Öğe içindeki öğesindeki öğesinde `policyType` bulunan özniteliğinde `add` `authorizationPolicies` `serviceAuthorization` özel yetkilendirme ilkesi türünü belirtin.  
  
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
  
1. ' A <xref:System.Collections.Generic.List%601> <xref:System.IdentityModel.Policy.IAuthorizationPolicy>oluşturun.  
  
2. Özel yetkilendirme ilkesinin bir örneğini oluşturun.  
  
3. Yetkilendirme ilkesi örneğini listeye ekleyin.  
  
4. Her özel yetkilendirme ilkesi için adım 2 ve 3 ' ü yineleyin.  
  
5. Özelliğe, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> listenin salt okunurdur bir sürümünü atayın.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm <xref:System.IdentityModel.Policy.IAuthorizationPolicy> bir uygulamayı göstermektedir.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Nasıl yapılır: Talepleri Karşılaştır](how-to-compare-claims.md)
- [Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Yetkilendirme İlkesi](../samples/authorization-policy.md)
