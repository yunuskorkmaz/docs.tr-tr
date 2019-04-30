---
title: -= işleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688689"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="e499e-102">-= işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e499e-102">-= operator (C# Reference)</span></span>

<span data-ttu-id="e499e-103">Çıkarma atama işleci.</span><span class="sxs-lookup"><span data-stu-id="e499e-103">The subtraction assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e499e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e499e-104">Remarks</span></span>

<span data-ttu-id="e499e-105">Bir ifade kullanarak `-=` atama işleci gibi</span><span class="sxs-lookup"><span data-stu-id="e499e-105">An expression using the `-=` assignment operator, such as</span></span>

```csharp
x -= y
```

 <span data-ttu-id="e499e-106">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="e499e-106">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="e499e-107">dışında `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e499e-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="e499e-108">Anlamını [-işleci](subtraction-operator.md) türlerine bağlıdır `x` ve `y` (sayısal işlenenler için çıkarma temsilci temsilcinin işlenenleri için temizleme vb.).</span><span class="sxs-lookup"><span data-stu-id="e499e-108">The meaning of the [- operator](subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>

<span data-ttu-id="e499e-109">`-=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [-işleci](subtraction-operator.md) (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e499e-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](subtraction-operator.md) (see [operator](../keywords/operator.md)).</span></span>

<span data-ttu-id="e499e-110">-= İşleci ayrıca C# dilinde bir olayın aboneliğini kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e499e-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="e499e-111">Daha fazla bilgi için [nasıl yapılır: Abone olma ve aboneliği olaylardan](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="e499e-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="e499e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e499e-112">Example</span></span>

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a><span data-ttu-id="e499e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e499e-113">See also</span></span>

- [<span data-ttu-id="e499e-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e499e-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e499e-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e499e-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e499e-116">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e499e-116">C# operators</span></span>](index.md)
