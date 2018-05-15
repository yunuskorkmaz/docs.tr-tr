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
manager: markl
ms.openlocfilehash: 7801c55cf6b3334347788013d9052038d5d2f3ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="8a640-102">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="8a640-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="8a640-103">Dijital imzalar, başka bir programda gönderildiğinde, veri değiştirilmiş değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="8a640-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="8a640-104">Genellikle dijital imza imzalanacak veri karmasını matematiksel işlevi uygulayarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="8a640-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="8a640-105">İmzalanması için bir karma değer biçimlendirme sırasında bazı dijital imza algoritmaları biçimlendirme işleminin bir parçası olarak ASN.1 nesne tanımlayıcısı (OID) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8a640-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="8a640-106">OID karma hesaplamak için kullanılan algoritmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8a640-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="8a640-107">Özel algoritmaları kullanmak için şifreleme mekanizması genişletmek için nesne tanımlayıcıları algoritmaları eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a640-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="8a640-108">Aşağıdaki örnek, bir nesne tanımlayıcı yeni bir karma algoritma eşleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8a640-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="8a640-109">[ \<OidEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) iki öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8a640-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="8a640-110">**OID** nesne tanımlayıcı numarası bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="8a640-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="8a640-111">**Adı** özniteliktir değerini **adı** özniteliğini [ \<nameEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="8a640-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="8a640-112">Basit bir ad eşlenebilir. bir nesne tanımlayıcı önce eşlemesinden bir algoritma adı için bir sınıf olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a640-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a640-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a640-113">See Also</span></span>  
 [<span data-ttu-id="8a640-114">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8a640-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="8a640-115">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="8a640-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
