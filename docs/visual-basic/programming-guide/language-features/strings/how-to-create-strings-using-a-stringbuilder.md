---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic StringBuilder kullanarak dize oluşturma'
title: 'Nasıl yapılır: StringBuilder kullanarak dize oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 6def32517f71ec3c2a7795c3395e3e572903ce1e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429825"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="1cdb1-103">Nasıl yapılır: Visual Basic StringBuilder kullanarak dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="1cdb1-103">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="1cdb1-104">Bu örnek, sınıfını kullanarak çok sayıda küçük dizeden uzun bir dize oluşturur <xref:System.Text.StringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="1cdb1-104">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="1cdb1-105"><xref:System.Text.StringBuilder>Sınıf, `&=` çok sayıda dizeyi birleştirirken işleçten daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="1cdb1-105">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="1cdb1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cdb1-106">Example</span></span>

<span data-ttu-id="1cdb1-107">Aşağıdaki örnek, sınıfının bir örneğini oluşturur <xref:System.Text.StringBuilder> , bu örneğe 1.000 dizelerini ekler ve sonra dize gösterimini döndürür:</span><span class="sxs-lookup"><span data-stu-id="1cdb1-107">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="1cdb1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cdb1-108">See also</span></span>

- [<span data-ttu-id="1cdb1-109">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cdb1-109">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="1cdb1-110">&= Işleci</span><span class="sxs-lookup"><span data-stu-id="1cdb1-110">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="1cdb1-111">Dizeler</span><span class="sxs-lookup"><span data-stu-id="1cdb1-111">Strings</span></span>](index.md)
- [<span data-ttu-id="1cdb1-112">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1cdb1-112">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="1cdb1-113">Dizeleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1cdb1-113">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
