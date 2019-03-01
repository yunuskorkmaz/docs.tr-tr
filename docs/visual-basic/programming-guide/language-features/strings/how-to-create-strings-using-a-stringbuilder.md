---
title: "Nasıl yapılır: Visual Basic'de bir StringBuilder kullanarak dize oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 5cd118ddd196bdf84045ae8b02fe590e5b087e4e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967964"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="3ba78-102">Nasıl yapılır: Visual Basic'de bir StringBuilder kullanarak dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ba78-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="3ba78-103">Bu örnekte, uzun bir dize kullanarak çok sayıda küçük dizelerden oluşturur <xref:System.Text.StringBuilder> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3ba78-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="3ba78-104"><xref:System.Text.StringBuilder> Sınıfı, daha verimli `&=` birçok dizeleri birleştirme işleci.</span><span class="sxs-lookup"><span data-stu-id="3ba78-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ba78-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ba78-105">Example</span></span>  
 <span data-ttu-id="3ba78-106">Aşağıdaki örnek, bir örneğini oluşturur. <xref:System.Text.StringBuilder> sınıfı, bu örneğe 1.000 dizeleri ekler ve ardından kendi dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ba78-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a><span data-ttu-id="3ba78-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ba78-107">See also</span></span>
- [<span data-ttu-id="3ba78-108">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="3ba78-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="3ba78-109">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="3ba78-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="3ba78-110">Dizeler</span><span class="sxs-lookup"><span data-stu-id="3ba78-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="3ba78-111">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3ba78-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="3ba78-112">Dizeleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="3ba78-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
