---
title: 'Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 78cc77a5491e50d718a53efff1c6f99acf23cf27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115394"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Nasıl yapılır: Özel Yetkilendirme İlkesi Oluşturma
Windows Communication Foundation (WCF) kimlik modeli altyapısı, bir talep tabanlı yetkilendirme modelini destekler. Talep belirteçleri ayıklanan, isteğe bağlı olarak özel yetkilendirme ilkesi tarafından işlenen ve ardından yerleştirilip bir <xref:System.IdentityModel.Policy.AuthorizationContext> , ardından incelenebilir yetkilendirme kararları vermek için. Özel bir ilke, uygulama tarafından beklenen talep gelen belirteçleri gelen talepleri dönüştürmek için kullanılabilir. Bu şekilde, uygulama katmanı WCF desteklediği farklı belirteç türleri tarafından sunulan farklı talepleri ayrıntılarından yalıtılmış. Bu konuda, bir hizmet tarafından kullanılan ilkeleri koleksiyonunu Bu ilkeyi ekleme ve özel yetkilendirme ilkesi uygulamak nasıl gösterir.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Özel yetkilendirme ilkesi uygulamak için  
  
1.  Öğesinden türetilen yeni bir sınıf tanımlama <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Salt okunur uygulamak <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> özelliği erişildiğinde sınıf için oluşturucu içinde benzersiz bir dize oluşturma ve bu dize özelliği.  
  
3.  Salt okunur uygulamak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> döndürerek özelliği bir <xref:System.IdentityModel.Claims.ClaimSet> ilke veren temsil eden. Bunun bir `ClaimSet` temsil eden bir uygulama veya yerleşik bir `ClaimSet` (örneğin, `ClaimSet` özelliğinden döndürülen statik <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özelliği.  
  
4.  Uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> aşağıdaki yordamda açıklandığı şekilde yöntemi.  
  
### <a name="to-implement-the-evaluate-method"></a>Evaluate yöntemi uygulamak için  
  
1.  İki parametre, bu yönteme geçirilir: örneği <xref:System.IdentityModel.Policy.EvaluationContext> sınıfı ve bir nesne başvurusu.  
  
2.  Özel yetkilendirme ilkesi eklerse <xref:System.IdentityModel.Claims.ClaimSet> örnekleri geçerli içeriğini bakılmaksızın <xref:System.IdentityModel.Policy.EvaluationContext>, her ekleme `ClaimSet` çağırarak <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemi ve dönüş `true` gelen <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yöntemi. Döndüren `true` yetkilendirme ilkesi işini yürüttü ve yeniden çağrılması gerekmez yetkilendirme altyapısında gösterir.  
  
3.  Yalnızca belirli talep zaten varsa, özel yetkilendirme ilkesi talep kümelerinin eklerse, `EvaluationContext`, sonra bu talepleri için inceleyerek bakın `ClaimSet` tarafından döndürülen örnek <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> özelliği. Talep mevcut olması durumunda, ardından yeni bir talep ayarlar çağırarak ekleyin <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> yöntemi ve artık kümeleridir eklendi, iade edilecek talep if `true`yetkilendirme ilkesi çalışmasını tamamlamadan yetkilendirme altyapısına gösteren. Talep mevcut değilse, dönüş `false`, talep kümeleri için daha fazla diğer yetkilendirme ilkeleri eklerseniz, Yetkilendirme İlkesi'nin yeniden adlandırılması gerektiğini belirten `EvaluationContext`.  
  
4.  Daha karmaşık işleme senaryolarda, ikinci parametresinin <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi yetkilendirme altyapı geri her sonraki çağrı sırasında geçer bir durum değişkeninin depolamak için kullanılan <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> belirli bir değerlendirme için yöntemi.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Özel yetkilendirme ilkesi yapılandırma yoluyla belirtmek için  
  
1.  İçinde özel yetkilendirme ilkesi türünü belirtin `policyType` özniteliğini `add` öğesinde `authorizationPolicies` öğesinde `serviceAuthorization` öğesi.  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Özel yetkilendirme ilkesi kod aracılığıyla belirtmek için  
  
1.  Oluşturma bir <xref:System.Collections.Generic.List%601> , <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Özel yetkilendirme ilkesi örneği oluşturun.  
  
3.  Yetkilendirme ilkesi örneği listesine ekleyin.  
  
4.  Her bir özel yetkilendirme ilkesi için 2 ve 3. adımları tekrarlayın.  
  
5.  Listeye salt okunur bir sürümünü atamak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> özelliği.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir tam gösterir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulaması.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Nasıl yapılır: Talepleri Karşılaştırma](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Yetkilendirme İlkesi](../../../../docs/framework/wcf/samples/authorization-policy.md)
