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
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48263251"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="77261-102">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="77261-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="77261-103">Dijital imzalar, başka bir programdan gönderildiğinde, veri ile müdahaleye uğramadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="77261-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="77261-104">Genellikle verilerin imzalanmasını karma bir matematiksel işlev uygulayarak dijital imza hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="77261-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="77261-105">İmzalanacak bir karma değer biçimlendirilirken, biçimlendirme işleminin bir parçası olarak ASN.1 nesne tanımlayıcısı (OID) bazı dijital imza algoritmaları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77261-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="77261-106">OID, karma değeri hesaplamak için kullanılan algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="77261-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="77261-107">Özel algoritmalar kullanmak için şifreleme mekanizması genişletmek için nesne tanımlayıcılarını algoritmaları eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77261-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="77261-108">Aşağıdaki örnek, bir nesne tanımlayıcı eşlemek için yeni bir karma algoritması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77261-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="77261-109">[ \<OidEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) iki öznitelik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="77261-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="77261-110">**OID** nesne tanımlayıcı numarası bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="77261-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="77261-111">**Adı** değeri özniteliktir **adı** özniteliğini [ \<nameEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="77261-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="77261-112">Bir nesne tanımlayıcı basit adına eşlenebilir önce bir algoritma adının bir eşleme bir sınıf olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77261-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77261-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77261-113">See Also</span></span>  
 [<span data-ttu-id="77261-114">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="77261-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="77261-115">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="77261-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
