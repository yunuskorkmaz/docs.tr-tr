---
title: 'How to: create strings using a StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 9295b9d0cdcfdb05dfc75f75f48c16c2354b09b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344375"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="37f32-102">How to: create strings using a StringBuilder in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37f32-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="37f32-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span><span class="sxs-lookup"><span data-stu-id="37f32-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="37f32-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span><span class="sxs-lookup"><span data-stu-id="37f32-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="37f32-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="37f32-105">Example</span></span>

<span data-ttu-id="37f32-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span><span class="sxs-lookup"><span data-stu-id="37f32-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="37f32-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37f32-107">See also</span></span>

- [<span data-ttu-id="37f32-108">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="37f32-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="37f32-109">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="37f32-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="37f32-110">Dizeler</span><span class="sxs-lookup"><span data-stu-id="37f32-110">Strings</span></span>](index.md)
- [<span data-ttu-id="37f32-111">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="37f32-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="37f32-112">Dizeleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="37f32-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
