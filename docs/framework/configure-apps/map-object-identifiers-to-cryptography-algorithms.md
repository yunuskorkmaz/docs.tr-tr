---
title: "Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: dbfe394193925e38dad774d39d79ac813abef22a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme
Dijital imzalar, başka bir programda gönderildiğinde, veri değiştirilmiş değil emin olun. Genellikle dijital imza imzalanacak veri karmasını matematiksel işlevi uygulayarak hesaplanır. İmzalanması için bir karma değer biçimlendirme sırasında bazı dijital imza algoritmaları biçimlendirme işleminin bir parçası olarak ASN.1 nesne tanımlayıcısı (OID) ekleyin. OID karma hesaplamak için kullanılan algoritmayı tanımlar. Özel algoritmaları kullanmak için şifreleme mekanizması genişletmek için nesne tanımlayıcıları algoritmaları eşleyebilirsiniz. Aşağıdaki örnek, bir nesne tanımlayıcı yeni bir karma algoritma eşleme gösterilmektedir.  
  
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
  
 [ \<OidEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) iki öznitelikleri içerir. **OID** nesne tanımlayıcı numarası bir özniteliktir. **Adı** özniteliktir değerini **adı** özniteliğini [ \<nameEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md). Basit bir ad eşlenebilir. bir nesne tanımlayıcı önce eşlemesinden bir algoritma adı için bir sınıf olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme sınıflarını yapılandırma](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
