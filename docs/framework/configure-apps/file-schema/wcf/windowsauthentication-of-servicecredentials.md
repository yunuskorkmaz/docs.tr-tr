---
title: <windowsAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399107"
---
# <a name="windowsauthentication-of-servicecredentials"></a>\<\<ServiceCredentials > > WindowsAuthentication
Bir Windows hizmeti kimlik bilgisinin ayarlarını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsAuthentication >**  
  
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
|`includeWindowsGroups`|Sistemin güvenlik bağlamındaki Windows gruplarını içerip içermediğini belirten isteğe bağlı bir Boolean özniteliği. Varsayılan, `true` değeridir.<br /><br /> Bu özniteliğin olarak `true` ayarlanması, tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir. Bir kullanıcının ait olduğu `false` grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.|  
|`allowAnonymousLogons`|Anonim, kimliği doğrulanmamış çağıranlara izin verilip verilmeyeceğini belirten isteğe bağlı bir Boolean özniteliği. Varsayılan, `false` değeridir.<br /><br /> Bir bağlamanın `Windows`özniteliği olarak ayarlandığında, sistem anonim arayanlara izin vermez. `clientCredentialType` Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış çağıranların sisteme erişimine izin verildiği anlamına gelir. Bu davranışı, bu özniteliği kullanarak geçersiz kılabilirsiniz.<br /><br /> Bu ayarı, çok dikkatli bir şekilde kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `allowAnonymousLogons` Özniteliğini ayarlayarak anonim Windows kullanıcılarına erişime izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanın. Ayrıca, `includeWindowsGroups` özniteliğini ayarlayarak kullanıcıların AuthorizationContext 'e ait olduğu grup bilgilerinin eklenip eklenmeyeceğini belirtebilirsiniz. (Varsayılan ayar) olarak `true` ayarlandıysa, hizmet istemcinin ait olduğu Windows gruplarını belirleyebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
