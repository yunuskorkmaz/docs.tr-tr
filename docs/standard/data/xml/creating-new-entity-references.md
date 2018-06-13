---
title: Yeni varlık başvuruları oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fefea6f8dfd74dfd31c7c07a158e4935ab0e02c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568452"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="dac53-102">Yeni varlık başvuruları oluşturma</span><span class="sxs-lookup"><span data-stu-id="dac53-102">Creating New Entity References</span></span>
<span data-ttu-id="dac53-103">**CreateEntityReference** yöntemi yeni bir oluşturur **XmlEntityReference** düğümü.</span><span class="sxs-lookup"><span data-stu-id="dac53-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="dac53-104">Başvurulan varlık adı zaten bildirilmiş olmadığını görmek için XML belge nesne modeli (DOM) arar.</span><span class="sxs-lookup"><span data-stu-id="dac53-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="dac53-105">Varsa, alt düğümleri **XmlEntityReference** düğümü varlık bildirimi düğümden kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="dac53-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="dac53-106">Eşleşen hiçbir varlık bildirimi ise, boş metin düğümü yalnızca düğümün alt öğesi varlık başvuru eklendi.</span><span class="sxs-lookup"><span data-stu-id="dac53-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="dac53-107">Çünkü alt düğümlerin **XmlEntityReference** düğümü diğer düğümlere kopyalarını, bu alt düğümlerin salt okunurdur ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="dac53-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="dac53-108">Düğümleri kopyalandığında, olabilir. bir ad alanı varlık başvurusu noktasında kapsamı.</span><span class="sxs-lookup"><span data-stu-id="dac53-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="dac53-109">Bu ad alanı oluşturulan herhangi bir öğe veya öznitelik düğümünün yapılandırmasını etkiler.</span><span class="sxs-lookup"><span data-stu-id="dac53-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dac53-110">DOM alt düğüm ekler **EntityReference** eklediğinizde yalnızca **EntityReference** belge düğümü.</span><span class="sxs-lookup"><span data-stu-id="dac53-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="dac53-111">Yeni oluşturulan **EntityReference** düğümünüz alt düğüm yok.</span><span class="sxs-lookup"><span data-stu-id="dac53-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="dac53-112">Olsa bile **XmlDataDocument** türetilmiş bir sınıf **XmlDocument**, **XmlDataDocument** varlık başvuruları oluşturulmasını desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="dac53-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="dac53-113">Bunun nedeni, **EntityReference** alt salt okunur.</span><span class="sxs-lookup"><span data-stu-id="dac53-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="dac53-114">Alt öğelerinin bir **EntityReference** düğümü birden fazla bölge yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="dac53-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="dac53-115">Bu durumda, bir satır parçası ilişkili bir parçasını içeren bölgesiyle bir **EntityReference** salt okunur olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dac53-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac53-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dac53-116">See Also</span></span>  
 [<span data-ttu-id="dac53-117">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="dac53-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
