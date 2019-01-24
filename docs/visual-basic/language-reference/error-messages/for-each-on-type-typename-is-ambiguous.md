---
title: '&#39;Her&#39; türündeki &#39; &lt;typename&gt; &#39; türü, birden çok örneklemesini uyguladığından belirsiz &#39;.IEnumerable (Of T) örneği&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 7fd779ba34afa2a59fa6c42971597df8ce01495a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597352"
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="275d3-102">&#39;Her&#39; türündeki &#39; &lt;typename&gt; &#39; türü, birden çok örneklemesini uyguladığından belirsiz &#39;.IEnumerable (Of T) örneği&#39;</span><span class="sxs-lookup"><span data-stu-id="275d3-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="275d3-103">A `For Each` deyimi birden fazla olan bir yineleyici değişkeni belirtir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="275d3-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="275d3-104">Yineleyici değişkeni uygulayan bir türü olmalıdır <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi biriyle `Collections` isim [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="275d3-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="275d3-105">Her yapı için farklı tür bağımsız değişkeni kullanarak birden fazla oluşturulmuş genel arabirim uygulamak bir sınıf mümkündür.</span><span class="sxs-lookup"><span data-stu-id="275d3-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="275d3-106">Yineleyici değişken için bunu yapan bir sınıfı kullandıysanız, bu değişkeni birden fazla sahip <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="275d3-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="275d3-107">Böyle bir durumda, Visual Basic çağırmak için kullanılacak yöntemi seçin.</span><span class="sxs-lookup"><span data-stu-id="275d3-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="275d3-108">**Hata Kimliği:** BC32096</span><span class="sxs-lookup"><span data-stu-id="275d3-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="275d3-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="275d3-109">To correct this error</span></span>  
  
-   <span data-ttu-id="275d3-110">Kullanma [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) arabirimi tanımlama yineleyici değişken türü olarak atanamadı <xref:System.Collections.IEnumerable.GetEnumerator%2A> kullanmak istediğiniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="275d3-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275d3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="275d3-111">See also</span></span>
- [<span data-ttu-id="275d3-112">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="275d3-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="275d3-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="275d3-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
