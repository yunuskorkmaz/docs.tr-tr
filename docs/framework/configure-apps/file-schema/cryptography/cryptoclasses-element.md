---
title: '&lt;cryptoClasses&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 85e47830649b0088d1e1645d73c4fb924ba5591f
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083333"
---
# <a name="ltcryptoclassesgt-element"></a>&lt;cryptoClasses&gt; öğesi
Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) öğesi.  
  
 \<Yapılandırma >  
\<mscorlib >  
\<cryptographySettings >  
\<cryptoNameMapping >  
\<cryptoClasses >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|İçin bir kolay ad eşlemesi var. bir şifreleme sınıfına içeren  **\<nameEntry >** öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`cryptographySettings`|Şifreleme ayarlarını içerir.|  
|`cryptoNameMapping`|Sınıf için kolay adlar eşlemeleri içerir.|  
|`mscorlib`|İçeren `cryptographySettings` öğesi.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanıldığını gösterir  **\<cryptoClass >** bir şifreleme sınıfına başvurmak için ve çalışma zamanı yapılandırma öğesi. Ardından "RSA" dize iletebileceğiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemini <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesne.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Security.Cryptography>
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Şifreleme Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [Şifreleme Hizmetleri](../../../../../docs/standard/security/cryptographic-services.md)
- [System.Security.Cryptography.CryptoConfig.CreateFromName](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [Şifreleme Sınıflarını Yapılandırma](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
