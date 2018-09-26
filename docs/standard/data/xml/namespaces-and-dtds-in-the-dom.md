---
title: Ad alanları ve DTD'ler DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203101"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="e1988-102">Ad alanları ve DTD'ler DOM</span><span class="sxs-lookup"><span data-stu-id="e1988-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="e1988-103">Belge türü tanımları (DTD'ler) complicate ad alanı desteği.</span><span class="sxs-lookup"><span data-stu-id="e1988-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="e1988-104">Örneğin, aşağıdaki XML, iki nokta üst üste adlarında içeren varsayılan öznitelikler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e1988-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="e1988-105">Tento konstruktor je izin verilip verilmediğini olası çözümlemeler aşağıda belirtilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1988-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
-   <span data-ttu-id="e1988-106">`x:` Çözümlenebilir kullanarak bir ad alanı öneki, ancak bu öneki olmalıdır olarak kabul edilir bir `xmlns:x` ad alanı bildirimi, ayrıca DTD'nin yere bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1988-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="e1988-107">Bu örnek belgeye farklı bir şey bu ön ek eşlemek için bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="e1988-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
-   <span data-ttu-id="e1988-108">`x:` Bir ad alanı öneki kabul edilir, ancak bu ön eki her zaman örneği öğeleri bağlamında çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="e1988-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="e1988-109">Önek gerçekten eşleme farklı bir ad alanı Tekdüzen Kaynak Tanımlayıcıları (URI'lar) ad alanı kapsamında bağlı olarak başka bir deyişle `item` öğe görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e1988-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="e1988-110">Bu davranış önceki maddede verilen çözümleme daha öngörülebilir olmakla birlikte, varsayılan öznitelikler gerçekleştirilmiş gerektirdiğinden, diğer karmaşık ayrımlar sahip.</span><span class="sxs-lookup"><span data-stu-id="e1988-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
-   <span data-ttu-id="e1988-111">İki nokta üst üste bir DTD'nin içinde olduğundan ve öznitelik adı olduğundan göz ardı edilir `x:y`, önek ve ad alanı URI.</span><span class="sxs-lookup"><span data-stu-id="e1988-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
-   <span data-ttu-id="e1988-112">İki nokta üst üste varsayılan özniteliğinde, iki nokta üst üste bir DTD'nin içinde adlarının desteklenmediğine belirten, özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1988-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="e1988-113">Bu tahmin edilebilir bir davranışa neden olur, ancak DTD'ler çok World Wide Web Consortium (W3C) yüklenemiyor anlamına gelir yayımlanmış.</span><span class="sxs-lookup"><span data-stu-id="e1988-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
-   <span data-ttu-id="e1988-114">Kullanıcı DTD'nin doğrulama istediğinde, ad alanı desteği için belgenin tamamını kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1988-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="e1988-115">W3C DTD'ler ve sonuçları tahmin edilebilir davranış yüklemek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="e1988-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="e1988-116">Microsoft .NET Framework XML W3C en büyük uyumluluk için ikinci seçeneği uygular.</span><span class="sxs-lookup"><span data-stu-id="e1988-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1988-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1988-117">See also</span></span>

- [<span data-ttu-id="e1988-118">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="e1988-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
