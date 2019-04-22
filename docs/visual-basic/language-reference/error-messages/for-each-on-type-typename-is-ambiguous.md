---
title: Tür birden fazla 'System.Collections.Generic.IEnumerable(Of T)' örneği uyguladığından '<typename>' türü üzerindeki 'For Each' belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 6c34ca43decc3c5d8c72b529d8f51d7cc3b0c6b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833392"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="fa72e-102">'For Each' türündeki '\<typename >' türü '.IEnumerable (Of T) örneği' öğesinin birden çok örneklemesini uyguladığından belirsiz</span><span class="sxs-lookup"><span data-stu-id="fa72e-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>
<span data-ttu-id="fa72e-103">A `For Each` deyimi birden fazla olan bir yineleyici değişkeni belirtir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fa72e-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="fa72e-104">Yineleyici değişkeni uygulayan bir türü olmalıdır <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi biriyle `Collections` isim [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa72e-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="fa72e-105">Her yapı için farklı tür bağımsız değişkeni kullanarak birden fazla oluşturulmuş genel arabirim uygulamak bir sınıf mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fa72e-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="fa72e-106">Yineleyici değişken için bunu yapan bir sınıfı kullandıysanız, bu değişkeni birden fazla sahip <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fa72e-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="fa72e-107">Böyle bir durumda, Visual Basic çağırmak için kullanılacak yöntemi seçin.</span><span class="sxs-lookup"><span data-stu-id="fa72e-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="fa72e-108">**Hata Kimliği:** BC32096</span><span class="sxs-lookup"><span data-stu-id="fa72e-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa72e-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fa72e-109">To correct this error</span></span>  
  
-   <span data-ttu-id="fa72e-110">Kullanma [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) arabirimi tanımlama yineleyici değişken türü olarak atanamadı <xref:System.Collections.IEnumerable.GetEnumerator%2A> kullanmak istediğiniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fa72e-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa72e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa72e-111">See also</span></span>

- [<span data-ttu-id="fa72e-112">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="fa72e-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="fa72e-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="fa72e-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
