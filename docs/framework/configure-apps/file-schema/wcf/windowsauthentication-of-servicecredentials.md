---
title: "&lt;serviceCredentials&gt; için &lt;windowsAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b6043b35ea9dbed1e1e6e170035436038334b34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a>&lt;serviceCredentials&gt; için &lt;windowsAuthentication&gt;
Bir Windows hizmeti kimlik bilgileri ayarlarını belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceCredentials >  
\<windowsAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`includeWindowsGroups`|Sistem güvenlik bağlamında Windows grupları içerip içermeyeceğini belirten isteğe bağlı Boole öznitelik. Varsayılan, `true` değeridir.<br /><br /> Bu öznitelik ayarını `true` bir tam Grup genişletme sonuçları gibi bir performans etkisi olur. Bu öznitelik ayarlanırsa `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcının ait olduğu.|  
|`allowAnonymousLogons`|Anonim, kimliği doğrulanmamış arayanlara izin verilip verilmeyeceğini belirten isteğe bağlı Boole özniteliği. Varsayılan, `false` değeridir.<br /><br /> Zaman `clientCredentialType` özniteliği bağlaması `Windows`, sistem anonim arayanlara izin vermiyor. Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış gelir arayanlar sisteme erişmesine izin verilir. Bu öznitelik kullanarak bu davranışı geçersiz kılabilirsiniz.<br /><br /> Bu ayar çok dikkatli kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Anonim Windows kullanıcıları ayarlayarak erişimine izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanın `allowAnonymousLogons` özniteliği. Ayrıca kullanıcıların ait olduğu grubu bilgilerini ayarlayarak yetkilendirme bağlamı içinde dahil edilip edilmeyeceğini belirtebilirsiniz `includeWindowsGroups` özniteliği. Bu ayarlanırsa `true` (varsayılan ayar), hizmet istemcinin ait olduğu Windows gruplarını belirleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
