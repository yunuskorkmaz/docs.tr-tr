---
title: C#İfadeleri - Turu C# dil
description: ifadeleri ve işlenenleri işleçleri olan yapı taşları C# dil
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: ffe800304a9125e11e20d96a84919936f1fee2c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753640"
---
# <a name="expressions"></a><span data-ttu-id="5e048-103">İfadeler</span><span class="sxs-lookup"><span data-stu-id="5e048-103">Expressions</span></span>

<span data-ttu-id="5e048-104">*İfadeleri* oluşturulan *işlenenler* ve *işleçleri*.</span><span class="sxs-lookup"><span data-stu-id="5e048-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="5e048-105">İfade işleçleri işlenenlere uygulamak için hangi işlemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e048-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="5e048-106">İşleçler örnekler `+`, `-`, `*`, `/`, ve `new`.</span><span class="sxs-lookup"><span data-stu-id="5e048-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="5e048-107">Değişmez değerler, alanlar, yerel değişkenleri ve ifadeleri işlenenler örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="5e048-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="5e048-108">Bir ifade birden çok işleç içeren *öncelik* işleçleri tek tek işleçler değerlendirilme sırası denetler.</span><span class="sxs-lookup"><span data-stu-id="5e048-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="5e048-109">Örneğin, ifade `x + y * z` değerlendirmesinde `x + (y * z)` çünkü `*` işleci daha yüksek önceliğe sahip `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="5e048-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="5e048-110">Bir işlenen aynı önceliğe sahip iki işleç arasında gerçekleştiğinde *ilişkilendirilebilirliği* operatörleri işlemleri gerçekleştirilir sırasını denetler:</span><span class="sxs-lookup"><span data-stu-id="5e048-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="5e048-111">Atama işleçleri hariç tüm ikili işleçler şunlardır *ilişkilendirilebilir*, yani işlemler soldan sağa doğru gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5e048-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="5e048-112">Örneğin, `x + y + z` değerlendirmesinde `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="5e048-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="5e048-113">Atama işleçleri ve koşullu işleç (`?:`) olan *sağla ilişkilendirilebilir*, sağdan sola işlemler gerçekleştirilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5e048-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="5e048-114">Örneğin, `x = y = z` değerlendirmesinde `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="5e048-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="5e048-115">Öncelik ve ilişkisellik parantez kullanılarak denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5e048-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="5e048-116">Örneğin, `x + y * z` ilk çarpar `y` tarafından `z` ve ardından sonuca ekler `x`, ancak `(x + y) * z` ilk ekler `x` ve `y` ve sonucu çarpan `z`.</span><span class="sxs-lookup"><span data-stu-id="5e048-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="5e048-117">Çoğu işleçleri olabilir [ *aşırı*](../language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="5e048-117">Most operators can be [*overloaded*](../language-reference/keywords/operator.md).</span></span> <span data-ttu-id="5e048-118">İşleç aşırı yüklemesi, aşağıdakilerden birini veya her iki işlenen kullanıcı tanımlı sınıf veya yapı türü olduğu işlemlerinde belirtilmesi için kullanıcı tanımlı işleç uygulamalarına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5e048-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="5e048-119">C#birkaç gerçekleştirmek için işleçleri sağlar [aritmetik](../language-reference/operators/arithmetic-operators.md), [mantıksal](../language-reference/operators/boolean-logical-operators.md), [bit düzeyinde and -shift ile](../language-reference/operators/bitwise-and-shift-operators.md) işlemleri ve [eşitlik](../language-reference/operators/equality-operators.md) ve [sipariş](../language-reference/operators/comparison-operators.md) karşılaştırmalar.</span><span class="sxs-lookup"><span data-stu-id="5e048-119">C# provides a number of operators to perform [arithmetic](../language-reference/operators/arithmetic-operators.md), [logical](../language-reference/operators/boolean-logical-operators.md), [bitwise and shift](../language-reference/operators/bitwise-and-shift-operators.md) operations and [equality](../language-reference/operators/equality-operators.md) and [order](../language-reference/operators/comparison-operators.md) comparisons.</span></span>

<span data-ttu-id="5e048-120">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e048-120">For the complete list of C# operators ordered by precedence level, see [C# operators](../language-reference/operators/index.md).</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="5e048-121">[Önceki](types-and-variables.md)
> [İleri](statements.md)</span><span class="sxs-lookup"><span data-stu-id="5e048-121">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
