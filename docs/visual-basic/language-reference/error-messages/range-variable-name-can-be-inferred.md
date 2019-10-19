---
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: ca50ddd86cfbba8db0148ed315645714acabc18d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582418"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="b2945-102">Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir</span><span class="sxs-lookup"><span data-stu-id="b2945-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="b2945-103">Bir veya daha fazla bağımsız değişken alan bir programlama öğesi bir LINQ sorgusuna dahildir.</span><span class="sxs-lookup"><span data-stu-id="b2945-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="b2945-104">Derleyici, bu programlama öğesinden bir Aralık değişkeni çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="b2945-104">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="b2945-105">**Hata kimliği:** BC36599</span><span class="sxs-lookup"><span data-stu-id="b2945-105">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b2945-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b2945-106">To correct this error</span></span>

<span data-ttu-id="b2945-107">Aşağıdaki kodda gösterildiği gibi, programlama öğesi için açık bir değişken adı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="b2945-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="b2945-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2945-108">See also</span></span>

- [<span data-ttu-id="b2945-109">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="b2945-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b2945-110">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="b2945-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
