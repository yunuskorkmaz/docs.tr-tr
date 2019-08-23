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
ms.openlocfilehash: a5aebac2d392d4540581dfe7c7afff0819968ac0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912538"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="23e31-102">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="23e31-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="23e31-103">Dijital imzalar, bir programdan diğerine gönderildiğinde verilerin üzerinde oynanmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="23e31-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="23e31-104">Genellikle dijital imza, imzalanacak verilerin karmasını matematiksel bir işlev uygulanarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="23e31-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="23e31-105">Bir karma değeri imzalanacak olarak biçimlendirirken, bazı dijital imza algoritmaları biçimlendirme işleminin bir parçası olarak bir ASN. 1 nesne tanımlayıcısı (OID) ekler.</span><span class="sxs-lookup"><span data-stu-id="23e31-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="23e31-106">OID, karmayı hesaplamak için kullanılan algoritmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="23e31-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="23e31-107">Şifreleme mekanizmasını özel algoritmaları kullanmak üzere genişletmek için algoritmaları nesne tanımlayıcılarıyla eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23e31-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="23e31-108">Aşağıdaki örnek, bir nesne tanımlayıcısının yeni bir karma algoritmasına nasıl eşleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23e31-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="23e31-109">Oıdentry > öğesi iki öznitelik içerir. [ \<](./file-schema/cryptography/oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="23e31-109">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="23e31-110">**OID** özniteliği, nesne tanımlayıcı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="23e31-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="23e31-111">**Name** özniteliği, [ \<nameEntry > öğesinden](./file-schema/cryptography/nameentry-element.md) **ad** özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="23e31-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="23e31-112">Bir nesne tanımlayıcısının basit bir ada eşleştirilemeden önce bir algoritma adından bir sınıfa eşleme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23e31-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e31-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23e31-113">See also</span></span>

- [<span data-ttu-id="23e31-114">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="23e31-114">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="23e31-115">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="23e31-115">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
