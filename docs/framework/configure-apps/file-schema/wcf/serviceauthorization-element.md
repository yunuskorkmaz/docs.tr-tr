---
title: '&lt;serviceAuthorization&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: 6c69d10eb2f6cdf4546dd5895d196723417f5494
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146010"
---
# <a name="ltserviceauthorizationgt-element"></a>&lt;serviceAuthorization&gt; öğesi
Hizmet işlemleri erişim yetkisi ayarlarını belirtir  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceAuthorization >  
  
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
|ImpersonateCallerForAllOperations|Hizmetteki tüm işlemlerin çağıranın kimliğine bürünüp bürünmediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Belirli bir hizmet işlemine çağıranın kimliğine bürünür, iş parçacığı bağlamını, belirtilen hizmet yürütmeden önce çağıranın bağlamına anahtarlanır.|  
|PrincipalPermissionMode|Sunucu üzerinde işlem gerçekleştirmek için kullanılan asıl öğeleri ayarlar. Değerler aşağıdakileri içerir:<br /><br /> -Yok<br />-UseWindowsGroups<br />-UseAspNetRoles<br />-Özel<br /><br /> UseWindowsGroups varsayılan değerdir. Değer türünde <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Bu öznitelik kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Bir Windows Communication Foundation (WCF) uygulaması için rol bilgileri sağlayan rol sağlayıcısının adını belirten dize. Varsayılan değer boş bir dizedir.|  
|ServiceAuthorizationManagerType|Hizmet Yetkilendirme Yöneticisi türünü içeren bir dize. Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|authorizationPolicies|Hangi kullanılarak eklenebilen bir yetkilendirme ilkesi türü koleksiyonu içerir `add` anahtar sözcüğü. Gereken tek bir her yetkilendirme ilkesi içeren `policyType` dize özniteliği. Öznitelik, bir giriş talep kümesini talep başka bir dizi dönüşümünü sağlayan bir yetkilendirme ilkesi belirtir. Erişim denetimi verilen veya reddedilen oturum tabanlı. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|İçin bir hizmet davranışı ayar koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölümde, kimliğe bürünme yetkilendirme ve özel rol sağlayıcıları etkileyen öğeleri içerir.  
  
 `principalPermissionMode` Özniteliği, korumalı bir yöntem kullanımını yetkilendirirken kullanmak için kullanıcı gruplarını belirtir. Varsayılan değer `UseWindowsGroups` ve "Yöneticiler" veya "Kullanıcılar" gibi Windows gruplarını bir kaynağa erişmeye çalışırken bir kimlik için aranır belirtir. Ayrıca belirtebileceğiniz `UseAspNetRoles` altında yapılandırılmış bir özel rol sağlayıcıyı kullanacak şekilde \<system.web > öğesi, aşağıdaki kodda gösterildiği gibi.  
  
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
  
 Aşağıdaki kodda gösterildiği `roleProviderName` ile kullanılan `principalPermissionMode` özniteliği.  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 Bu yapılandırma öğesini kullanarak bir ayrıntılı örnek için bkz: [hizmet işlemlerine erişimi yetkilendirme](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) ve [yetkilendirme ilkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Hizmet İşlemlerine Erişimi Yetkilendirme](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Yetkilendirme İlkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md)
