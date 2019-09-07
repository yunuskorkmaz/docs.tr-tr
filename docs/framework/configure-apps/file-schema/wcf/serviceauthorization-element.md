---
title: <serviceAuthorization> öğesi
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: b636b7006900ecff1be553cf32105df7cea7e800
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399700"
---
# <a name="serviceauthorization-element"></a>\<serviceAuthorization > öğesi
Hizmet işlemlerine erişim yetkisi veren ayarları belirtir  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceAuthorization >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|ImpersonateCallerForAllOperations|Hizmette tüm işlemlerin çağıranın kimliğine bürünmesini belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Belirli bir hizmet işlemi çağıranı taklit ettiğinde, belirtilen hizmeti yürütmeden önce iş parçacığı bağlamı arayan bağlamına geçiş yapılır.|  
|principalPermissionMode|Sunucuda işlemleri yürütmek için kullanılan sorumluyu ayarlar. Değerler şunlardır:<br /><br /> -Hiçbiri<br />-UseWindowsGroups<br />-UseAspNetRoles<br />-Özel<br /><br /> Varsayılan değer UseWindowsGroups değeridir. Değer, türündedir <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Bu özniteliği kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: PrincipalPermissionAttribute sınıfıyla](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)erişimi kısıtlayın.|  
|roleProviderName|Bir Windows Communication Foundation (WCF) uygulaması için rol bilgileri sağlayan rol sağlayıcısının adını belirten bir dize. Varsayılan değer boş bir dizedir.|  
|ServiceAuthorizationManagerType|Hizmet Yetkilendirme Yöneticisi türünü içeren bir dize. Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|authorizationPolicies|`add` Anahtar sözcüğü kullanılarak eklenebilen bir yetkilendirme ilkesi türü koleksiyonu içerir. Her yetkilendirme ilkesi, bir dize olan `policyType` tek bir gerekli özniteliği içerir. Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir. Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir hizmetin davranışı için ayarların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölüm yetkilendirme, özel rol sağlayıcıları ve kimliğe bürünme işlemlerini etkileyen öğeleri içerir.  
  
 Özniteliği `principalPermissionMode` , korumalı bir yöntemin kullanımını yetkilendirirken kullanılacak kullanıcı gruplarını belirtir. Varsayılan değer ' dir `UseWindowsGroups` ve bir kaynağa erişmeye çalışan bir kimlik için "Yöneticiler" veya "kullanıcılar" gibi Windows gruplarının arandığını belirtir. Ayrıca, aşağıdaki kodda `UseAspNetRoles` gösterildiği gibi, \<System. Web > öğesi altında yapılandırılmış özel bir rol sağlayıcısı kullanmayı da belirtebilirsiniz.  
  
```xml  
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```  
  
 Aşağıdaki kod, `principalPermissionMode` özniteliğiyle birlikte `roleProviderName` kullanılan öğesini gösterir.  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 Bu yapılandırma öğesinin kullanımına ilişkin ayrıntılı bir örnek için bkz. [hizmet işlemlerine](../../../wcf/samples/authorizing-access-to-service-operations.md) ve [Yetkilendirme ilkesine](../../../wcf/samples/authorization-policy.md)erişimi yetkilendirme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Hizmet İşlemlerine Erişimi Yetkilendirme](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md)
