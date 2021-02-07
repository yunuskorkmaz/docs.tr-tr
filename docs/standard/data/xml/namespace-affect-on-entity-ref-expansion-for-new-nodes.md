---
description: 'Daha fazla bilgi: öğe ve öznitelik Içeren yeni düğümler için varlık başvurusu genişletmesi üzerinde ad alanı etkileri'
title: Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi
ms.date: 03/30/2017
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 48345d75f9cf77f8e70655c8f166978cafbf06c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713487"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="0e97c-103">Öğe ve Öznitelikler İçeren Yeni Düğümler için Varlık Başvurusu Genişlemesine Ad Alanı Etkisi</span><span class="sxs-lookup"><span data-stu-id="0e97c-103">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>

<span data-ttu-id="0e97c-104">Bir varlık bildiriminin içeriği neredeyse her şey içerebildiğinden, içeriğin gibi bir öğe içerebildiği bir olasılık vardır `<!ENTITY aname "<elem>test</elem>">` .</span><span class="sxs-lookup"><span data-stu-id="0e97c-104">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="0e97c-105">XML ayrıştırıldığında, `&aname;` ayrıştırma zamanında değiştirme içeriğiyle genişletilmez.</span><span class="sxs-lookup"><span data-stu-id="0e97c-105">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="0e97c-106">XML genişletmesi bitmedi çünkü öğe için ad alanının çözümlenmesi, düğüm belgeye yerleştirilene kadar gerçekleşemez.</span><span class="sxs-lookup"><span data-stu-id="0e97c-106">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="0e97c-107">Bu saate kadar, kapsamda ne ad alanı olduğuna ilişkin bir bilgi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0e97c-107">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="0e97c-108">Düğüm belgeye eklendiğinde, ad alanı çözümlemesi oluşur ve sonuçta elde edilen varlık içeriği ilgili düğümlere ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0e97c-108">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e97c-109">Yeni oluşturulan bir varlık başvurusu düğümünde genişletme gerçekleştikten sonra, hiçbir şekilde yeniden gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="0e97c-109">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="0e97c-110">Bu nedenle, öğe için değiştirme metninde kullanılan ad alanları, üst düğümün ayarlandığı zamanda bağlanır.</span><span class="sxs-lookup"><span data-stu-id="0e97c-110">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="0e97c-111">Ancak, başka bir yerde veya **CloneNode** yöntemiyle kopyalanan varlık başvuru düğümlerinde bu ad alanı, var olan varlık başvuru düğümleri için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e97c-111">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e97c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e97c-112">See also</span></span>

- [<span data-ttu-id="0e97c-113">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="0e97c-113">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
