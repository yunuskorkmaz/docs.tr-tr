---
title: Tür birden fazla 'System.Collections.Generic.IEnumerable(Of T)' örneği uyguladığından '<typename>' türü üzerindeki 'For Each' belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 0f19836efeabcf1d9e5097667c719c1f7d99cbbb
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163473"
---
# <a name="bc32096-for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="4abf9-102">\<typename>Tür birden çok ' System. Collections. Generic. IEnumerable (Of T) ' örneği uyguladığı için, ' ' TÜRÜNDEKI BC32096: ' for each ' belirsiz</span><span class="sxs-lookup"><span data-stu-id="4abf9-102">BC32096: 'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>

<span data-ttu-id="4abf9-103">Bir `For Each` ifade, birden fazla metodu olan bir yineleyici değişkenini belirtir <xref:System.Collections.IEnumerable.GetEnumerator%2A> .</span><span class="sxs-lookup"><span data-stu-id="4abf9-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>

 <span data-ttu-id="4abf9-104">Yineleyici değişkeni, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> `Collections` .NET Framework ad uzaylarından birinde veya arabirimini uygulayan bir türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4abf9-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="4abf9-105">Bir sınıfın, her oluşturma için farklı bir tür bağımsız değişkeni kullanılarak birden fazla oluşturulmuş genel arabirim uygulaması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4abf9-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="4abf9-106">Bunu yapan bir sınıf Yineleyici değişkeni için kullanılırsa, bu değişkenin birden fazla <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="4abf9-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="4abf9-107">Böyle bir durumda Visual Basic hangi yöntemin çağrılacağını seçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4abf9-107">In such a case, Visual Basic cannot choose which method to call.</span></span>

 <span data-ttu-id="4abf9-108">**Hata kimliği:** BC32096</span><span class="sxs-lookup"><span data-stu-id="4abf9-108">**Error ID:** BC32096</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4abf9-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4abf9-109">To correct this error</span></span>

- <span data-ttu-id="4abf9-110">Yineleyici değişken türünü kullanmak istediğiniz yöntemi tanımlayan arabirime dönüştürmek için [DirectCast İşleci](../operators/directcast-operator.md) veya [TryCast işlecini](../operators/trycast-operator.md) kullanın <xref:System.Collections.IEnumerable.GetEnumerator%2A> .</span><span class="sxs-lookup"><span data-stu-id="4abf9-110">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>

## <a name="see-also"></a><span data-ttu-id="4abf9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4abf9-111">See also</span></span>

- [<span data-ttu-id="4abf9-112">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="4abf9-112">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="4abf9-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="4abf9-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
