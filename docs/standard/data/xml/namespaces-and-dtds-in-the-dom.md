---
title: Ad alanları ve DOM DTD'leri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92d7a50d2db25f5e4d32734d550ce2d55a02e3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568686"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="0f3bb-102">Ad alanları ve DOM DTD'leri</span><span class="sxs-lookup"><span data-stu-id="0f3bb-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="0f3bb-103">Belge türü tanımları (DTD) complicate ad alanı desteği.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="0f3bb-104">Örneğin, aşağıdaki XML adlarında iki nokta üst üste içeren varsayılan öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="0f3bb-105">Bu yapıyı izin verilip verilmediğini olası çözümlemeler aşağıda belirtilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0f3bb-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
-   <span data-ttu-id="0f3bb-106">`x:` Çözümlenebilir kullanarak bir ad alanı öneki, ancak bu öneki olmalıdır olarak kabul edilir bir `xmlns:x` ayrıca DTD içinde herhangi bir yerde bulunmalıdır ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="0f3bb-107">Bu örnek belgeye farklı bir şey bu öneki eşlemek için bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
-   <span data-ttu-id="0f3bb-108">`x:` Bir ad alanı öneki kabul edilir, ancak bu öneki örneği öğeleri bağlamında her zaman çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="0f3bb-109">Bu öneki gerçekte ad alanı kapsamında bağlı olarak farklı ad Tekdüzen Kaynak Tanımlayıcıları (URI'ler) için eşleme anlamına gelir `item` öğesi görünür.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="0f3bb-110">Bu davranış önceki maddede verilen çözümleme'den daha tahmin edilebilir, ancak varsayılan öznitelikler gerçekleştirilip gerektirdiğinden diğer karmaşık ayrımlar sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
-   <span data-ttu-id="0f3bb-111">İki nokta üst üste DTD içinde olduğundan ve öznitelik adı yoksayıldı `x:y`, önek ve hiçbir ad alanı URI'si.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
-   <span data-ttu-id="0f3bb-112">İki nokta üst üste varsayılan özniteliğinde DTD içinde adlarında iki nokta üst üste desteklenmez söyleyen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="0f3bb-113">Bu tahmin edilebilir bir davranış olur, ancak birçok World Wide Web Konsorsiyumu (W3C) yüklenemiyor anlamına gelir DTD'leri yayımlanan.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
-   <span data-ttu-id="0f3bb-114">Kullanıcı DTD doğrulama istediğinde, tüm belgeyi ad alanı desteğini devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="0f3bb-115">W3C DTD'leri ve tahmin edilebilir bir davranış sonuçlarında yüklemek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="0f3bb-116">Microsoft .NET Framework XML'de maksimum W3C uyumluluk için ikinci seçeneği uygular.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f3bb-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f3bb-117">See Also</span></span>  
 [<span data-ttu-id="0f3bb-118">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="0f3bb-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
