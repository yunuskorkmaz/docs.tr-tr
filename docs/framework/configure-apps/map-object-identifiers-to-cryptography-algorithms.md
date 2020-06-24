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
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="0a059-103">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="0a059-103">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="0a059-104">Dijital imzalar, bir programdan diğerine gönderildiğinde verilerin üzerinde oynanmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a059-104">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="0a059-105">Genellikle dijital imza, imzalanacak verilerin karmasını matematiksel bir işlev uygulanarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="0a059-105">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="0a059-106">Bir karma değeri imzalanacak olarak biçimlendirirken, bazı dijital imza algoritmaları biçimlendirme işleminin bir parçası olarak bir ASN. 1 nesne tanımlayıcısı (OID) ekler.</span><span class="sxs-lookup"><span data-stu-id="0a059-106">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="0a059-107">OID, karmayı hesaplamak için kullanılan algoritmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a059-107">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="0a059-108">Şifreleme mekanizmasını özel algoritmaları kullanmak üzere genişletmek için algoritmaları nesne tanımlayıcılarıyla eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a059-108">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="0a059-109">Aşağıdaki örnek, bir nesne tanımlayıcısının yeni bir karma algoritmasına nasıl eşleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a059-109">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="0a059-110">[ \<oidEntry> Öğesi](./file-schema/cryptography/oidentry-element.md) iki öznitelik içerir.</span><span class="sxs-lookup"><span data-stu-id="0a059-110">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="0a059-111">**OID** özniteliği, nesne tanımlayıcı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="0a059-111">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="0a059-112">**Name** [ \<nameEntry> özniteliği, öğesinden](./file-schema/cryptography/nameentry-element.md) **ad** özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="0a059-112">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="0a059-113">Bir nesne tanımlayıcısının basit bir ada eşleştirilemeden önce bir algoritma adından bir sınıfa eşleme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a059-113">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a059-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a059-114">See also</span></span>

- [<span data-ttu-id="0a059-115">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0a059-115">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="0a059-116">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="0a059-116">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
