---
title: Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d23fc48a53ee47aacfc290b52887b800ce37477f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232813"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme
Dijital imzalar, başka bir programdan gönderildiğinde, veri ile müdahaleye uğramadığından emin olun. Genellikle verilerin imzalanmasını karma bir matematiksel işlev uygulayarak dijital imza hesaplanır. İmzalanacak bir karma değer biçimlendirilirken, biçimlendirme işleminin bir parçası olarak ASN.1 nesne tanımlayıcısı (OID) bazı dijital imza algoritmaları ekleyin. OID, karma değeri hesaplamak için kullanılan algoritmayı belirtir. Özel algoritmalar kullanmak için şifreleme mekanizması genişletmek için nesne tanımlayıcılarını algoritmaları eşleyebilirsiniz. Aşağıdaki örnek, bir nesne tanımlayıcı eşlemek için yeni bir karma algoritması gösterilmektedir.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [ \<OidEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) iki öznitelik içeriyor. **OID** nesne tanımlayıcı numarası bir özniteliktir. **Adı** değeri özniteliktir **adı** özniteliğini [ \<nameEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md). Bir nesne tanımlayıcı basit adına eşlenebilir önce bir algoritma adının bir eşleme bir sınıf olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme Sınıflarını Yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
