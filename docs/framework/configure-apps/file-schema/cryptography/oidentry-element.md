---
title: '&lt;oidEntry&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 7c5309bc98a7781e82753869b1cf2bcf0a472327
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084100"
---
# <a name="ltoidentrygt-element"></a>&lt;oidEntry&gt; öğesi
ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.  
  
 \<Yapılandırma >  
\<mscorlib >  
\<cryptographySettings >  
\<oidMap>  
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
|**OID**|Gerekli öznitelik.<br /><br /> Sınıfınız tarafından uygulanan algoritması karşılık gelen ASN.1 OID belirtir.|  
|**Adı**|Gerekli öznitelik.<br /><br /> Değeri belirtir **adı** özniteliğini [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) etiketi.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`cryptographySettings`|Şifreleme ayarlarını içerir.|  
|`mscorlib`|İçeren `cryptographySettings` öğesi.|  
|`oidMap`|ASN.1 nesne tanımlayıcısını (OID) eşlemeleri için sınıflar içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 ASN.1 nesne tanımlayıcılarını şifreleme bazı biçimlerde algoritmaları tanımlar. Nesne tanımlayıcılarını tanımlamak istediğiniz algoritmalar için kolay adlar eşleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<oidEntry >** RIPEMD 160 karma algoritması için nesne tanımlayıcısı bu karma algoritmayı uygulaması için eşlemek için öğesi.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Şifreleme Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [Şifreleme Hizmetleri](../../../../../docs/standard/security/cryptographic-services.md)
- [Şifreleme Sınıflarını Yapılandırma](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
