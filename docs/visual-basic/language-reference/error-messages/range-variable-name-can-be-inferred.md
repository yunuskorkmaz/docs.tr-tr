---
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6d082511d501b961b537317f0cb17bcd1c9370b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594627"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="10004-102">Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir</span><span class="sxs-lookup"><span data-stu-id="10004-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="10004-103">Bir veya daha fazla bağımsız değişken almayan bir programlama öğesi bir LINQ Sorgu dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="10004-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="10004-104">Derleyici aralık değişkeni bu programlama öğeden Infer alamıyor.</span><span class="sxs-lookup"><span data-stu-id="10004-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="10004-105">**Hata Kimliği:** BC36599</span><span class="sxs-lookup"><span data-stu-id="10004-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10004-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="10004-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="10004-107">Aşağıdaki kodda gösterildiği gibi programlama öğesi için açık bir değişken adı girin:</span><span class="sxs-lookup"><span data-stu-id="10004-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="10004-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10004-108">See Also</span></span>  
 [<span data-ttu-id="10004-109">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="10004-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="10004-110">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="10004-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
