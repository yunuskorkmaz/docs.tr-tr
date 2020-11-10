---
title: WITH ifadesi-C# başvurusu
description: C# kayıtlarını bozucu olmayan bir şekilde gerçekleştiren bir ifade hakkında bilgi edinin
ms.date: 11/10/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: 7948df3c6260e297cdb2fa380f1790a55e0abb58
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445820"
---
# <a name="with-expression-c-reference"></a><span data-ttu-id="ccd10-103">With ifadesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ccd10-103">with expression (C# reference)</span></span>

<span data-ttu-id="ccd10-104">C# 9,0 ve üzeri sürümlerde kullanılabilen bir `with` ifade, belirtilen özellikler ve alanlarla birlikte [kayıt](../../whats-new/csharp-9.md#record-types) işleneninin bir kopyasını oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ccd10-104">Available in C# 9.0 and later, a `with` expression produces a copy of its [record](../../whats-new/csharp-9.md#record-types) operand with the specified properties and fields modified:</span></span>

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

<span data-ttu-id="ccd10-105">Yukarıdaki örnekte gösterildiği gibi, hangi üyelerin değiştirileceğini ve bunların yeni değerlerini belirtmek için [nesne Başlatıcısı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) sözdizimini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ccd10-105">As the preceding example shows, you use [object initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) syntax to specify what members to modify and their new values.</span></span> <span data-ttu-id="ccd10-106">Bir `with` ifadede, sol taraftaki bir işlenen bir kayıt türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccd10-106">In a `with` expression, a left-hand operand must be of a record type.</span></span>

<span data-ttu-id="ccd10-107">Bir başvuru türü üyesi olması durumunda, bir kayıt kopyalanırken yalnızca bir örneğe başvuru kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="ccd10-107">In case of a reference-type member, only the reference to an instance is copied when a record is copied.</span></span> <span data-ttu-id="ccd10-108">Hem kopya hem de özgün kaydın aynı başvuru türü örneğine erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="ccd10-108">Both the copy and original record have access to the same reference-type instance.</span></span> <span data-ttu-id="ccd10-109">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ccd10-109">The following example demonstrates that behavior:</span></span>

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

<span data-ttu-id="ccd10-110">Herhangi bir kayıt türünün *kopya Oluşturucusu* vardır.</span><span class="sxs-lookup"><span data-stu-id="ccd10-110">Any record type has the *copy constructor*.</span></span> <span data-ttu-id="ccd10-111">Bu, kapsayan kayıt türünde tek bir parametreye sahip bir oluşturucudur.</span><span class="sxs-lookup"><span data-stu-id="ccd10-111">That is a constructor with a single parameter of the containing record type.</span></span> <span data-ttu-id="ccd10-112">Bağımsız değişkeninin durumunu yeni bir kayıt örneğine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="ccd10-112">It copies the state of its argument to a new record instance.</span></span> <span data-ttu-id="ccd10-113">Bir ifadenin değerlendirmesi sırasında `with` , kopya Oluşturucu, orijinal bir kayda göre yeni bir kayıt örneği oluşturmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="ccd10-113">At evaluation of a `with` expression, the copy constructor gets called to instantiate a new record instance based on an original record.</span></span> <span data-ttu-id="ccd10-114">Bundan sonra yeni örnek, belirtilen değişikliklere göre güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ccd10-114">After that, the new instance gets updated according to the specified modifications.</span></span> <span data-ttu-id="ccd10-115">Varsayılan olarak, kopya Oluşturucu örtük, diğer bir deyişle, derleyici tarafından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ccd10-115">By default, the copy constructor is implicit, that is, compiler-generated.</span></span> <span data-ttu-id="ccd10-116">Kayıt kopyalama semantiğini özelleştirmeniz gerekiyorsa, istenen davranışla birlikte açıkça bir kopya Oluşturucu bildirin.</span><span class="sxs-lookup"><span data-stu-id="ccd10-116">If you need to customize the record copy semantics, explicitly declare a copy constructor with the desired behavior.</span></span> <span data-ttu-id="ccd10-117">Aşağıdaki örnek, önceki örneği açık bir kopya Oluşturucusu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="ccd10-117">The following example updates the preceding example with an explicit copy constructor.</span></span> <span data-ttu-id="ccd10-118">Yeni kopyalama davranışı, bir kayıt kopyalanırken liste başvurusu yerine liste öğelerini kopyalamadır:</span><span class="sxs-lookup"><span data-stu-id="ccd10-118">The new copy behavior is to copy list items instead of a list reference when a record is copied:</span></span>

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a><span data-ttu-id="ccd10-119">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ccd10-119">C# language specification</span></span>

<span data-ttu-id="ccd10-120">Daha fazla bilgi için, [kayıtlar Özellik teklifi notunun](~/_csharplang/proposals/csharp-9.0/records.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="ccd10-120">For more information, see the following sections of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md):</span></span>

- [<span data-ttu-id="ccd10-121">`with` ifadesini</span><span class="sxs-lookup"><span data-stu-id="ccd10-121">`with` expression</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [<span data-ttu-id="ccd10-122">Üyeleri Kopyala ve Kopyala</span><span class="sxs-lookup"><span data-stu-id="ccd10-122">Copy and Clone members</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a><span data-ttu-id="ccd10-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccd10-123">See also</span></span>

- [<span data-ttu-id="ccd10-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ccd10-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ccd10-125">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ccd10-125">C# operators and expressions</span></span>](index.md)
