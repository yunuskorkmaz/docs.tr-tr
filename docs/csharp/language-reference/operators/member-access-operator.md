---
title: biçimindeki telefon numarasıdır. Operator - C# başvurusu
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689209"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ae90b-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae90b-103">.</span></span> <span data-ttu-id="ae90b-104">operator (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ae90b-104">operator (C# Reference)</span></span>

<span data-ttu-id="ae90b-105">Nokta `.`, genellikle üye erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae90b-105">The dot, `.`, is typically used for member access.</span></span>

<span data-ttu-id="ae90b-106">Kullandığınız `.` aşağıdaki örneklerde gösterildiği gibi bir ad alanı veya tür, üye erişim belirteci:</span><span class="sxs-lookup"><span data-stu-id="ae90b-106">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="ae90b-107">Kullanım `.` iç içe geçmiş ad alanı içinde bir ad alanı, aşağıdaki örnek olarak erişmek için bir [ `using` yönergesi](../keywords/using-directive.md) gösterir:</span><span class="sxs-lookup"><span data-stu-id="ae90b-107">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- <span data-ttu-id="ae90b-108">Kullanım `.` forma bir *tam adı* aşağıdaki kodun gösterdiği gibi bir ad alanı içinde bir tür erişmek için:</span><span class="sxs-lookup"><span data-stu-id="ae90b-108">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  <span data-ttu-id="ae90b-109">Kullanma [ `using` yönergesi](../keywords/using-directive.md) nitelenmiş adlar kullanımı isteğe bağlı yapmak için.</span><span class="sxs-lookup"><span data-stu-id="ae90b-109">Use the [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="ae90b-110">Kullanım `.` erişimi [üyelerini türü](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan, aşağıdaki kodun gösterdiği olarak:</span><span class="sxs-lookup"><span data-stu-id="ae90b-110">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

<span data-ttu-id="ae90b-111">Ayrıca `.` çağrılacak bir [genişletme yöntemi](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ae90b-111">You can also use `.` to invoke an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ae90b-112">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="ae90b-112">Operator overloadability</span></span>

<span data-ttu-id="ae90b-113">İşleç `.` aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="ae90b-113">The operator `.` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ae90b-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ae90b-114">C# language specification</span></span>

<span data-ttu-id="ae90b-115">Daha fazla bilgi için [üye erişimi](~/_csharplang/spec/expressions.md#member-access) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae90b-115">For more information, see the [Member access](~/_csharplang/spec/expressions.md#member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae90b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae90b-116">See also</span></span>

- [<span data-ttu-id="ae90b-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ae90b-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ae90b-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ae90b-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ae90b-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ae90b-119">C# Operators</span></span>](index.md)
- <span data-ttu-id="ae90b-120">[?. ve? [] işleçleri](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="ae90b-120">[?. and ?[] operators](null-conditional-operators.md)</span></span>