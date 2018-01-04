---
title: "&lt;oidEntry&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2d6dfe38f8e632a31f7a20191678f1fff7fd88ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltoidentrygt-element"></a>&lt;oidEntry&gt; öğesi
ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.  
  
 \<Yapılandırma >  
\<mscorlib >  
\<cryptographySettings >  
\<oidMap >  
\<oidEntry >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**OID**|Gerekli öznitelik.<br /><br /> Sınıfı tarafından uygulanan algoritması karşılık gelen ASN.1 OID belirtir.|  
|**adı**|Gerekli öznitelik.<br /><br /> Değerini belirtir **adı** özniteliğini [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) etiketi.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`cryptographySettings`|Şifreleme ayarlarını içerir.|  
|`mscorlib`|İçeren `cryptographySettings` öğesi.|  
|`oidMap`|ASN.1 nesne tanımlayıcısı (OID) eşlemeleri sınıflar içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 ASN.1 nesne tanımlayıcılarını şifreleme bazı biçimlerde algoritmaları tanımlayın. Nesne tanımlayıcıları tanımlamak istediğiniz algoritmalar için kolay adlar eşleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<oidEntry >** Bu karma algoritmayı uygulaması için bir nesne tanımlayıcı RIPEMD 160 karma algoritması için eşlemek için öğesi.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Şifreleme Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Şifreleme Hizmetleri](../../../../../docs/standard/security/cryptographic-services.md)  
 [Şifreleme Sınıflarını Yapılandırma](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
