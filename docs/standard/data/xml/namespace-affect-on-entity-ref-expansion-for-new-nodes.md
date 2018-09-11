---
title: Öğeler ve öznitelikler içeren yeni düğümler için varlık başvurusu genişlemesine Namespace etkiler
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4231516848cc50212a3a6a03d101907b2f6b3920
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337037"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="3bf61-102">Öğeler ve öznitelikler içeren yeni düğümler için varlık başvurusu genişlemesine Namespace etkiler</span><span class="sxs-lookup"><span data-stu-id="3bf61-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="3bf61-103">Bir varlık bildiriminin içeriği neredeyse her şeyi içerebileceğinden, içeriği gibi bir öğe içerebilecek bir olasılık yoktur `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="3bf61-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="3bf61-104">XML ayrıştırıldığında `&aname;` değiştirme içeriğini ayrıştırma zamanında genişletilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="3bf61-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="3bf61-105">Genişletme XML belgesine düğüm yerleştirilir kadar öğe için ad çözümleme olamaz çünkü yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="3bf61-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="3bf61-106">O zamana kadar hangi ad alanı kapsamında olduğu bilgisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3bf61-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="3bf61-107">Düğüm belgeye yerleştirdiğinizde, ardından ad çözümlemesi gerçekleşir ve sonuç varlık içeriği uygun düğümlerini ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3bf61-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bf61-108">Yeni oluşturulan varlık başvurusu düğümde genişletme gerçekleşir sonra hiçbir zaman yeniden.</span><span class="sxs-lookup"><span data-stu-id="3bf61-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="3bf61-109">Bu nedenle, değiştirme metni öğe için kullanılan ad alanları üst düğüm kümesi zamanında bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3bf61-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="3bf61-110">Ad alanı çıkarıp başka bir yere yerleştirin, mevcut varlık başvurusu düğümleri için veya ile kopyalanan varlık başvurusu düğümlerinde ancak değiştirilebilir **CloneNode** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3bf61-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf61-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bf61-111">See also</span></span>

- [<span data-ttu-id="3bf61-112">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="3bf61-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
