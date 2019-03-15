---
title: 'Nasıl yapılır: olay örneklerini - depolamak için Sözlük kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 03/11/2019
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f8522e499887398402f63c7788bbc6c6c4f57782
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845286"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="3fa0b-102">Nasıl yapılır: olay örneklerini depolamak için Sözlük kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3fa0b-102">How to: use a dictionary to store event instances (C# Programming Guide)</span></span>

<span data-ttu-id="3fa0b-103">Bir kullanımı `add` ve `remove` özel olay erişimcilerini olan çok sayıda olay her olay için bir alan ayırma, ancak bunun yerine kullanıma sunmak için bir <xref:System.Collections.Generic.Dictionary%602> aşağıdaki örnekte gösterildiği gibi olay örneklerini depolamak için örneği.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-103">One use for the `add` and `remove` custom event accessors is to expose many events without allocating a field for each event, but instead using a <xref:System.Collections.Generic.Dictionary%602> instance to store the event instances, as the example below demonstrates.</span></span> <span data-ttu-id="3fa0b-104">Bu yalnızca çok sayıda olay türünde, ancak çoğu olayların abone değil, beklediğiniz yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-104">This is only useful if a type has many events, but you expect that most of the events will not be subscribed to.</span></span>

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

<span data-ttu-id="3fa0b-105">Bu uygulama davranışını uyan [ekleme ve kaldırma Temsilciler](~/_csharplang/spec/delegates.md#delegate-invocation) içinde C# dil belirtimi.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-105">This implementation conforms to the behavior for [adding and removing delegates](~/_csharplang/spec/delegates.md#delegate-invocation) in the C# language specification.</span></span>

<span data-ttu-id="3fa0b-106">Unutmayın [kilit](../../language-reference/keywords/lock-statement.md) deyimi yalnızca kullanılan *erişim* olay işleyicileri sahip sözlük.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-106">Note that the [lock](../../language-reference/keywords/lock-statement.md) statement is used only to *access* the dictionary with event handlers.</span></span> <span data-ttu-id="3fa0b-107">Gövdesi içinde bir olay işleyicisi çağırma yoksa `lock` ifadesi olarak müşteri adayı için kilitlenme veya kilit çakışması.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-107">Don't invoke an event handler inside the body of the `lock` statement, as it could lead to deadlocks or lock contention.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fa0b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fa0b-108">See also</span></span>

- [<span data-ttu-id="3fa0b-109">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3fa0b-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3fa0b-110">Olaylar</span><span class="sxs-lookup"><span data-stu-id="3fa0b-110">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="3fa0b-111">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="3fa0b-111">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
