---
title: Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme
description: Bir XML yapılandırma dosyasındaki Oıdentry ve nameEntry öğelerini kullanarak bir nesne tanımlayıcısını (OID) .NET 'teki bir şifreleme algoritmasına eşleme konusuna bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e22510014071455b83ba28cd82690b5ecdce9bc9
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85142010"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme
Dijital imzalar, bir programdan diğerine gönderildiğinde verilerin üzerinde oynanmamasını sağlar. Genellikle dijital imza, imzalanacak verilerin karmasını matematiksel bir işlev uygulanarak hesaplanır. Bir karma değeri imzalanacak olarak biçimlendirirken, bazı dijital imza algoritmaları biçimlendirme işleminin bir parçası olarak bir ASN. 1 nesne tanımlayıcısı (OID) ekler. OID, karmayı hesaplamak için kullanılan algoritmayı tanımlar. Şifreleme mekanizmasını özel algoritmaları kullanmak üzere genişletmek için algoritmaları nesne tanımlayıcılarıyla eşleyebilirsiniz. Aşağıdaki örnek, bir nesne tanımlayıcısının yeni bir karma algoritmasına nasıl eşleneceğini gösterir.  
  
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
  
 [ \<oidEntry> Öğesi](./file-schema/cryptography/oidentry-element.md) iki öznitelik içerir. **OID** özniteliği, nesne tanımlayıcı numarasıdır. **Name** [ \<nameEntry> özniteliği, öğesinden](./file-schema/cryptography/nameentry-element.md) **ad** özniteliğinin değeridir. Bir nesne tanımlayıcısının basit bir ada eşleştirilemeden önce bir algoritma adından bir sınıfa eşleme olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Sınıflarını Yapılandırma](configure-cryptography-classes.md)
- [Şifreleme Hizmetleri](../../standard/security/cryptographic-services.md)
