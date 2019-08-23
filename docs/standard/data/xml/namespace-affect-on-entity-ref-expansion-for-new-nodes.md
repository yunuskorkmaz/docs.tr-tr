---
title: Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a92f1b08719c926e6384c220e3695de26dbb4fd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967323"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="0fa28-102">Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi</span><span class="sxs-lookup"><span data-stu-id="0fa28-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="0fa28-103">Bir varlık bildiriminin içeriği neredeyse her şey içerebildiğinden, içeriğin gibi `<!ENTITY aname "<elem>test</elem>">`bir öğe içerebildiği bir olasılık vardır.</span><span class="sxs-lookup"><span data-stu-id="0fa28-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="0fa28-104">XML ayrıştırıldığında, `&aname;` ayrıştırma zamanında değiştirme içeriğiyle genişletilmez.</span><span class="sxs-lookup"><span data-stu-id="0fa28-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="0fa28-105">XML genişletmesi bitmedi çünkü öğe için ad alanının çözümlenmesi, düğüm belgeye yerleştirilene kadar gerçekleşemez.</span><span class="sxs-lookup"><span data-stu-id="0fa28-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="0fa28-106">Bu saate kadar, kapsamda ne ad alanı olduğuna ilişkin bir bilgi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0fa28-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="0fa28-107">Düğüm belgeye eklendiğinde, ad alanı çözümlemesi oluşur ve sonuçta elde edilen varlık içeriği ilgili düğümlere ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0fa28-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fa28-108">Yeni oluşturulan bir varlık başvurusu düğümünde genişletme gerçekleştikten sonra, hiçbir şekilde yeniden gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="0fa28-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="0fa28-109">Bu nedenle, öğe için değiştirme metninde kullanılan ad alanları, üst düğümün ayarlandığı zamanda bağlanır.</span><span class="sxs-lookup"><span data-stu-id="0fa28-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="0fa28-110">Ancak, başka bir yerde veya **CloneNode** yöntemiyle kopyalanan varlık başvuru düğümlerinde bu ad alanı, var olan varlık başvuru düğümleri için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0fa28-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fa28-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fa28-111">See also</span></span>

- [<span data-ttu-id="0fa28-112">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="0fa28-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
