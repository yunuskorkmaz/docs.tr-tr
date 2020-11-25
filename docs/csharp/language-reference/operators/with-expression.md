---
title: WITH ifadesi-C# başvurusu
description: C# kayıtlarını bozucu olmayan bir şekilde gerçekleştiren bir ifade hakkında bilgi edinin
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: d7d3758c8c5da7859974b5b50b63d2a5ca16b24d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702231"
---
# <a name="with-expression-c-reference"></a><span data-ttu-id="8bf7e-103">With ifadesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8bf7e-103">with expression (C# reference)</span></span>

<span data-ttu-id="8bf7e-104">C# 9,0 ve üzeri sürümlerde kullanılabilen bir `with` ifade, belirtilen özellikler ve alanlarla birlikte [kayıt](../../whats-new/csharp-9.md#record-types) işleneninin bir kopyasını oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8bf7e-104">Available in C# 9.0 and later, a `with` expression produces a copy of its [record](../../whats-new/csharp-9.md#record-types) operand with the specified properties and fields modified:</span></span>

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

<span data-ttu-id="8bf7e-105">Yukarıdaki örnekte gösterildiği gibi, hangi üyelerin değiştirileceğini ve bunların yeni değerlerini belirtmek için [nesne Başlatıcısı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) sözdizimini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-105">As the preceding example shows, you use [object initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) syntax to specify what members to modify and their new values.</span></span> <span data-ttu-id="8bf7e-106">Bir `with` ifadede, sol taraftaki bir işlenen bir kayıt türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-106">In a `with` expression, a left-hand operand must be of a record type.</span></span>

<span data-ttu-id="8bf7e-107">`with`Aşağıdaki örnekte gösterildiği gibi bir ifadenin sonucu, ifadenin işleneni ile aynı çalışma zamanı türüne sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8bf7e-107">The result of a `with` expression has the same runtime type as the expression's operand, as the following example shows:</span></span>

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

<span data-ttu-id="8bf7e-108">Bir başvuru türü üyesi söz konusu olduğunda, bir kayıt kopyalanırken yalnızca bir örneğe başvuru kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-108">In the case of a reference-type member, only the reference to an instance is copied when a record is copied.</span></span> <span data-ttu-id="8bf7e-109">Hem kopya hem de özgün kaydın aynı başvuru türü örneğine erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-109">Both the copy and original record have access to the same reference-type instance.</span></span> <span data-ttu-id="8bf7e-110">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8bf7e-110">The following example demonstrates that behavior:</span></span>

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

<span data-ttu-id="8bf7e-111">Herhangi bir kayıt türünün *kopya Oluşturucusu* vardır.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-111">Any record type has the *copy constructor*.</span></span> <span data-ttu-id="8bf7e-112">Bu, kapsayan kayıt türünde tek bir parametreye sahip bir oluşturucudur.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-112">That is a constructor with a single parameter of the containing record type.</span></span> <span data-ttu-id="8bf7e-113">Bağımsız değişkeninin durumunu yeni bir kayıt örneğine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-113">It copies the state of its argument to a new record instance.</span></span> <span data-ttu-id="8bf7e-114">Bir ifadenin değerlendirmesi sırasında `with` , kopya Oluşturucu, orijinal bir kayda göre yeni bir kayıt örneği oluşturmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-114">At evaluation of a `with` expression, the copy constructor gets called to instantiate a new record instance based on an original record.</span></span> <span data-ttu-id="8bf7e-115">Bundan sonra yeni örnek, belirtilen değişikliklere göre güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-115">After that, the new instance gets updated according to the specified modifications.</span></span> <span data-ttu-id="8bf7e-116">Varsayılan olarak, kopya Oluşturucu örtük, diğer bir deyişle, derleyici tarafından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-116">By default, the copy constructor is implicit, that is, compiler-generated.</span></span> <span data-ttu-id="8bf7e-117">Kayıt kopyalama semantiğini özelleştirmeniz gerekiyorsa, istenen davranışla birlikte açıkça bir kopya Oluşturucu bildirin.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-117">If you need to customize the record copy semantics, explicitly declare a copy constructor with the desired behavior.</span></span> <span data-ttu-id="8bf7e-118">Aşağıdaki örnek, önceki örneği açık bir kopya Oluşturucusu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-118">The following example updates the preceding example with an explicit copy constructor.</span></span> <span data-ttu-id="8bf7e-119">Yeni kopyalama davranışı, bir kayıt kopyalanırken liste başvurusu yerine liste öğelerini kopyalamadır:</span><span class="sxs-lookup"><span data-stu-id="8bf7e-119">The new copy behavior is to copy list items instead of a list reference when a record is copied:</span></span>

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a><span data-ttu-id="8bf7e-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8bf7e-120">C# language specification</span></span>

<span data-ttu-id="8bf7e-121">Daha fazla bilgi için, [kayıtlar Özellik teklifi notunun](~/_csharplang/proposals/csharp-9.0/records.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="8bf7e-121">For more information, see the following sections of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md):</span></span>

- [<span data-ttu-id="8bf7e-122">`with` ifadesini</span><span class="sxs-lookup"><span data-stu-id="8bf7e-122">`with` expression</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [<span data-ttu-id="8bf7e-123">Üyeleri Kopyala ve Kopyala</span><span class="sxs-lookup"><span data-stu-id="8bf7e-123">Copy and Clone members</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a><span data-ttu-id="8bf7e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bf7e-124">See also</span></span>

- [<span data-ttu-id="8bf7e-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8bf7e-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8bf7e-126">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="8bf7e-126">C# operators and expressions</span></span>](index.md)
