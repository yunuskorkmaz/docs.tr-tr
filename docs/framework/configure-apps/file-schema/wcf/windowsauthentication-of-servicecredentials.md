---
title: <windowsAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: bda375959b535ce5f2996d594f719893164b0bd4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195005"
---
# <a name="windowsauthentication-of-servicecredentials"></a>\<windowsAuthentication> / \<serviceCredentials>

Bir Windows hizmeti kimlik bilgisinin ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`includeWindowsGroups`|Sistemin güvenlik bağlamındaki Windows gruplarını içerip içermediğini belirten isteğe bağlı bir Boolean özniteliği. Varsayılan değer: `true`.<br /><br /> Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir. `false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.|  
|`allowAnonymousLogons`|Anonim, kimliği doğrulanmamış çağıranlara izin verilip verilmeyeceğini belirten isteğe bağlı bir Boolean özniteliği. Varsayılan değer: `false`.<br /><br /> `clientCredentialType`Bir bağlamanın özniteliği olarak ayarlandığında `Windows` , sistem anonim arayanlara izin vermez. Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış çağıranların sisteme erişimine izin verildiği anlamına gelir. Bu davranışı, bu özniteliği kullanarak geçersiz kılabilirsiniz.<br /><br /> Bu ayarı, çok dikkatli bir şekilde kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Özniteliğini ayarlayarak anonim Windows kullanıcılarına erişime izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanın `allowAnonymousLogons` . Ayrıca, özniteliğini ayarlayarak kullanıcıların AuthorizationContext 'e ait olduğu grup bilgilerinin eklenip eklenmeyeceğini belirtebilirsiniz `includeWindowsGroups` . `true`(Varsayılan ayar) olarak ayarlandıysa, hizmet istemcinin ait olduğu Windows gruplarını belirleyebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
