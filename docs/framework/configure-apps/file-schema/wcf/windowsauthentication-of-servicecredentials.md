---
title: '&lt;serviceCredentials&gt; için &lt;windowsAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 3077baf49c13c91c6293823aa841525bf07ca7f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616270"
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a>&lt;serviceCredentials&gt; için &lt;windowsAuthentication&gt;
Bir Windows hizmeti kimlik bilgisi ayarlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<ServiceCredentials >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`includeWindowsGroups`|Sistemin Windows gruplarını güvenlik bağlamına dahil olup olmadığını belirten isteğe bağlı bir Boolean özniteliği. Varsayılan, `true` değeridir.<br /><br /> Bu öznitelik ayarını `true` tam Grup genişletme içinde sonuçları gibi bir performans etkisi vardır. Bu öznitelik ayarlanan `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcıya ait.|  
|`allowAnonymousLogons`|Anonim, kimliği doğrulanmamış çağıranlara izin verilip verilmeyeceğini belirten isteğe bağlı bir Boolean özniteliği. Varsayılan, `false` değeridir.<br /><br /> Zaman `clientCredentialType` bağlama özniteliği `Windows`, sistem anonim bir çağırıcıya izin vermeyen. Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış anlamına gelir çağıranlar sisteme erişmek için izin verilir. Bu özniteliği kullanarak bu davranışı geçersiz kılabilirsiniz.<br /><br /> Bu ayarı dikkatli kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet ve istemci kimlik doğrulama ile ilgili ayarlarda kullanılan kimlik bilgisini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows kullanıcıları anonim erişim ayarlayarak izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanırsınız `allowAnonymousLogons` özniteliği. Ayrıca kullanıcıların ait olduğu grubu bilgileri ayarlayarak içinde AuthorizationContext eklenip eklenmeyeceğini belirtebilirsiniz `includeWindowsGroups` özniteliği. Bu ayarlanırsa `true` (varsayılan ayar), hizmet istemcinin ait olduğu Windows grupları belirleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
