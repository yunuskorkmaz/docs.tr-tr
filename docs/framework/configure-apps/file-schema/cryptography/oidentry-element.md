---
title: <oidEntry> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088544"
---
# <a name="oidentry-element"></a>\<Oıdentry > öğesi
Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Cryptographyısettings >** ](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oıdmap >** ](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Oıdentry >**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**ID**|Gerekli öznitelik.<br /><br /> Sınıfınız tarafından uygulanan algoritmaya karşılık gelen ASN. 1 OID 'yi belirtir.|  
|**ada**|Gerekli öznitelik.<br /><br /> [\<nameEntry >](nameentry-element.md) etiketindeki **Name** özniteliğinin değerini belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`cryptographySettings`|Şifreleme ayarlarını içerir.|  
|`mscorlib`|`cryptographySettings` öğesini içerir.|  
|`oidMap`|Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 ASN. 1 nesne tanımlayıcıları bazı şifreleme biçimlerinde algoritmaları belirler. Tanımlamak istediğiniz algoritmaların nesne tanımlayıcılarını kolay adlarla eşleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, RIPEMD-160 karma algoritması için bir nesne tanımlayıcısını bu karma algoritmanın bir uygulamasına eşlemek için **\<Oıdentry >** öğesinin nasıl kullanılacağını gösterir.  
  
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

- [Yapılandırma Dosyası Şeması](../index.md)
- [Şifreleme Ayarları Şeması](index.md)
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)
- [Şifreleme Sınıflarını Yapılandırma](../../configure-cryptography-classes.md)
- [Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme](../../map-object-identifiers-to-cryptography-algorithms.md)
