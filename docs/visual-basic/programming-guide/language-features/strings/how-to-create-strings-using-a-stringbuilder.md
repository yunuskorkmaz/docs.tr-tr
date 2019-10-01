---
title: 'Nasıl yapılır: Visual Basic StringBuilder kullanarak dize oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 19e036abc9d25ec7fdfd6c33ebb420ec4f503cbc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700102"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="747fd-102">Nasıl yapılır: Visual Basic StringBuilder kullanarak dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="747fd-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="747fd-103">Bu örnek <xref:System.Text.StringBuilder> sınıfını kullanarak birçok küçük dizeden uzun bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="747fd-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="747fd-104">@No__t-0 sınıfı, çok sayıda dizeyi birleştirirken `&=` işlecinden daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="747fd-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="747fd-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="747fd-105">Example</span></span>

<span data-ttu-id="747fd-106">Aşağıdaki örnek <xref:System.Text.StringBuilder> sınıfının bir örneğini oluşturur, bu örneğe 1.000 dizelerini ekler ve sonra dize gösterimini döndürür:</span><span class="sxs-lookup"><span data-stu-id="747fd-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="747fd-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="747fd-107">See also</span></span>

- [<span data-ttu-id="747fd-108">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="747fd-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="747fd-109">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="747fd-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="747fd-110">Dizeler</span><span class="sxs-lookup"><span data-stu-id="747fd-110">Strings</span></span>](index.md)
- [<span data-ttu-id="747fd-111">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="747fd-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="747fd-112">Dizeleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="747fd-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
