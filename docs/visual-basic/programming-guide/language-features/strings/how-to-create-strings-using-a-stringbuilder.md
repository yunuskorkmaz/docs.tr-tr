---
title: 'Nasıl: StringBuilder kullanarak dizeleri oluşturmak'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645333"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="d1ca4-102">Nasıl: Visual Basic bir StringBuilder kullanarak dizeleri oluşturmak</span><span class="sxs-lookup"><span data-stu-id="d1ca4-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="d1ca4-103">Bu örnek, <xref:System.Text.StringBuilder> sınıfı kullanarak birçok küçük dizeleri uzun bir dize inşa eder.</span><span class="sxs-lookup"><span data-stu-id="d1ca4-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="d1ca4-104">Sınıf, <xref:System.Text.StringBuilder> birçok dizeleri `&=` biraraya getirmek için işleçten daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="d1ca4-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="d1ca4-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1ca4-105">Example</span></span>

<span data-ttu-id="d1ca4-106">Aşağıdaki <xref:System.Text.StringBuilder> örnek, sınıfın bir örneğini oluşturur, bu örneğe 1.000 dize ekler ve dize gösterimini döndürür:</span><span class="sxs-lookup"><span data-stu-id="d1ca4-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="d1ca4-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1ca4-107">See also</span></span>

- [<span data-ttu-id="d1ca4-108">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="d1ca4-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="d1ca4-109">&= Operatör</span><span class="sxs-lookup"><span data-stu-id="d1ca4-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="d1ca4-110">Dizeler</span><span class="sxs-lookup"><span data-stu-id="d1ca4-110">Strings</span></span>](index.md)
- [<span data-ttu-id="d1ca4-111">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1ca4-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="d1ca4-112">Dizeleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d1ca4-112">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
