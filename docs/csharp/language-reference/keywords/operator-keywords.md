---
title: İşleç anahtar sözcükleri - C# başvurusu
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- keywords [C#], operators
- operators [C#], keywords
ms.assetid: f745c81f-f8d8-4673-86a1-0f3a85cc63c3
ms.openlocfilehash: e03e1c930b452cf5e4f2c4bb1d06d5363f20c991
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243616"
---
# <a name="operator-keywords-c-reference"></a><span data-ttu-id="40f43-102">İşleç Anahtar Sözcükleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="40f43-102">Operator Keywords (C# Reference)</span></span>

<span data-ttu-id="40f43-103">Bir tür boyutunu alma, bir nesnenin çalışma zamanı tür denetimi nesneleri oluşturma gibi çeşitli eylemler ve diğer işlemleri gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40f43-103">Used to perform miscellaneous actions such as creating objects, checking the run-time type of an object, obtaining the size of a type, and other actions.</span></span> <span data-ttu-id="40f43-104">Bu bölümde, aşağıdaki anahtar sözcükler sunar:</span><span class="sxs-lookup"><span data-stu-id="40f43-104">This section introduces the following keywords:</span></span>

- <span data-ttu-id="40f43-105">[olarak](as.md) nesneyi uyumlu bir türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="40f43-105">[as](as.md) Converts an object to a compatible type.</span></span>

- <span data-ttu-id="40f43-106">[await](await.md) Suspends bir [zaman uyumsuz](async.md) bir beklenen görev tamamlanana kadar yöntem.</span><span class="sxs-lookup"><span data-stu-id="40f43-106">[await](await.md) Suspends an [async](async.md) method until an awaited task is completed.</span></span>

- <span data-ttu-id="40f43-107">[olan](is.md) bir nesnenin çalışma zamanı türü denetler veya (başlayarak C# 7.0) belirli bir desene göre bir ifade eder.</span><span class="sxs-lookup"><span data-stu-id="40f43-107">[is](is.md) Checks the run-time type of an object, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

- [<span data-ttu-id="40f43-108">new</span><span class="sxs-lookup"><span data-stu-id="40f43-108">new</span></span>](new.md)

  - <span data-ttu-id="40f43-109">[New işleci](new-operator.md) nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40f43-109">[new Operator](new-operator.md) Creates objects.</span></span>

  - <span data-ttu-id="40f43-110">[New değiştiricisi](new-modifier.md) devralınmış bir üyeyi gizler.</span><span class="sxs-lookup"><span data-stu-id="40f43-110">[new Modifier](new-modifier.md) Hides an inherited member.</span></span>

  - <span data-ttu-id="40f43-111">[New kısıtlaması](new-constraint.md) bir tür parametresi niteliği taşır.</span><span class="sxs-lookup"><span data-stu-id="40f43-111">[new Constraint](new-constraint.md) Qualifies a type parameter.</span></span>

- <span data-ttu-id="40f43-112">[nameof](nameof.md) değişken, tür veya üyenin basit (nitelenmemiş) dize adını alır.</span><span class="sxs-lookup"><span data-stu-id="40f43-112">[nameof](nameof.md) Obtains the simple (unqualified) string name of a variable, type, or member.</span></span>

- <span data-ttu-id="40f43-113">[sizeof](sizeof.md) nespravovaným typem boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="40f43-113">[sizeof](sizeof.md) Obtains the size of an unmanaged type.</span></span>  

- <span data-ttu-id="40f43-114">[typeof](typeof.md) elde ediyor <xref:System.Type?displayProperty=nameWithType> nesne türü.</span><span class="sxs-lookup"><span data-stu-id="40f43-114">[typeof](typeof.md) Obtains the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span>  

- [<span data-ttu-id="40f43-115">true</span><span class="sxs-lookup"><span data-stu-id="40f43-115">true</span></span>](true.md)  

  - <span data-ttu-id="40f43-116">[true işleci](true-false-operators.md) döndürür [bool](bool.md) değer `true` işlenen kesinlikle doğru olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="40f43-116">[true Operator](true-false-operators.md) Returns the [bool](bool.md) value `true` to indicate that the operand is definitely true.</span></span>

  - <span data-ttu-id="40f43-117">[TRUE değişmez değeri](true-literal.md) temsil [bool](bool.md) değer `true`.</span><span class="sxs-lookup"><span data-stu-id="40f43-117">[true Literal](true-literal.md) Represents the [bool](bool.md) value `true`.</span></span>

- [<span data-ttu-id="40f43-118">false</span><span class="sxs-lookup"><span data-stu-id="40f43-118">false</span></span>](false.md)  

  - <span data-ttu-id="40f43-119">[false işleci](true-false-operators.md) döndürür [bool](bool.md) değer `true` işlenen kesinlikle false olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="40f43-119">[false Operator](true-false-operators.md) Returns the [bool](bool.md) value `true` to indicate that the operand is definitely false.</span></span>

  - <span data-ttu-id="40f43-120">[false değişmez değeri](false-literal.md) temsil [bool](bool.md) değer `false`.</span><span class="sxs-lookup"><span data-stu-id="40f43-120">[false Literal](false-literal.md) Represents the [bool](bool.md) value `false`.</span></span>

- <span data-ttu-id="40f43-121">[stackalloc](stackalloc.md) bir yığında bellek bloğu ayırır.</span><span class="sxs-lookup"><span data-stu-id="40f43-121">[stackalloc](stackalloc.md) Allocates a block of memory on the stack.</span></span>  

<span data-ttu-id="40f43-122">İşleçler ve deyimler olarak kullanılabilir, aşağıdaki anahtar sözcükler, ele alınmaktadır [deyimleri](statement-keywords.md) bölümü:</span><span class="sxs-lookup"><span data-stu-id="40f43-122">The following keywords, which can be used as operators and as statements, are covered in the [Statements](statement-keywords.md) section:</span></span>

- <span data-ttu-id="40f43-123">[işaretli](checked.md) içerik teslim belirtir.</span><span class="sxs-lookup"><span data-stu-id="40f43-123">[checked](checked.md) Specifies checked context.</span></span>  

- <span data-ttu-id="40f43-124">[denetlenmeyen](unchecked.md) denetlenmeyen bağlam belirtir.</span><span class="sxs-lookup"><span data-stu-id="40f43-124">[unchecked](unchecked.md) Specifies unchecked context.</span></span>  

## <a name="see-also"></a><span data-ttu-id="40f43-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40f43-125">See also</span></span>

- [<span data-ttu-id="40f43-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="40f43-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="40f43-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="40f43-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="40f43-128">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="40f43-128">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="40f43-129">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="40f43-129">C# Operators</span></span>](../operators/index.md)
