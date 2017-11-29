---
title: "Namespace güncelleştirmedikçe öğeleri ve öznitelikleri içeren yeni düğüm için varlık başvurusu genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39110a9b44e6efbe7ad0331cfdb4fbe6078e7cfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="dc08e-102">Namespace güncelleştirmedikçe öğeleri ve öznitelikleri içeren yeni düğüm için varlık başvurusu genişletme</span><span class="sxs-lookup"><span data-stu-id="dc08e-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="dc08e-103">Bir varlık bildiriminin içeriği neredeyse her şeyi içerebileceğinden içeriği gibi bir öğe içerebilir olasılığı yok `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="dc08e-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="dc08e-104">XML ayrıştırıldığında `&aname;` değiştirme içeriğini ayrıştırma zamanında genişletilmiş değil.</span><span class="sxs-lookup"><span data-stu-id="dc08e-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="dc08e-105">Düğümün belgede yerleştirilen kadar öğe için bir ad çözümlemesini gerçekleşemez çünkü XML genişletme yapılmadı.</span><span class="sxs-lookup"><span data-stu-id="dc08e-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="dc08e-106">O zamana kadar hangi ad alanı kapsamında olup hiçbir bilgisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="dc08e-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="dc08e-107">Düğüm belgeye geçirdiğinizde, ad çözümlemesi oluşur ve içerik sonuç varlık uygun düğümlerinden ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="dc08e-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc08e-108">Yeni oluşturulan varlık başvurusu düğümde genişletme oluşur sonra hiçbir zaman oluşana.</span><span class="sxs-lookup"><span data-stu-id="dc08e-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="dc08e-109">Bu nedenle, öğe için değiştirme metinde kullanılan ad alanları üst düğüm kümesi aynı anda bağlanır.</span><span class="sxs-lookup"><span data-stu-id="dc08e-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="dc08e-110">Ad alanı kaldırdığınızda ve başka bir yere yerleştirin varolan varlık başvurusu düğümleri için veya ile kopyalanması varlık başvurusu düğümlerde ancak değiştirilebilir **CloneNode** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dc08e-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc08e-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc08e-111">See Also</span></span>  
 [<span data-ttu-id="dc08e-112">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="dc08e-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
