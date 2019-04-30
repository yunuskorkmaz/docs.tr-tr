---
title: C# 7.2 yenilikleri
description: C# 7.2 yenilikleri genel bakış.
ms.date: 08/16/2017
ms.openlocfilehash: b8b2be68aac3cba92e0dbd74dfe4ee3cbbef0e88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706097"
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="ab73c-103">C# 7.2 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="ab73c-103">What's new in C# 7.2</span></span>

<span data-ttu-id="ab73c-104">C# 7.2 birçok yararlı özellik ekleyen başka bir noktası sürümdür.</span><span class="sxs-lookup"><span data-stu-id="ab73c-104">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="ab73c-105">Bu sürüm için bir tema, gereksiz kopyalarını veya ayırmaları önleyerek değer türleri ile daha verimli bir şekilde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="ab73c-105">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span>

<span data-ttu-id="ab73c-106">Geri kalan özellikleri, küçük, iyi sahip özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="ab73c-106">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="ab73c-107">C# 7.2 kullanan [dil sürüm seçimi](../language-reference/configure-language-version.md) derleyici dil sürüm seçmek için yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ab73c-107">C# 7.2 uses the [language version selection](../language-reference/configure-language-version.md) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="ab73c-108">Bu sürümdeki yeni diz özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ab73c-108">The new language features in this release are:</span></span>

* [<span data-ttu-id="ab73c-109">Güvenli verimli kod yazmak için teknikleri</span><span class="sxs-lookup"><span data-stu-id="ab73c-109">Techniques for writing safe efficient code</span></span>](#safe-efficient-code-enhancements)
  - <span data-ttu-id="ab73c-110">Başvuru semantiği kullanarak değer türleri ile çalışmayı etkinleştirmek söz dizimi geliştirmeleri birleşimi.</span><span class="sxs-lookup"><span data-stu-id="ab73c-110">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="ab73c-111">Girintili olmayan adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ab73c-111">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="ab73c-112">Adlandırılmış bağımsız değişkenler konumsal bağımsız değişken tarafından izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ab73c-112">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="ab73c-113">Sayısal sabit değerlerde önde gelen altçizgilere</span><span class="sxs-lookup"><span data-stu-id="ab73c-113">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="ab73c-114">Artık sayısal değişmez değerler yazdırılan herhangi bir rakam önce önde gelen altçizgilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ab73c-114">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="ab73c-115">`private protected` Erişim değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="ab73c-115">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="ab73c-116">`private protected` Erişim değiştiricisi, aynı derlemedeki türetilmiş sınıflar için erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab73c-116">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>
* [<span data-ttu-id="ab73c-117">Koşullu `ref` ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ab73c-117">Conditional `ref` expressions</span></span>](#conditional-ref-expressions)
  - <span data-ttu-id="ab73c-118">Koşullu ifadenin sonucu (`?:`) artık bir başvuru olabilir.</span><span class="sxs-lookup"><span data-stu-id="ab73c-118">The result of a conditional expression (`?:`) can now be a reference.</span></span>

## <a name="safe-efficient-code-enhancements"></a><span data-ttu-id="ab73c-119">Güvenli verimli kod geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="ab73c-119">Safe efficient code enhancements</span></span>

<span data-ttu-id="ab73c-120">Tanıtılan 7.2 dil özellikleri, değer türleri ile başvuru semantiği kullanırken çalışmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ab73c-120">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="ab73c-121">Kopyalama değer türleri başvuru türleri kullanmayla ilişkili bellek ayırmaları ödemeden en aza indirerek, performansı artırmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ab73c-121">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="ab73c-122">Özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ab73c-122">The features include:</span></span>

- <span data-ttu-id="ab73c-123">`in` Değiştirici bağımsız değişken başvuruyla geçirildi ancak tarafından çağrılan yöntem değiştirilmemiş belirtmek için parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ab73c-123">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span> <span data-ttu-id="ab73c-124">Ekleme `in` değiştiricisi bir bağımsız değişken için bir [kaynağı uyumlu değişiklik](version-update-considerations.md#source-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="ab73c-124">Adding the `in` modifier to an argument is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span>
- <span data-ttu-id="ab73c-125">`ref readonly` Değiştirici yöntemi döndüğünde, bir yöntem değerine başvuru ile döndürülen ancak bu nesne için yazma izin vermez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="ab73c-125">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span> <span data-ttu-id="ab73c-126">Ekleme `ref readonly` değiştiricisi bir [kaynağı uyumlu değişiklik](version-update-considerations.md#source-compatible-changes), dönüş için bir değer atanır.</span><span class="sxs-lookup"><span data-stu-id="ab73c-126">Adding the `ref readonly` modifier is a [source compatible change](version-update-considerations.md#source-compatible-changes), if the return is assigned to a value.</span></span> <span data-ttu-id="ab73c-127">Ekleme `readonly` değiştirici mevcut bir `ref` dönüş deyimi bir [uyumsuz değişiklik](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="ab73c-127">Adding the `readonly` modifier to an existing `ref` return statement is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="ab73c-128">Bildirimi güncelleştirmek çağıranlar gerektirir `ref` eklemek için yerel değişkenleri `readonly` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="ab73c-128">It requires callers to update the declaration of `ref` local variables to include the `readonly` modifier.</span></span>
- <span data-ttu-id="ab73c-129">`readonly struct` Yapı sabittir ve olarak geçirilmelidir belirtmek için bildirimi bir `in` üye yöntemlerinin parametre.</span><span class="sxs-lookup"><span data-stu-id="ab73c-129">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span> <span data-ttu-id="ab73c-130">Ekleme `readonly` değiştiricisi var olan bir yapı bildirim için bir [ikili uyumlu değişiklik](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="ab73c-130">Adding the `readonly` modifier to an existing struct declaration is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>
- <span data-ttu-id="ab73c-131">`ref struct` Bildirimi, bir yapı türü yönetilen bellek doğrudan erişir ve her zaman yığını ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab73c-131">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span> <span data-ttu-id="ab73c-132">Ekleme `ref` değiştirici mevcut bir `struct` bildirimi bir [uyumsuz değişiklik](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="ab73c-132">Adding the `ref` modifier to an existing `struct` declaration is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="ab73c-133">A `ref struct` bunu ayrıldığı yığında diğer konumlarda kullanılan veya bir sınıf üyesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="ab73c-133">A `ref struct` cannot be a member of a class or used in other locations where it may be allocated on the heap.</span></span>

<span data-ttu-id="ab73c-134">Tüm bunlar hakkında daha fazla değişiklikler okuyabilirsiniz [güvenli verimli kod yazma](../write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="ab73c-134">You can read more about all these changes in [Write safe efficient code](../write-safe-efficient-code.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="ab73c-135">Girintili olmayan adlandırılmış bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ab73c-135">Non-trailing named arguments</span></span>

<span data-ttu-id="ab73c-136">Yöntem çağrıları artık bu adlandırılmış bağımsız değişkenler doğru konumda olduğunda, önünde konumsal bağımsız değişkenler adlandırılmış bağımsız değişkenler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab73c-136">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="ab73c-137">Daha fazla bilgi için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="ab73c-137">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="ab73c-138">Sayısal sabit değerlerde önde gelen altçizgilere</span><span class="sxs-lookup"><span data-stu-id="ab73c-138">Leading underscores in numeric literals</span></span>

<span data-ttu-id="ab73c-139">Rakam ayırıcıları C# 7.0 desteği uygulamasına izin vermedi `_` değişmez değerin ilk karakteri olarak.</span><span class="sxs-lookup"><span data-stu-id="ab73c-139">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="ab73c-140">Onaltılık ve ikili sayısal değişmez değerler artık ile başlayan bir `_`.</span><span class="sxs-lookup"><span data-stu-id="ab73c-140">Hex and binary numeric literals may now begin with an `_`.</span></span>

<span data-ttu-id="ab73c-141">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ab73c-141">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a><span data-ttu-id="ab73c-142">_Özel korumalı_ erişim değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="ab73c-142">_private protected_ access modifier</span></span>

<span data-ttu-id="ab73c-143">Yeni bir bileşik erişim değiştiricisi: `private protected` üye sınıfı veya aynı derlemede bildirilmiş türetilmiş sınıfları içeren tarafından erişilebilecek gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab73c-143">A new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="ab73c-144">Sırada `protected internal` türetilmiş sınıflar veya aynı derlemede bulunan sınıflar tarafından erişime `private protected` türetilen türlerin aynı derlemede bildirilmiş erişimi sınırlar.</span><span class="sxs-lookup"><span data-stu-id="ab73c-144">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="ab73c-145">Daha fazla bilgi için [erişim değiştiricilerine](../language-reference/keywords/access-modifiers.md) dil başvurusu.</span><span class="sxs-lookup"><span data-stu-id="ab73c-145">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

## <a name="conditional-ref-expressions"></a><span data-ttu-id="ab73c-146">Koşullu `ref` ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ab73c-146">Conditional `ref` expressions</span></span>

<span data-ttu-id="ab73c-147">Son olarak, koşullu ifade bir değer sonuç yerine bir başvuru sonuç üretebilir.</span><span class="sxs-lookup"><span data-stu-id="ab73c-147">Finally, the conditional expression may produce a ref result instead of a value result.</span></span> <span data-ttu-id="ab73c-148">Örneğin, bir iki dizinin içindeki ilk öğeye bir başvuru almak için aşağıdaki yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="ab73c-148">For example, you would write the following to retrieve a reference to the first element in one of two arrays:</span></span>

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

<span data-ttu-id="ab73c-149">Değişken `r` ilk değeri ya da bir başvurudur `arr` veya `otherArr`.</span><span class="sxs-lookup"><span data-stu-id="ab73c-149">The variable `r` is a reference to the first value in either `arr` or `otherArr`.</span></span>

<span data-ttu-id="ab73c-150">Daha fazla bilgi için [koşullu işleç (?:) ](../language-reference/operators/conditional-operator.md) dil başvurusu.</span><span class="sxs-lookup"><span data-stu-id="ab73c-150">For more information, see [conditional operator (?:)](../language-reference/operators/conditional-operator.md) in the language reference.</span></span>
