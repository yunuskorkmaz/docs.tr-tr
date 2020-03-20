---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152794"
---
# <a name="certificatevalidator"></a>\<sertifikaValidator>
Sertifika doğrulama için özel bir tür belirtir. Bu tür, yalnızca `certificateValidationMode` [ \<sertifika Doğrulama>](certificatevalidation.md) öğesinin özniteliği "Özel" olarak ayarlanırsa kullanılır.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sertifikaDoğrulama>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sertifikaValidator>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|type|<xref:System.IdentityModel.Selectors.X509CertificateValidator> Sınıftan türeyen özel bir tür belirtir. Bu tür kullanmak için [ \<sertifika Doğrulama>](certificatevalidation.md) öğesinin özniteliğini "Özel" olarak ayarlayın. `certificateValidationMode` Öznitelik nasıl belirtilir `type` hakkında daha fazla bilgi için bkz. [Custom Type References](../windows-workflow-foundation/index.md) İsteğe bağlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 None  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<sertifikaDoğrulama>](certificatevalidation.md)|Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.|  
  
## <a name="example"></a>Örnek  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
