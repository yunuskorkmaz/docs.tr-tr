---
title: "Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="e3032-102">Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3032-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="e3032-103">Bu örnek kodunuzu XML belge açıklamaları ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3032-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="e3032-104">Bir tür veya üye için XML belgeleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e3032-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="e3032-105">İçinde **Kod düzenleyicisinde**, imlecinizi belgeleri oluşturmak istediğiniz tür veya üye üstündeki satırın getirin.</span><span class="sxs-lookup"><span data-stu-id="e3032-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="e3032-106">Tür `'''` (üç tek tırnak işaretleri).</span><span class="sxs-lookup"><span data-stu-id="e3032-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="e3032-107">Tür veya üye için bir XML çatıyı eklenir **Kod düzenleyicisinde**.</span><span class="sxs-lookup"><span data-stu-id="e3032-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="e3032-108">Uygun etiketleri arasında açıklayıcı bilgileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3032-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3032-109">XML belgeleri bloğu içinde ek satırlar eklerseniz, her bir satır ile başlamalıdır `'''`.</span><span class="sxs-lookup"><span data-stu-id="e3032-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="e3032-110">Tür veya üye ile yeni XML belgeleri yorumları kullanan ek kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3032-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="e3032-111">IntelliSense görüntüler metinden \<Özet > tür veya üye etiketi.</span><span class="sxs-lookup"><span data-stu-id="e3032-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="e3032-112">Belge açıklamaları içeren bir XML dosyası oluşturmak için kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="e3032-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="e3032-113">Daha fazla bilgi için bkz: [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="e3032-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3032-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3032-114">See Also</span></span>  
 [<span data-ttu-id="e3032-115">XML ile kodunuzu belgeleme</span><span class="sxs-lookup"><span data-stu-id="e3032-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="e3032-116">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="e3032-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="e3032-117">/ doc</span><span class="sxs-lookup"><span data-stu-id="e3032-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
