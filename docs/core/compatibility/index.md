---
title: Son değişiklik türleri
description: .NET Core 'un .NET sürümlerindeki geliştiriciler için uyumluluk denemelerini ve ne tür bir değişikliğin Son değişiklik olduğunu öğrenin.
ms.date: 06/10/2019
ms.openlocfilehash: bc93316141ae99d8cfedc5e6d88a9e91216f9c6e
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415751"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="bf40e-103">Uyumluluğu etkileyen değişiklikler</span><span class="sxs-lookup"><span data-stu-id="bf40e-103">Changes that affect compatibility</span></span>

<span data-ttu-id="bf40e-104">.NET, geçmişi boyunca sürümden sürüme ve .NET 'in özellikleri arasında yüksek düzeyde uyumluluk tutmaya çalıştı.</span><span class="sxs-lookup"><span data-stu-id="bf40e-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="bf40e-105">Bu, .NET Core için doğru olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="bf40e-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="bf40e-106">.NET Core, .NET Framework bağımsız olan yeni bir teknoloji olarak düşünülebilir, ancak iki ana etken .NET Core 'un .NET Framework arasında sınırsız olmasına izin verebilir:</span><span class="sxs-lookup"><span data-stu-id="bf40e-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="bf40e-107">Asıl olarak çok sayıda geliştirici geliştirmiş veya .NET Framework uygulamaları geliştirmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="bf40e-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="bf40e-108">.NET uygulamalarında tutarlı davranış beklentilerine sahip olurlar.</span><span class="sxs-lookup"><span data-stu-id="bf40e-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="bf40e-109">.NET Standard kitaplık projeleri, geliştiricilerin .NET Core ve .NET Framework tarafından paylaşılan ortak API 'Leri hedefleyen kitaplıklar oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="bf40e-110">Geliştiriciler .NET Core uygulamasında kullanılan bir kitaplığın, .NET Framework uygulamasında kullanılan aynı kitaplıkla aynı şekilde davranmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="bf40e-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="bf40e-111">Geliştiriciler .NET uygulamaları genelinde uyumlulukla birlikte .NET Core sürümleri arasında yüksek düzeyde uyumluluk bekler.</span><span class="sxs-lookup"><span data-stu-id="bf40e-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="bf40e-112">Özellikle .NET Core 'un önceki bir sürümü için yazılan kod, daha sonraki bir .NET Core sürümünde sorunsuz çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="bf40e-113">Aslında birçok geliştirici, .NET Core 'un yeni yayımlanmış sürümlerinde bulunan yeni API 'Lerin, bu API 'Lerin tanıtıldıkları yayın öncesi sürümlerle de uyumlu olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="bf40e-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="bf40e-114">Bu makalede, uyumluluğu etkileyen değişiklikler ve .NET ekibinin her tür değişikliği değerlendirme yöntemi özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-114">This article outlines changes that affect compatibility and the way in which the .NET team evaluates each type of change.</span></span> <span data-ttu-id="bf40e-115">.NET ekibinin olası son değişikliklere nasıl yaklaşılacağını anlamak, [mevcut .NET API](https://github.com/dotnet/runtime)'lerinin davranışını değiştiren çekme isteklerini açan geliştiriciler için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests that modify the behavior of [existing .NET APIs](https://github.com/dotnet/runtime).</span></span>

<span data-ttu-id="bf40e-116">Aşağıdaki bölümlerde, .NET Core API 'Lerinde yapılan değişikliklerin kategorileri ve bunların uygulama uyumluluğuyla ilgili bir etkisi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-116">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="bf40e-117">Değişikliklere izin verilmez ✔️, izin verilmiyor ❌ veya karartan ve önceden tahmin edilebilir, belirgin ve tutarlı bir değerlendirme, önceki davranışın ❓.</span><span class="sxs-lookup"><span data-stu-id="bf40e-117">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="bf40e-118">.NET kitaplıklarında yapılan değişikliklerin nasıl değerlendirildiğini gösteren bir kılavuz olarak, kitaplık geliştiricileri de bu ölçütleri kullanarak birden çok .NET uygulaması ve sürümü hedefleyen kitaplıklarında yapılan değişiklikleri değerlendirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-118">In addition to serving as a guide to how changes to .NET libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>
> - <span data-ttu-id="bf40e-119">Uyumluluk kategorileri hakkında daha fazla bilgi için, bkz. [Uyumluluk](categories.md), ileri ve geri uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="bf40e-119">For information about the compatibility categories, for example, forward and backwards compatibility, see [Compatibility](categories.md).</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="bf40e-120">Ortak Sözleşmede yapılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="bf40e-120">Modifications to the public contract</span></span>

<span data-ttu-id="bf40e-121">Bu kategorideki değişiklikler bir türün genel yüzey alanını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="bf40e-122">Bu kategorideki değişikliklerden büyük bir olasılıkla, *geriye dönük uyumluluğu* ihlal etdiklerinden (API 'nin önceki bir sürümü ile geliştirilen bir uygulamanın daha sonraki bir sürümde yeniden derleme olmadan yürütülmesi için geliştirilmiş bir uygulama özelliği) izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="bf40e-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="bf40e-123">Türler</span><span class="sxs-lookup"><span data-stu-id="bf40e-123">Types</span></span>

- <span data-ttu-id="bf40e-124">✔️ **Izin verildi: arabirim bir temel tür tarafından zaten uygulandığında bir türden arabirim uygulamasını kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="bf40e-125">❓, **Bir türe yeni bir arabirim uygulama ekleme konusunda Yargıduyuyor.**</span><span class="sxs-lookup"><span data-stu-id="bf40e-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="bf40e-126">Bu, mevcut istemcileri olumsuz etkilemediğinden, kabul edilebilir bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="bf40e-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="bf40e-127">Yeni uygulamanın kabul edilebilir olarak kalması için, bu türdeki tüm değişiklikler burada tanımlanan kabul edilebilir değişiklik sınırları içinde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="bf40e-128">Bir tasarımcının veya seri hale getiricinin alt düzey tüketilemeyecek kod veya veri oluşturma yeteneğini doğrudan etkileyen arabirimler eklenirken aşırı dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="bf40e-129">Arabirim bir örnektir <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="bf40e-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="bf40e-130">❓, **Yeni bir temel sınıf tanıtımı gerekir**</span><span class="sxs-lookup"><span data-stu-id="bf40e-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="bf40e-131">Bir tür, yeni bir [soyut](../../csharp/language-reference/keywords/abstract.md) üye sunmaz veya var olan türlerin semantiğini ya da davranışını değiştirmek değilse, iki mevcut tür arasında bir hiyerarşiye tanıtılamaz.</span><span class="sxs-lookup"><span data-stu-id="bf40e-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="bf40e-132">Örneğin, .NET Framework 2,0 ' de, <xref:System.Data.Common.DbConnection> sınıfı <xref:System.Data.SqlClient.SqlConnection> daha önce doğrudan öğesinden türetilmiş olan için yeni bir temel sınıf haline geldi <xref:System.ComponentModel.Component> .</span><span class="sxs-lookup"><span data-stu-id="bf40e-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="bf40e-133">✔️ **Izin verildi: bir tür bir derlemeden diğerine taşınıyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="bf40e-134">*Eski* derlemenin, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> yeni derlemeye işaret eden ile işaretlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="bf40e-135">✔️ **Izin verildi: bir [Yapı](../../csharp/language-reference/builtin-types/struct.md) türünü `readonly struct` tür olarak değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="bf40e-136">Tür türüne değiştirme `readonly struct` `struct` yapılmasına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="bf40e-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="bf40e-137">✔️ **Izin verildi: *erişilebilir* (genel veya korumalı) oluşturucular olmadığında bir türe [Sealed](../../csharp/language-reference/keywords/sealed.md) veya [abstract](../../csharp/language-reference/keywords/abstract.md) anahtar sözcüğünü ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="bf40e-138">✔️ **Izin verildi: bir türün görünürlüğünü genişletme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="bf40e-139">❌**Izin verilmiyor: bir türün ad alanını veya adını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="bf40e-140">❌**Izin verilmiyor: ortak bir türü yeniden adlandırma veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="bf40e-141">Bu, yeniden adlandırılan veya kaldırılan türü kullanan tüm kodları keser.</span><span class="sxs-lookup"><span data-stu-id="bf40e-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="bf40e-142">❌**Izin verilmiyor: bir numaralandırmanın temel alınan türünü değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="bf40e-143">Bu bir derleme zamanı ve davranışsız değişiklik ve öznitelik bağımsız değişkenlerini ayrıştırılabilir hale getirmek için ikili bir değişiklik de yapar.</span><span class="sxs-lookup"><span data-stu-id="bf40e-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="bf40e-144">❌**Izin verilmiyor: daha önce korumasız bir tür mühürleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="bf40e-145">❌**Izin verilmiyor: bir arabirimin temel türleri kümesine arabirim ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="bf40e-146">Bir arabirim daha önce uygulanmayan bir arabirim uygularsa, arabirimin orijinal sürümünü uygulayan tüm türler bozulur.</span><span class="sxs-lookup"><span data-stu-id="bf40e-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="bf40e-147">❓, **Bir sınıfı temel sınıflar kümesinden veya uygulanan arabirimler kümesinden bir arabirimden kaldırmak istiyor.**</span><span class="sxs-lookup"><span data-stu-id="bf40e-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="bf40e-148">Arabirim kaldırma kuralı için bir özel durum vardır: kaldırılan arabirimden türetilen bir arabirimin uygulamasını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf40e-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="bf40e-149">Örneğin, <xref:System.IDisposable> türü veya arabirimi ' nin uyguladığı bir şekilde, öğesini kaldırabilirsiniz <xref:System.ComponentModel.IComponent> <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="bf40e-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="bf40e-150">❌**Izin verilmiyor: bir `readonly struct` türü [struct](../../csharp/language-reference/builtin-types/struct.md) türü olarak değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="bf40e-151">Ancak bir tür için bir türe `struct` yapılan değişikliğe `readonly struct` izin verilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="bf40e-152">❌**Izin verilmiyor: bir [Yapı](../../csharp/language-reference/builtin-types/struct.md) türünü tür olarak değiştirme `ref struct` ve tam tersi**</span><span class="sxs-lookup"><span data-stu-id="bf40e-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="bf40e-153">❌**Izin verilmiyor: bir türün görünürlüğünü azaltma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="bf40e-154">Ancak, bir türün görünürlüğünü artırmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="bf40e-155">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf40e-155">Members</span></span>

- <span data-ttu-id="bf40e-156">✔️ **Izin verildi: [sanal](../../csharp/language-reference/keywords/sealed.md) olmayan bir üyenin görünürlüğünü genişletme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="bf40e-157">✔️ \*\*Izin verildi: bir soyut üyeyi, *erişilebilir* (genel veya korumalı) oluşturuculara sahip olmayan bir ortak türe ekleme veya tür [mühürlü](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="bf40e-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="bf40e-158">Ancak, erişilebilir (genel veya korumalı) oluşturuculara sahip bir türe soyut üye eklenmesine `sealed` izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="bf40e-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="bf40e-159">✔️ **Izin verildi: tür erişilebilir olmayan (ortak veya korumalı) oluşturuculara veya tür [korumalı](../../csharp/language-reference/keywords/sealed.md) olduğunda [korumalı](../../csharp/language-reference/keywords/protected.md) bir üyenin görünürlüğünü kısıtlama**</span><span class="sxs-lookup"><span data-stu-id="bf40e-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="bf40e-160">✔️ **Izin verildi: bir üyeyi hiyerarşide daha yüksek bir sınıfa, onun kaldırıldığı türden daha yukarıya taşıma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="bf40e-161">✔️ **Izin verilen: bir geçersiz kılma ekleme veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="bf40e-162">Bir geçersiz kılma ile tanışın, önceki tüketicilere [taban](../../csharp/language-reference/keywords/base.md)çağrılırken geçersiz kılma üzerinde atlama yapılmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="bf40e-163">✔️ **Izin verildi: sınıfın daha önce Oluşturucusu yoksa, bir sınıfa Oluşturucu Ekleme, parametresiz bir oluşturucuyla birlikte**</span><span class="sxs-lookup"><span data-stu-id="bf40e-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="bf40e-164">Ancak, parametresiz oluşturucuyu eklemeden daha önceden hiç oluşturucuya *sahip olmayan bir* sınıfa bir Oluşturucu eklemeye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="bf40e-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="bf40e-165">✔️ **Izin verildi: bir üyeyi [soyut](../../csharp/language-reference/keywords/abstract.md) Iken [sanal](../../csharp/language-reference/keywords/virtual.md) olarak değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="bf40e-166">✔️ **Izin verildi: bir `ref readonly` `ref` dönüş değerine değiştirme (sanal yöntemler veya arabirimler hariç)**</span><span class="sxs-lookup"><span data-stu-id="bf40e-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="bf40e-167">✔️ **Izin verildi: alanın statik türü kesilebilir değer türünde değilse, bir alandan [ReadOnly](../../csharp/language-reference/keywords/readonly.md) öğesini kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="bf40e-168">✔️ **Izin verildi: daha önce tanımlanmayan yeni bir olay çağrılıyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="bf40e-169">❓, **Bir türe yeni bir örnek alanı ekleme konusunda Yargıduyuyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="bf40e-170">Bu değişiklik Serileştirmeyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="bf40e-170">This change impacts serialization.</span></span>

- <span data-ttu-id="bf40e-171">❌**Izin verilmiyor: ortak bir üyeyi veya parametreyi yeniden adlandırma veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="bf40e-172">Bu, yeniden adlandırılan veya kaldırılan üyeyi veya parametreyi kullanan tüm kodları keser.</span><span class="sxs-lookup"><span data-stu-id="bf40e-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="bf40e-173">Bu, bir alıcı veya ayarlayıcının bir özellikten kaldırılmasını veya yeniden adlandırılmasını, ayrıca sabit listesi üyelerini yeniden adlandırmayı veya kaldırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="bf40e-174">❌**Izin verilmiyor: arabirime üye ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="bf40e-175">❌**Izin verilmiyor: bir genel sabit veya numaralandırma üyesinin değerini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="bf40e-176">❌**Izin verilmiyor: bir özelliğin, alanın, parametrenin veya dönüş değerinin türünü değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="bf40e-177">❌**Izin verilmiyor: parametre sırasını ekleme, kaldırma veya değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="bf40e-178">❌**Izin verilmiyor: bir parametreden [ın](../../csharp/language-reference/keywords/in.md), [Out](../../csharp/language-reference/keywords/out.md) veya [ref](../../csharp/language-reference/keywords/ref.md) anahtar sözcüğünü ekleme veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="bf40e-179">❌**Izin verilmiyor: bir parametreyi yeniden adlandırma (büyük küçük harf değişikliği dahil)**</span><span class="sxs-lookup"><span data-stu-id="bf40e-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="bf40e-180">Bunun iki nedenden dolayı bölünmesi kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="bf40e-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="bf40e-181">C# ' de Visual Basic ve [Dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) ' deki geç bağlama özelliği gibi geç bağlantılı senaryoları keser.</span><span class="sxs-lookup"><span data-stu-id="bf40e-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="bf40e-182">Geliştiriciler [adlandırılmış bağımsız değişkenler](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)kullandıklarında [kaynak uyumluluğunu](categories.md#source-compatibility) keser.</span><span class="sxs-lookup"><span data-stu-id="bf40e-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="bf40e-183">❌**Izin verilmiyor: `ref` dönüş değerinden `ref readonly` dönüş değerine değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="bf40e-184">❌️**Izin verilmiyor: bir `ref readonly` `ref` sanal yöntem veya arabirimdeki bir dönüş değerine değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="bf40e-185">❌**Izin verilmiyor: bir üyeden [Özet](../../csharp/language-reference/keywords/abstract.md) ekleme veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="bf40e-186">❌**Izin verilmiyor: [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğü bir üyeden kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="bf40e-187">C# derleyicisi, sanal olmayan yöntemleri çağırmak için [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) ara DIL (IL) yönergelerini yayma eğilimi gösterirken (bir `callvirt` null denetimi gerçekleştirir, normal bir çağrı olmadığında), bu davranış çeşitli nedenlerle ınvariable değildir:</span><span class="sxs-lookup"><span data-stu-id="bf40e-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="bf40e-188">C#, .net 'in hedeflediği tek dil değildir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="bf40e-189">C# derleyicisi, `callvirt` hedef yöntem sanal olmayan ve muhtemelen null olmadığında ( [?. null yayma operatörü](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)aracılığıyla erişilen bir yöntem gibi) normal bir çağrıyı en iyi şekilde iyileştirmenize çalışır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="bf40e-190">Bir yöntem sanal hale getirmek, tüketici kodunun genellikle neredeyse bir kez çağrılmasını sona erdirmek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="bf40e-191">❌**Izin verilmiyor: bir üyeye [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcük ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="bf40e-192">❌**Izin verilmiyor: bir sanal üyeyi soyut hale getirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="bf40e-193">Bir [sanal üye](../../csharp/language-reference/keywords/virtual.md) , türetilmiş bir sınıf tarafından *geçersiz kılınabilen bir* Yöntem uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf40e-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="bf40e-194">[Soyut üye](../../csharp/language-reference/keywords/abstract.md) , uygulama sağlamaz ve geçersiz *kılınmalıdır* .</span><span class="sxs-lookup"><span data-stu-id="bf40e-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="bf40e-195">❌**Izin verilmiyor: erişilebilir (genel veya korumalı) oluşturuculara ve [korumalı](../../csharp/language-reference/keywords/sealed.md) olmayan bir ortak türe soyut üye ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="bf40e-196">❌**Izin verilmiyor: üyenin [statik](../../csharp/language-reference/keywords/static.md) anahtar sözcüğünü ekleme veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="bf40e-197">❌**Izin verilmiyor: var olan bir aşırı yüklemeyi engelleyen ve farklı bir davranışı tanımlayan bir aşırı yükleme ekleniyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="bf40e-198">Bu, önceki aşırı yüklemeye bağlanan mevcut istemcileri keser.</span><span class="sxs-lookup"><span data-stu-id="bf40e-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="bf40e-199">Örneğin, bir sınıfın bir yöntemi kabul eden tek bir sürümü varsa <xref:System.UInt32> , var olan bir tüketici bir değer geçirirken bu aşırı yüklemeye başarıyla bağlanır <xref:System.Int32> .</span><span class="sxs-lookup"><span data-stu-id="bf40e-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="bf40e-200">Ancak, kabul eden bir aşırı yükleme eklerseniz <xref:System.Int32> veya geç bağlamayı kullandığınızda, derleyici artık yeni aşırı yüklemeye bağlanır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="bf40e-201">Farklı davranış sonuç alıyorsa, bu durum bir son değişiklik olur.</span><span class="sxs-lookup"><span data-stu-id="bf40e-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="bf40e-202">❌**Izin verilmiyor: parametresiz oluşturucuyu eklemeden daha önce Oluşturucusu olmayan bir sınıfa Oluşturucu Ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="bf40e-203">❌️**Izin verilmiyor: bir alana [ReadOnly](../../csharp/language-reference/keywords/readonly.md) ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="bf40e-204">❌**Izin verilmiyor: üyenin görünürlüğünü azaltma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="bf40e-205">Bu, *erişilebilir* ( [protected](../../csharp/language-reference/keywords/protected.md) `public` veya `protected` ) oluşturucular olduğunda ve tür *not* [korumalı](../../csharp/language-reference/keywords/sealed.md)olmadığında korunan bir üyenin görünürlüğünü azaltmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="bf40e-206">Bu durumda, korunan bir üyenin görünürlüğünü azaltmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="bf40e-207">Üyenin görünürlüğünü artırmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="bf40e-208">❌**Izin verilmiyor: üyenin türünü değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="bf40e-209">Bir metodun veya bir özelliğin ya da alanın dönüş değeri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="bf40e-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="bf40e-210">Örneğin, döndüren bir yöntemin imzası <xref:System.Object> , bir veya döndürmek için değiştirilemez <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="bf40e-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="bf40e-211">❌**Izin verilmiyor: daha önce durumu olmayan bir yapıya alan ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="bf40e-212">Kesin atama kuralları, değişken türü durum bilgisi olmayan bir yapı olduğu sürece başlatılmamış değişkenlerin kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="bf40e-213">Yapı durum bilgisi olarak yapılırsa, kod başlatılmamış verilerle bitebilecek.</span><span class="sxs-lookup"><span data-stu-id="bf40e-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="bf40e-214">Bu, büyük olasılıkla kaynak bölünmesi ve ikili bir değişiklik değişikliği olur.</span><span class="sxs-lookup"><span data-stu-id="bf40e-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="bf40e-215">❌**Izin verilmiyor: daha önce hiç tetiklendiğinde var olan bir olayı tetikleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="bf40e-216">Davranış değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="bf40e-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="bf40e-217">Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="bf40e-217">Assemblies</span></span>

- <span data-ttu-id="bf40e-218">✔️ **Izin verildi: aynı platformlar hala desteklenmeden bir derlemeyi taşınabilir hale getirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="bf40e-219">❌**Izin verilmiyor: bir derlemenin adını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="bf40e-220">❌**Izin verilmiyor: bir derlemenin ortak anahtarını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="bf40e-221">Özellikler, alanlar, parametreler ve dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="bf40e-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="bf40e-222">**Izin verilen ✔️: bir özellik, alan, dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresinin değerini daha türetilmiş bir türe değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="bf40e-223">Örneğin, bir türü döndüren bir yöntem <xref:System.Object> bir <xref:System.String> örnek döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="bf40e-224">(Ancak, yöntem imzası değiştirilemez.)</span><span class="sxs-lookup"><span data-stu-id="bf40e-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="bf40e-225">✔️ **Izin verildi: üye [sanal](../../csharp/language-reference/keywords/virtual.md) değilse, bir özellik veya parametre için kabul edilen değerlerin aralığını artırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="bf40e-226">Yönteme geçirilebilecek veya üye tarafından döndürülen değer aralığı genişken, parametre veya üye türü ' ni genişletebilirler.</span><span class="sxs-lookup"><span data-stu-id="bf40e-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="bf40e-227">Örneğin, bir yönteme geçirilen değerler 0-124 ' den 0-255 ' e genişleyebilir, parametre türü ' dan ' a geçiş yapılamaz <xref:System.Byte> <xref:System.Int32> .</span><span class="sxs-lookup"><span data-stu-id="bf40e-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="bf40e-228">❌**Izin verilmiyor: üye [sanal](../../csharp/language-reference/keywords/virtual.md) ise, bir özellik veya parametre için kabul edilen değerlerin aralığını artırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="bf40e-229">Bu değişiklik, genişletilmiş değer aralığı için doğru şekilde çalışmayacak olan geçersiz kılınan üyeleri keser.</span><span class="sxs-lookup"><span data-stu-id="bf40e-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="bf40e-230">❌**Izin verilmiyor: bir özellik veya parametre için kabul edilen değerlerin aralığını azaltma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="bf40e-231">❌**Izin verilmiyor: bir özellik, alan, dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerlerin aralığını artırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="bf40e-232">❌**Izin verilmiyor: bir özellik, alan, yöntem dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi Için döndürülen değerleri değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="bf40e-233">❌**Izin verilmiyor: bir özelliğin, alanın veya parametrenin varsayılan değerini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="bf40e-234">❌**Izin verilmiyor: sayısal bir dönüş değerinin hassasiyetini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="bf40e-235">❓ **, Giriş ayrıştırması ve yeni özel durumlar oluşturmadaki bir değişiklik olmalıdır (ayrıştırma davranışı belgelerde belirtilmese bile).**</span><span class="sxs-lookup"><span data-stu-id="bf40e-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="bf40e-236">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bf40e-236">Exceptions</span></span>

- <span data-ttu-id="bf40e-237">✔️ **Izin verilen: var olan bir özel durumdan daha fazla türetilmiş özel durum üretiliyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="bf40e-238">Yeni özel durum var olan bir özel durumun alt sınıfı olduğundan, önceki özel durum işleme kodu özel durumu işlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="bf40e-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="bf40e-239">Örneğin, .NET Framework 4 ' te kültür oluşturma ve alma yöntemleri kültür bulunamazsa bir yerine bir oluşturmaya başlamıştır <xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="bf40e-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="bf40e-240"><xref:System.Globalization.CultureNotFoundException>Öğesinden türetildiğinden <xref:System.ArgumentException> , bu kabul edilebilir bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="bf40e-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="bf40e-241">✔️ **Izin verildi: <xref:System.NotSupportedException> <xref:System.NotImplementedException> <xref:System.NullReferenceException> şundan daha özel bir özel durum üretiliyor** ,</span><span class="sxs-lookup"><span data-stu-id="bf40e-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="bf40e-242">✔️ **Izin verildi: kurtarılamaz olarak kabul edilen bir özel durum üretiliyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="bf40e-243">Kurtarılamaz özel durumlar yakalanmamalıdır, bunun yerine üst düzey bir catch-all işleyicisi tarafından işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="bf40e-244">Bu nedenle, kullanıcıların bu açık özel durumları yakalayan kodun olması beklenmez.</span><span class="sxs-lookup"><span data-stu-id="bf40e-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="bf40e-245">Kurtarılamaz özel durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bf40e-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="bf40e-246">✔️ **Izin verilen: yeni bir kod yolunda yeni bir özel durum üretiliyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="bf40e-247">Özel durum yalnızca yeni parametre değerleri veya durumuyla yürütülen ve önceki sürümü hedefleyen mevcut kodla yürütülemeyen yeni bir kod yolu için geçerli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="bf40e-248">✔️ **Izin verildi: daha sağlam davranışı veya yeni senaryoları etkinleştirmek için özel durumu kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="bf40e-249">Örneğin, `Divide` daha önce yalnızca pozitif değerleri işlenmiş ve başka bir şekilde oluşturulmuş bir yöntem, <xref:System.ArgumentOutOfRangeException> özel durum oluşturmadan hem negatif hem de pozitif değerleri destekleyecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="bf40e-250">✔️ **Izin verilen: hata iletisi metnini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="bf40e-251">Geliştiriciler, kullanıcının kültürüne göre de değişen hata iletilerinin metnine güvenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="bf40e-252">❌**Izin verilmiyor: Yukarıda listelenmeyen başka bir durumda özel durum üretiliyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="bf40e-253">❌**Izin verilmiyor: Yukarıda listelenmeyen herhangi bir özel durumu kaldırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="bf40e-254">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf40e-254">Attributes</span></span>

- <span data-ttu-id="bf40e-255">✔️ **Izin verildi: observable *olmayan* bir özniteliğin değerini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="bf40e-256">❌\*\*Izin verilmiyor: observable olan bir özniteliğin değerini değiştirme *is* \*\*</span><span class="sxs-lookup"><span data-stu-id="bf40e-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="bf40e-257">❓, **Bir özniteliği kaldırmak IÇIN Yargıduyuyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="bf40e-258">Çoğu durumda, bir özniteliği (gibi) kaldırmak, önemli <xref:System.NonSerializedAttribute> bir değişiklik olur.</span><span class="sxs-lookup"><span data-stu-id="bf40e-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="bf40e-259">Platform desteği</span><span class="sxs-lookup"><span data-stu-id="bf40e-259">Platform support</span></span>

- <span data-ttu-id="bf40e-260">✔️ **Izin verildi: daha önce desteklenmeyen bir platformda Işlem destekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="bf40e-261">❌**Izin verilmeyen: bir platformda daha önce desteklenen bir işlem için belirli bir hizmet paketini desteklemiyor veya artık gerektirmiyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="bf40e-262">İç uygulama değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="bf40e-262">Internal implementation changes</span></span>

- <span data-ttu-id="bf40e-263">❓ **, Bir iç türün yüzey alanını değiştirmek Için gereken bır yargıdır.**</span><span class="sxs-lookup"><span data-stu-id="bf40e-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="bf40e-264">Bu tür değişikliklere genel olarak izin verilir, ancak özel yansımayı keser.</span><span class="sxs-lookup"><span data-stu-id="bf40e-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="bf40e-265">Bazı durumlarda, popüler üçüncü taraf kitaplıklarının veya çok sayıda geliştiricinin iç API 'Lere bağlı olduğu durumlarda, bu değişikliklere izin verilmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="bf40e-266">❓ **, Bir üyenin iç uygulamasını değiştirme konusunda Yargıduyuyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="bf40e-267">Bu değişikliklere genel olarak izin verilir, ancak özel yansımayı keser.</span><span class="sxs-lookup"><span data-stu-id="bf40e-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="bf40e-268">Bazı durumlarda, müşteri kodunun genellikle özel yansımaya bağlı olması veya değişikliğin istenmeyen yan etkileri sağlaması durumunda bu değişikliklere izin verilmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="bf40e-269">✔️ **Izin verildi: bir işlemin performansını artırma**</span><span class="sxs-lookup"><span data-stu-id="bf40e-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="bf40e-270">Bir işlemin performansını değiştirme yeteneği zorunludur, ancak bu tür değişiklikler bir işlemin geçerli hızına bağlı kodu kesebilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="bf40e-271">Bu, özellikle de zaman uyumsuz işlemlerin zamanlamasına bağlı olan kodun bir doğrudur.</span><span class="sxs-lookup"><span data-stu-id="bf40e-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="bf40e-272">Performans değişikliğinin, söz konusu API 'nin diğer davranışları üzerinde hiçbir etkisi olmamalıdır; Aksi takdirde, değişiklik koparacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="bf40e-273">✔️ **Izin verildi: dolaylı (ve çoğunlukla olumsuz) bir işlemin performansını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="bf40e-274">Söz konusu değişiklik başka bir nedenden dolayı bölme olarak kategorilere ayrılmazsa, bu kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="bf40e-275">Genellikle, ek işlemleri içerebilen veya yeni işlevsellik ekleyen eylemlerin alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="bf40e-276">Bu, neredeyse her zaman performansı etkiler ancak API 'yi soru işlevinin beklendiği gibi yapmak için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="bf40e-277">❌**Izin verilmiyor: zaman uyumlu bır API 'yi zaman uyumsuz (ve tam tersi) olarak değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="bf40e-278">Kod değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="bf40e-278">Code changes</span></span>

- <span data-ttu-id="bf40e-279">✔️ **Izin verilen: parametreye [params](../../csharp/language-reference/keywords/params.md) ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="bf40e-280">❌**Izin verilmiyor: bir [yapıyı](../../csharp/language-reference/builtin-types/struct.md) bir [sınıfa](../../csharp/language-reference/keywords/class.md) değiştirme ve tam tersi**</span><span class="sxs-lookup"><span data-stu-id="bf40e-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="bf40e-281">❌**Izin verilmiyor: [Checked](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğünü bir kod bloğuna ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="bf40e-282">Bu değişiklik, daha önce bir ve oluşturması için yürütülen kodun <xref:System.OverflowException> kabul edilemez olmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bf40e-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="bf40e-283">❌**Izin verilmiyor: parametrelerin [parametreleri](../../csharp/language-reference/keywords/params.md) kaldırılıyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="bf40e-284">❌**Izin verilmiyor: olayların tetiklenme sırasını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="bf40e-285">Geliştiriciler, olayların aynı sırayla tetiklenmesi makul bir şekilde bekleyebilir ve geliştirici kodu genellikle olayların tetikleneceği sıraya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf40e-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="bf40e-286">❌**Izin verilmiyor: belirli bir eylemde olay oluşturma Işlemi kaldırılıyor**</span><span class="sxs-lookup"><span data-stu-id="bf40e-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="bf40e-287">❌**Izin verilmiyor: verilen olayların sayısını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="bf40e-288">❌**Izin verilmiyor: <xref:System.FlagsAttribute> bir numaralandırma türüne ekleme**</span><span class="sxs-lookup"><span data-stu-id="bf40e-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
