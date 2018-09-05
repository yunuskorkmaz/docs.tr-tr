---
title: "Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 3dfec94a3dd1b8da5d371529b91b47f018bb3843
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527602"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="943e2-102">Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="943e2-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="943e2-103">Bu örnek XML belge açıklamaları ekleme kodunuzu gösterir.</span><span class="sxs-lookup"><span data-stu-id="943e2-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="943e2-104">Bir tür veya üye için XML belgeleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="943e2-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="943e2-105">İçinde **Kod Düzenleyicisi**, yukarıdaki belgeleri oluşturmak istediğiniz türe veya üyeye satırında imlecinizi.</span><span class="sxs-lookup"><span data-stu-id="943e2-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="943e2-106">Tür `'''` (üç tek tırnak işareti).</span><span class="sxs-lookup"><span data-stu-id="943e2-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="943e2-107">Türe veya üyeye bir XML çatısı eklenir **Kod Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="943e2-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="943e2-108">Uygun etiketleri arasına tanımlayıcı bilgiler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="943e2-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="943e2-109">XML belgeleri bloğu içinde ek satırlar eklerseniz, her bir çizgi ile başlamalıdır `'''`.</span><span class="sxs-lookup"><span data-stu-id="943e2-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="943e2-110">Türe veya üyeye yeni XML belge açıklamaları kullanan ek kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="943e2-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="943e2-111">IntelliSense görüntüler metinden \<Özet > türe veya üyeye etiketi.</span><span class="sxs-lookup"><span data-stu-id="943e2-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="943e2-112">Belge açıklamaları içeren bir XML dosyası oluşturmak için kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="943e2-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="943e2-113">Daha fazla bilgi için [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="943e2-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943e2-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="943e2-114">See Also</span></span>  
 [<span data-ttu-id="943e2-115">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="943e2-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="943e2-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="943e2-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)  
 [<span data-ttu-id="943e2-117">/doc</span><span class="sxs-lookup"><span data-stu-id="943e2-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
