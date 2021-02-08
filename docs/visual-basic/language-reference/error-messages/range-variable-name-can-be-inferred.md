---
description: 'Hakkında daha fazla bilgi edinin: BC36599: Range değişken adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan çıkarsanamıyor'
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: b729b6786f9b7803a794b9a4e786d94fa41a57ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792069"
---
# <a name="bc36599-range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="ae8ee-103">BC36599: Range değişken adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan çıkarsanamıyor</span><span class="sxs-lookup"><span data-stu-id="ae8ee-103">BC36599: Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="ae8ee-104">Bir veya daha fazla bağımsız değişken alan bir programlama öğesi bir LINQ sorgusuna dahildir.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-104">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="ae8ee-105">Derleyici, bu programlama öğesinden bir Aralık değişkeni çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-105">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="ae8ee-106">**Hata kimliği:** BC36599</span><span class="sxs-lookup"><span data-stu-id="ae8ee-106">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ae8ee-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ae8ee-107">To correct this error</span></span>

<span data-ttu-id="ae8ee-108">Aşağıdaki kodda gösterildiği gibi, programlama öğesi için açık bir değişken adı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="ae8ee-108">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="ae8ee-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-109">See also</span></span>

- [<span data-ttu-id="ae8ee-110">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="ae8ee-110">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ae8ee-111">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="ae8ee-111">Select Clause</span></span>](../queries/select-clause.md)
