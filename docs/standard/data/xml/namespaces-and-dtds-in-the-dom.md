---
title: DOM Ad Alanları ve DTD’ler
ms.date: 03/30/2017
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: bd2a15b96cb456f475eb7dec439a0f328ae72a55
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830148"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="9b7a7-102">DOM Ad Alanları ve DTD’ler</span><span class="sxs-lookup"><span data-stu-id="9b7a7-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="9b7a7-103">Belge türü tanımları (DTD 'Ler) ad alanı desteğini karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="9b7a7-104">Örneğin, aşağıdaki XML adlarında iki nokta üst üste içeren varsayılan öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="9b7a7-105">Bu yapı için izin veriliyorsa aşağıdakiler olası çözümlerdir:</span><span class="sxs-lookup"><span data-stu-id="9b7a7-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
- <span data-ttu-id="9b7a7-106">, `x:` Bir ad alanı öneki olarak değerlendirilir, ancak bu ön ek bir `xmlns:x` ad alanı bildirimi kullanılarak çözümlenebilmelidir, bu da DTD 'de bir yerde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="9b7a7-107">Bu öneki örnek belgesinde farklı bir şeye eşlemek hatadır.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
- <span data-ttu-id="9b7a7-108">, `x:` Bir ad alanı öneki olarak değerlendirilir, ancak bu ön ek, örnek öğelerinin bağlamında her zaman çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="9b7a7-109">Bu, önekinin, öğenin göründüğü ad alanı kapsamına bağlı olarak, aslında farklı ad alanı Tekdüzen Kaynak tanımlayıcılarına (URI 'Ler) eşleme olabileceği anlamına gelir `item` .</span><span class="sxs-lookup"><span data-stu-id="9b7a7-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="9b7a7-110">Bu davranış, önceki madde işaretinde verilen çözünürlükten daha öngörülebilir hale gelir, ancak varsayılan özniteliklerin gerçekleştirilmiş olması gerektiğinden diğer karmaşık kollar vardır.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
- <span data-ttu-id="9b7a7-111">İki nokta üst üste, bir DTD 'de olduğundan ve özniteliğin adı `x:y` , ön ek ve ad alanı URI 'si olmadığından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
- <span data-ttu-id="9b7a7-112">Varsayılan öznitelikteki iki nokta üst üste, bir DTD içindeki adlarda iki nokta üst üsteyle desteklenmediğini söyleyen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="9b7a7-113">Bu, öngörülebilir bir davranışa neden olur, ancak World Wide Web Konsorsiyumu (W3C) yayımlanmış DTD 'lerin çoğunu yükleyemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
- <span data-ttu-id="9b7a7-114">Kullanıcı DTD doğrulaması istediğinde, tüm belge için ad alanı desteği kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="9b7a7-115">Bu, W3C DTD 'Leri yüklemek ve tahmin edilebilir bir davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="9b7a7-116">Microsoft .NET çerçevesindeki XML, en yüksek W3C uyumluluğu için ikinci seçeneği uygular.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b7a7-117">See also</span></span>

- [<span data-ttu-id="9b7a7-118">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="9b7a7-118">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
