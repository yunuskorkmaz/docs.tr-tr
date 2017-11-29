---
title: "&lt;serviceAuthorization&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cdbe676fa73c040737c947902d64b2c0e689e2a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltserviceauthorizationgt-element"></a>&lt;serviceAuthorization&gt; öğesi
Hizmet işlemlerine erişimi yetkilendirme ayarlarını belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceAuthorization >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceAuthorization  
     impersonateCallerForAllOperations="Boolean"  
      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"  
      roleProviderName="String"  
      serviceAuthorizationManagerType="String" />  
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
|impersonateCallerForAllOperations|Hizmetindeki tüm işlemleri çağıran kimliğine bürünmek olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Belirli bir hizmet işlemine arayan taklit ettiğinde, iş parçacığı içeriği belirtilen hizmet yürütmeden önce çağıran bağlamına anahtarlanır.|  
|principalPermissionMode|Sunucu üzerinde işlemler gerçekleştirmek için kullanılan sorumluyu ayarlar. Değerler aşağıdakileri içerir:<br /><br /> -Yok<br />-UseWindowsGroups<br />-UseAspNetRoles<br />-Özel<br /><br /> UseWindowsGroups varsayılan değerdir. Değer <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Bu öznitelik kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtla](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Bir Windows Communication Foundation (WCF) uygulaması için rol bilgileri sağlayan rol sağlayıcısı adını belirten dize. Varsayılan boş bir dizedir.|  
|ServiceAuthorizationManagerType|Hizmet Yetkilendirme Yöneticisi'ni türünü içeren bir dize. Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|authorizationPolicies|Kullanılarak eklenebilir yetkilendirme ilkesi türleri koleksiyonunu içeren `add` anahtar sözcüğü. Her bir yetkilendirme ilkesi gereken tek bir içeren `policyType` bir dize özniteliği. Öznitelik, bir giriş talep kümesini bir dönüştürme talep başka bir dizi içine sağlayan bir yetkilendirme ilkesi belirtir. Erişim denetimi verilen veya reddedilen oturum tabanlı. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir hizmet davranışını için ayarlar koleksiyonu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölümde, yetkilendirme, özel rol sağlayıcıları ve kimliğe bürünme etkileyen öğeleri içerir.  
  
 `principalPermissionMode` Özniteliği, korumalı bir yöntemin kullanılması, yetkilendirirken kullanmak için kullanıcı gruplarını belirtir. Varsayılan değer `UseWindowsGroups` ve "Yöneticiler" veya "Kullanıcı" gibi Windows grupları için bir kaynağa erişmeye çalışırken bir kimlik aranır belirtir. Ayrıca belirtebilirsiniz `UseAspNetRoles` altında yapılandırılmış bir özel rol sağlayıcıyı kullanacak şekilde \<system.web > aşağıdaki kodda gösterildiği gibi öğesi.  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
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
  <!-- Other configuration code not shown.-->  
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
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Hizmet işlemlerine erişimi yetkilendirme](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Nasıl yapılır: bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Yetkilendirme İlkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md)
