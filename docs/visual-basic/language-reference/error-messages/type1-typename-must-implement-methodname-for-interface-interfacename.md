---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;methodname&gt; &#39; Arabirimin &#39; &lt;InterfaceName&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: ff9ffd50f7f21814d5e4c23fd8df50b12bf746f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642454"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="fc1dd-102">&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;methodname&gt; &#39; Arabirimin &#39; &lt;InterfaceName&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="fc1dd-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="fc1dd-103">Bir sınıf veya yapı bir arabirim uygulamak talep ancak arabirim tarafından tanımlanan bir yordam uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="fc1dd-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="fc1dd-104">Her arabirimin üyesi uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc1dd-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="fc1dd-105">**Hata Kimliği:** BC30149</span><span class="sxs-lookup"><span data-stu-id="fc1dd-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fc1dd-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fc1dd-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="fc1dd-107">Bir yordam aynı adı ve imzası arabirim içinde tanımlanmış olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="fc1dd-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="fc1dd-108">Eklediğinizden emin olun en az `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fc1dd-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="fc1dd-109">Ekleme bir `Implements` sonuna yan tümcesi `Function` veya `Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fc1dd-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="fc1dd-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fc1dd-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fc1dd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc1dd-111">See also</span></span>
- [<span data-ttu-id="fc1dd-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="fc1dd-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="fc1dd-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="fc1dd-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
