---
title: Son değişiklikleri değerlendir-.NET Core
description: .NET Core 'un .NET sürümleri genelinde geliştiriciler için uyumluluğu sürdürme yolları hakkında bilgi edinin.
ms.date: 06/10/2019
ms.openlocfilehash: 4c3f051bf37ea4753d916ee22fedf97a9bad5892
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089355"
---
# <a name="evaluate-breaking-changes-in-net-core"></a><span data-ttu-id="3b30b-103">.NET Core 'daki kırılmaya karşı değişiklikleri değerlendir</span><span class="sxs-lookup"><span data-stu-id="3b30b-103">Evaluate breaking changes in .NET Core</span></span>

<span data-ttu-id="3b30b-104">.NET, geçmişi boyunca sürümden sürüme ve .NET 'in özellikleri arasında yüksek düzeyde uyumluluk tutmaya çalıştı.</span><span class="sxs-lookup"><span data-stu-id="3b30b-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="3b30b-105">Bu, .NET Core için doğru olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="3b30b-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="3b30b-106">.NET Core, .NET Framework bağımsız olan yeni bir teknoloji olarak düşünülebilir, ancak iki ana etken .NET Core 'un .NET Framework arasında sınırsız olmasına izin verebilir:</span><span class="sxs-lookup"><span data-stu-id="3b30b-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="3b30b-107">Asıl olarak çok sayıda geliştirici geliştirmiş veya .NET Framework uygulamaları geliştirmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="3b30b-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="3b30b-108">.NET uygulamalarında tutarlı davranış beklentilerine sahip olurlar.</span><span class="sxs-lookup"><span data-stu-id="3b30b-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="3b30b-109">.NET Standard kitaplık projeleri, geliştiricilerin .NET Core ve .NET Framework tarafından paylaşılan ortak API 'Leri hedefleyen kitaplıklar oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="3b30b-110">Geliştiriciler .NET Core uygulamasında kullanılan bir kitaplığın, .NET Framework uygulamasında kullanılan aynı kitaplıkla aynı şekilde davranmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="3b30b-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="3b30b-111">Geliştiriciler .NET uygulamaları genelinde uyumlulukla birlikte .NET Core sürümleri arasında yüksek düzeyde uyumluluk bekler.</span><span class="sxs-lookup"><span data-stu-id="3b30b-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="3b30b-112">Özellikle .NET Core 'un önceki bir sürümü için yazılan kod, daha sonraki bir .NET Core sürümünde sorunsuz çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="3b30b-113">Aslında birçok geliştirici, .NET Core 'un yeni yayımlanmış sürümlerinde bulunan yeni API 'Lerin, bu API 'Lerin tanıtıldıkları yayın öncesi sürümlerle de uyumlu olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="3b30b-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="3b30b-114">Bu makalede, uyumluluk değişikliklerinin (veya son değişikliklerin) kategorileri ve .NET ekibinin bu kategorilerin her birinde değişiklikleri değerlendirme yöntemi özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="3b30b-115">.NET ekibinin olası önemli değişikliklere nasıl yaklaşılacağını anlamak, var olan API 'lerin davranışını değiştiren [DotNet/corefx](https://github.com/dotnet/corefx) GitHub deposundaki çekme isteklerini açan geliştiriciler için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who are opening pull requests in the [dotnet/corefx](https://github.com/dotnet/corefx) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="3b30b-116">İkili uyumluluk ve geri uyumluluk gibi uyumluluk kategorilerinin bir tanımı için bkz. [değişiklik kategorilerini bölme](categories.md).</span><span class="sxs-lookup"><span data-stu-id="3b30b-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="3b30b-117">Aşağıdaki bölümlerde .NET Core API 'Lerinde yapılan değişiklik kategorileri ve bunların uygulama uyumluluğuyla ilgili kategoriler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-117">The following sections describes the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="3b30b-118">✔️ simgesi, belirli bir değişiklik türüne izin verildiğini gösterir, ❌ izin verilmediğini gösterir ve ❓ izin verilmeyen bir değişikliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-118">The ✔️ icon indicates that a particular kind of change is allowed, ❌ indicates that it is disallowed, and  ❓ indicates a change that may or may not be allowed.</span></span> <span data-ttu-id="3b30b-119">Bu son kategorideki değişiklikler, önceden tahmin edilebilir, belirgin ve tutarlı bir önceki davranışın nasıl olduğunu değerlendirmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-119">Changes in this last category require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was.</span></span>

> [!NOTE]
> <span data-ttu-id="3b30b-120">.NET Core kitaplıklarının değişikliklerinin nasıl değerlendirildiğini gösteren bir kılavuz olarak sunabilmesinin yanı sıra, kitaplık geliştiricileri birden çok .NET uygulaması ve sürümünü hedefleyen kitaplıklarında yapılan değişiklikleri değerlendirmek için de bu ölçütleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-120">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="3b30b-121">Ortak Sözleşmede yapılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="3b30b-121">Modifications to the public contract</span></span>

<span data-ttu-id="3b30b-122">Bu kategorideki değişiklikler bir türün genel yüzey alanını *değiştirir* .</span><span class="sxs-lookup"><span data-stu-id="3b30b-122">Changes in this category *modify* the public surface area of a type.</span></span> <span data-ttu-id="3b30b-123">Bu kategorideki değişikliklerden büyük bir olasılıkla, *geriye dönük uyumluluğu* ihlal etdiklerinden (API 'nin önceki bir sürümü ile geliştirilen bir uygulamanın daha sonraki bir sürümde yeniden derleme olmadan yürütülmesi için geliştirilmiş bir uygulama özelliği) izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="3b30b-123">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="3b30b-124">Türler</span><span class="sxs-lookup"><span data-stu-id="3b30b-124">Types</span></span>

- <span data-ttu-id="3b30b-125">**arabirim bir temel tür tarafından zaten uygulandığında bir türden arabirim uygulamasını kaldırma ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-125">**✔️ Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="3b30b-126">**Türe yeni bir arabirim uygulamasını ekleme ❓**</span><span class="sxs-lookup"><span data-stu-id="3b30b-126">**❓ Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="3b30b-127">Bu, mevcut istemcileri olumsuz etkilemediğinden, kabul edilebilir bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="3b30b-127">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="3b30b-128">Yeni uygulamanın kabul edilebilir olarak kalması için, bu türdeki tüm değişiklikler burada tanımlanan kabul edilebilir değişiklik sınırları içinde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-128">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="3b30b-129">Bir tasarımcının veya seri hale getiricinin alt düzey tüketilemeyecek kod veya veri oluşturma yeteneğini doğrudan etkileyen arabirimler eklenirken aşırı dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-129">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="3b30b-130"><xref:System.Runtime.Serialization.ISerializable> arabirimi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-130">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="3b30b-131">**Yeni bir temel sınıfa giriş ❓**</span><span class="sxs-lookup"><span data-stu-id="3b30b-131">**❓ Introducing a new base class**</span></span>

  <span data-ttu-id="3b30b-132">Bir tür, yeni bir [soyut](../../csharp/language-reference/keywords/abstract.md) üye sunmaz veya var olan türlerin semantiğini ya da davranışını değiştirmek değilse, mevcut iki tür arasında bir hiyerarşiye tanıtılamaz.</span><span class="sxs-lookup"><span data-stu-id="3b30b-132">A type can be introduced into an hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="3b30b-133">Örneğin, .NET Framework 2,0 ' de <xref:System.Data.Common.DbConnection> sınıfı, daha önce doğrudan <xref:System.ComponentModel.Component>türetmiş olan <xref:System.Data.SqlClient.SqlConnection>için yeni bir temel sınıf haline geldi.</span><span class="sxs-lookup"><span data-stu-id="3b30b-133">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="3b30b-134">**bir türü bir derlemeden diğerine taşımak ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-134">**✔️ Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="3b30b-135">*Eski* derlemenin yeni derlemeye işaret eden <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> işaretlenmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b30b-135">Note that the *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="3b30b-136">**✔️ [Yapı](../../csharp/language-reference/keywords/struct.md) türünü `readonly struct` türüne değiştirme**</span><span class="sxs-lookup"><span data-stu-id="3b30b-136">**✔️ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="3b30b-137">`readonly struct` türünün `struct` bir tür olarak değiştirilmesine izin verilmeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b30b-137">Note that changing a `readonly struct` type to a `struct` type is not allowed.</span></span>
  
- <span data-ttu-id="3b30b-138">***erişilebilir* (genel veya korumalı) oluşturucular olmadığında bir türe [Sealed](../../csharp/language-reference/keywords/sealed.md) veya [abstract](../../csharp/language-reference/keywords/abstract.md) anahtar sözcüğü eklemek ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-138">**✔️ Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="3b30b-139">**bir türün görünürlüğünü genişletmek ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-139">**✔️ Expanding the visibility of a type**</span></span>

- <span data-ttu-id="3b30b-140">**bir türün ad alanını veya adını değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-140">**❌ Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="3b30b-141">**ortak bir türü yeniden adlandırma veya kaldırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-141">**❌ Renaming or removing a public type**</span></span>

   <span data-ttu-id="3b30b-142">Bu, yeniden adlandırılan veya kaldırılan türü kullanan tüm kodları keser.</span><span class="sxs-lookup"><span data-stu-id="3b30b-142">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="3b30b-143">**sabit listesinin temel alınan türünü değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-143">**❌ Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="3b30b-144">Bu bir derleme zamanı ve davranışsız değişiklik ve öznitelik bağımsız değişkenlerini ayrıştırılabilir hale getirmek için ikili bir değişiklik de yapar.</span><span class="sxs-lookup"><span data-stu-id="3b30b-144">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="3b30b-145">**daha önce korumasız bir tür ❌ mühürlü**</span><span class="sxs-lookup"><span data-stu-id="3b30b-145">**❌ Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="3b30b-146">**bir arabirimin temel türleri kümesine arabirim ekleme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-146">**❌ Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="3b30b-147">Bir arabirim daha önce uygulanmayan bir arabirim uygularsa, arabirimin orijinal sürümünü uygulayan tüm türler bozulur.</span><span class="sxs-lookup"><span data-stu-id="3b30b-147">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="3b30b-148">**Bir sınıfı temel sınıflar kümesinden veya uygulanan arabirimler kümesinden bir arabirimden kaldırmak ❓**</span><span class="sxs-lookup"><span data-stu-id="3b30b-148">**❓ Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="3b30b-149">Arabirim kaldırma kuralı için bir özel durum vardır: kaldırılan arabirimden türetilen bir arabirimin uygulamasını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b30b-149">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="3b30b-150">Örneğin, tür veya arabirim artık <xref:System.IDisposable>uygulayan <xref:System.ComponentModel.IComponent>uygularsa <xref:System.IDisposable> kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b30b-150">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="3b30b-151">**`readonly struct` türünü [Yapı](../../csharp/language-reference/keywords/struct.md) türüne değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-151">**❌ Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="3b30b-152">`struct` türünün `readonly struct` bir tür değişikliğine izin verildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b30b-152">Note that the change of a `struct` type to a `readonly struct` type is allowed.</span></span>

- <span data-ttu-id="3b30b-153">**❌ [Yapı](../../csharp/language-reference/keywords/struct.md) türünü `ref struct` türüne değiştirme ve tam tersi**</span><span class="sxs-lookup"><span data-stu-id="3b30b-153">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="3b30b-154">**bir türün görünürlüğünü azaltma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-154">**❌ Reducing the visibility of a type**</span></span>

   <span data-ttu-id="3b30b-155">Ancak, bir türün görünürlüğünü artırmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-155">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="3b30b-156">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3b30b-156">Members</span></span>

- <span data-ttu-id="3b30b-157">**[sanal](../../csharp/language-reference/keywords/sealed.md) olmayan bir üyenin görünürlüğünü genişletmek ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-157">**✔️ Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3b30b-158">***erişilebilir* (genel veya korumalı) oluşturuculara sahip olmayan veya tür [korumalı](../../csharp/language-reference/keywords/sealed.md) olan bir ortak türe soyut üye ekleme ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-158">**✔️ Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="3b30b-159">Ancak, erişilebilir (genel veya korumalı) oluşturuculara sahip olan ve `sealed` olmayan bir türe soyut üye eklemek izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="3b30b-159">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="3b30b-160">**tür erişilebilir (genel veya korumalı) oluşturuculara sahip olmadığında veya tür [mühürleniyorsa](../../csharp/language-reference/keywords/sealed.md) [korunan](../../csharp/language-reference/keywords/protected.md) üyenin görünürlüğünü kısıtlama ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-160">**✔️ Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3b30b-161">**bir üyeyi hiyerarşide daha yüksek bir sınıfa, onun kaldırıldığı türden daha yukarıya taşımak ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-161">**✔️ Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="3b30b-162">**geçersiz kılma ekleme veya kaldırma ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-162">**✔️ Adding or removing an override**</span></span>

  <span data-ttu-id="3b30b-163">Bir geçersiz kılma ile tanışın, önceki tüketicilerin [taban](../../csharp/language-reference/keywords/base.md)çağrılırken geçersiz kılma üzerinde atlama yapılmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-163">Note that introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="3b30b-164">**sınıfın daha önce Oluşturucusu yoksa, bir sınıfa bir Oluşturucu eklemek ✔️ varsayılan (parametresiz) bir Oluşturucu ile birlikte**</span><span class="sxs-lookup"><span data-stu-id="3b30b-164">**✔️ Adding a constructor to a class, along with a default (parameterless) constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="3b30b-165">Ancak, parametresiz oluşturucuyu eklemeden daha önceden hiç oluşturucuya *sahip olmayan bir* sınıfa bir Oluşturucu eklemeye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="3b30b-165">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="3b30b-166">**üyeyi [abstract](../../csharp/language-reference/keywords/abstract.md) 'ten [sanal](../../csharp/language-reference/keywords/virtual.md) 'e değiştirme ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-166">**✔️ Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="3b30b-167">**bir `ref readonly` `ref` dönüş değerine değiştirme ✔️ (sanal yöntemler veya arabirimler dışında)**</span><span class="sxs-lookup"><span data-stu-id="3b30b-167">**✔️ Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="3b30b-168">**alanın statik türü kesilebilir değer türünde değilse, bir alandan [ReadOnly](../../csharp/language-reference/keywords/readonly.md) öğesini kaldırma ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-168">**✔️ Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="3b30b-169">**daha önce tanımlanmayan yeni bir olayı çağırmak ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-169">**✔️ Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="3b30b-170">**Türe yeni bir örnek alanı ekleme ❓**</span><span class="sxs-lookup"><span data-stu-id="3b30b-170">**❓ Adding a new instance field to a type**</span></span>

   <span data-ttu-id="3b30b-171">Bu değişiklik Serileştirmeyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="3b30b-171">This change impacts serialization.</span></span>

- <span data-ttu-id="3b30b-172">**ortak üye veya parametreyi yeniden adlandırma veya kaldırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-172">**❌ Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="3b30b-173">Bu, yeniden adlandırılan veya kaldırılan üyeyi veya parametreyi kullanan tüm kodları keser.</span><span class="sxs-lookup"><span data-stu-id="3b30b-173">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="3b30b-174">Bunun yanı sıra, bir alıcı veya ayarlayıcının bir özellikten kaldırılmasını veya yeniden adlandırılmasını, ayrıca sabit listesi üyelerini yeniden adlandırmayı veya kaldırmayı da içerdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b30b-174">Note that this includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="3b30b-175">**arabirime üye ekleme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-175">**❌ Adding a member to an interface**</span></span>

- <span data-ttu-id="3b30b-176">**ortak bir sabit veya numaralandırma üyesinin değerini değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-176">**❌ Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="3b30b-177">**bir özelliğin, alanın, parametrenin veya dönüş değerinin türünü değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-177">**❌ Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="3b30b-178">**Parametre sırasını ekleme, kaldırma veya değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-178">**❌ Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="3b30b-179">**bir parametreden [ın](../../csharp/language-reference/keywords/in.md), [Out](../../csharp/language-reference/keywords/out.md) veya [ref](../../csharp/language-reference/keywords/ref.md) anahtar sözcüğünü ekleme veya kaldırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-179">**❌ Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="3b30b-180">**bir parametreyi yeniden adlandırma ❌ (büyük/küçük harf durumunu değiştirme dahil)**</span><span class="sxs-lookup"><span data-stu-id="3b30b-180">**❌ Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="3b30b-181">Bunun iki nedenden dolayı bölünmesi kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="3b30b-181">This is considered breaking for two reasons:</span></span>
  
  - <span data-ttu-id="3b30b-182">Visual Basic ve [dinamik](../../csharp/language-reference/keywords/dynamic.md) sürümünde geç bağlama özelliği gibi geç bağlantılı senaryoları keser C#.</span><span class="sxs-lookup"><span data-stu-id="3b30b-182">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/keywords/dynamic.md) in C#.</span></span>
  
  - <span data-ttu-id="3b30b-183">Geliştiriciler [adlandırılmış bağımsız değişkenler](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)kullandıklarında [kaynak uyumluluğunu](categories.md#source-compatibility) keser.</span><span class="sxs-lookup"><span data-stu-id="3b30b-183">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="3b30b-184">**`ref` dönüş değerinden `ref readonly` dönüş değerine değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-184">**❌ Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="3b30b-185">**❌, bir `ref readonly` ️ bir sanal yöntem veya arabirimdeki `ref` dönüş değerine değiştirme**</span><span class="sxs-lookup"><span data-stu-id="3b30b-185">**❌️ Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="3b30b-186">**üyelerden [Özet](../../csharp/language-reference/keywords/abstract.md) ekleme veya kaldırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-186">**❌ Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="3b30b-187">**bir üyenin [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğünü kaldırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-187">**❌ Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="3b30b-188">C# Derleyici, sanal olmayan yöntemleri çağırmak için [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) ara dil (IL) yönergelerini yayma eğilimi yaptığından (`callvirt` bir null denetimi gerçekleştirir, normal çağrı olmadığında) Bu durum genellikle Bazı nedenlerle ınvariable:</span><span class="sxs-lookup"><span data-stu-id="3b30b-188">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="3b30b-189">C#, .NET 'in hedeflediği tek dil değildir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-189">C# is not the only language that .NET targets.</span></span>
  
  - <span data-ttu-id="3b30b-190">C# Derleyici, hedef yöntem sanal olmayan ve muhtemelen null olmadığında ( [?. null yayma operatörü](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)aracılığıyla erişilen bir yöntem gibi) normal bir çağrıya `callvirt` iyileştirmenize çalışır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-190">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>
  
  <span data-ttu-id="3b30b-191">Bir yöntem sanal hale getirmek, tüketici kodunun genellikle neredeyse bir kez çağrılmasını sona erdirmek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-191">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="3b30b-192">**bir üyeye [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcük eklemek ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-192">**❌ Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="3b30b-193">**bir sanal üyeyi soyut hale getirmek ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-193">**❌ Making a virtual member abstract**</span></span>

  <span data-ttu-id="3b30b-194">Bir [sanal üye](../../csharp/language-reference/keywords/virtual.md) , türetilmiş bir sınıf tarafından *geçersiz kılınabilen bir* Yöntem uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b30b-194">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="3b30b-195">[Soyut üye](../../csharp/language-reference/keywords/abstract.md) , uygulama sağlamaz ve geçersiz *kılınmalıdır* .</span><span class="sxs-lookup"><span data-stu-id="3b30b-195">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="3b30b-196">**erişilebilir (genel veya korumalı) oluşturuculara sahip ve [korumalı](../../csharp/language-reference/keywords/sealed.md) olmayan bir ortak türe soyut üye ekleme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-196">**❌ Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3b30b-197">**üyenin [statik](../../csharp/language-reference/keywords/static.md) anahtar sözcüğünü ekleme veya kaldırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-197">**❌ Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="3b30b-198">**var olan bir aşırı yüklemeyi engelleyen ve farklı bir davranışı tanımlayan bir aşırı yükleme eklemek ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-198">**❌ Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="3b30b-199">Bu, önceki aşırı yüklemeye bağlanan mevcut istemcileri keser.</span><span class="sxs-lookup"><span data-stu-id="3b30b-199">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="3b30b-200">Örneğin, bir sınıfın bir <xref:System.UInt32>kabul eden tek bir sürümü varsa, var olan bir tüketici <xref:System.Int32> bir değer geçirirken bu aşırı yüklemeye başarıyla bağlanır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-200">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="3b30b-201">Ancak, <xref:System.Int32>kabul eden bir aşırı yükleme eklerseniz veya geç bağlamayı kullandığınızda, derleyici artık yeni aşırı yüklemeye bağlanır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-201">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="3b30b-202">Farklı davranış sonuç alıyorsa, bu durum bir son değişiklik olur.</span><span class="sxs-lookup"><span data-stu-id="3b30b-202">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="3b30b-203">**Parametresiz oluşturucuyu eklemeden daha önce Oluşturucusu olmayan bir sınıfa Oluşturucu Ekleme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-203">**❌ Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="3b30b-204">**❌️ bir alana [ReadOnly](../../csharp/language-reference/keywords/readonly.md) ekleme**</span><span class="sxs-lookup"><span data-stu-id="3b30b-204">**❌️ Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="3b30b-205">**üyenin görünürlüğünü azaltma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-205">**❌ Reducing the visibility of a member**</span></span>

   <span data-ttu-id="3b30b-206">Bu, *erişilebilir* (ortak veya korumalı) oluşturucular olduğunda [korumalı](../../csharp/language-reference/keywords/protected.md) bir üyenin görünürlüğünü azaltmak ve tür [Sealed](../../csharp/language-reference/keywords/sealed.md) *değilse* içerir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-206">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (public or protected) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="3b30b-207">Bu durumda, korunan bir üyenin görünürlüğünü azaltmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-207">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="3b30b-208">Üyenin görünürlüğünü arttırmaya izin verildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b30b-208">Note that increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="3b30b-209">**üyenin türünü değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-209">**❌ Changing the type of a member**</span></span>

   <span data-ttu-id="3b30b-210">Bir metodun veya bir özelliğin ya da alanın dönüş değeri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="3b30b-210">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="3b30b-211">Örneğin, bir <xref:System.Object> döndüren bir yöntemin imzası bir <xref:System.String>döndürecek şekilde değiştirilemez ya da tam tersi.</span><span class="sxs-lookup"><span data-stu-id="3b30b-211">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="3b30b-212">**daha önce durumu olmayan bir yapıya alan ekleme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-212">**❌ Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="3b30b-213">Kesin atama kuralları, değişken türü durum bilgisi olmayan bir yapı olduğu sürece başlatılmamış değişkenlerin kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-213">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="3b30b-214">Yapı durum bilgisi olarak yapılırsa, kod başlatılmamış verilerle bitebilecek.</span><span class="sxs-lookup"><span data-stu-id="3b30b-214">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="3b30b-215">Bu, büyük olasılıkla kaynak bölünmesi ve ikili bir değişiklik değişikliği olur.</span><span class="sxs-lookup"><span data-stu-id="3b30b-215">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="3b30b-216">**daha önce hiç tetiklendiğinde var olan bir olayı ❌ tetiklenme**</span><span class="sxs-lookup"><span data-stu-id="3b30b-216">**❌ Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="3b30b-217">Davranış değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3b30b-217">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="3b30b-218">Bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="3b30b-218">Assemblies</span></span>

- <span data-ttu-id="3b30b-219">**aynı platformlar hala desteklenmeden bir derlemeyi taşınabilir hale getirmek ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-219">**✔️ Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="3b30b-220">**bir derlemenin adını değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-220">**❌ Changing the name of an assembly**</span></span>
- <span data-ttu-id="3b30b-221">**bir derlemenin ortak anahtarını değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-221">**❌ Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="3b30b-222">Özellikler, alanlar, parametreler ve dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="3b30b-222">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="3b30b-223">**bir özellik, alan, dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresinin değerini daha türetilmiş bir türe değiştirme ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-223">**✔️ Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="3b30b-224">Örneğin, <xref:System.Object> bir türü döndüren bir yöntem <xref:System.String> bir örnek döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-224">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="3b30b-225">(Ancak, yöntem imzası değiştirilemez.)</span><span class="sxs-lookup"><span data-stu-id="3b30b-225">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="3b30b-226">**üye [sanal](../../csharp/language-reference/keywords/virtual.md) değilse bir özellik veya parametre için kabul edilen değerlerin aralığını ✔️ artırma**</span><span class="sxs-lookup"><span data-stu-id="3b30b-226">**✔️ Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="3b30b-227">Yönteme geçirilebilecek veya üye tarafından döndürülen değer aralığı genişken, parametre veya üye türü ' nin genişleyebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b30b-227">Note that while the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="3b30b-228">Örneğin, bir yönteme geçirilen değerler 0-124 ' den 0-255 ' e genişleyebilir, parametre türü <xref:System.Byte> <xref:System.Int32>olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="3b30b-228">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="3b30b-229">**üye [sanal](../../csharp/language-reference/keywords/virtual.md) ise, bir özellik veya parametre için kabul edilen değerlerin aralığını artırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-229">**❌ Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="3b30b-230">Bu değişiklik, genişletilmiş değer aralığı için doğru şekilde çalışmayacak olan geçersiz kılınan üyeleri keser.</span><span class="sxs-lookup"><span data-stu-id="3b30b-230">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="3b30b-231">**bir özellik veya parametre için kabul edilen değerlerin aralığını ❌ azaltma**</span><span class="sxs-lookup"><span data-stu-id="3b30b-231">**❌ Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="3b30b-232">**bir özellik, alan, dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerlerin aralığını artırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-232">**❌ Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="3b30b-233">**bir özellik, alan, yöntem dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerleri değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-233">**❌ Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="3b30b-234">**bir özelliğin, alanın veya parametrenin varsayılan değerini değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-234">**❌ Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="3b30b-235">**sayısal bir dönüş değerinin hassasiyetini değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-235">**❌ Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="3b30b-236">**Girişi ayrıştırırken bir değişikliği ❓ ve yeni özel durumlar oluşturma (belgede ayrıştırma davranışı belirtilmese de)**</span><span class="sxs-lookup"><span data-stu-id="3b30b-236">**❓ A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="3b30b-237">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="3b30b-237">Exceptions</span></span>

- <span data-ttu-id="3b30b-238">**✔️ Mevcut bir özel durumdan daha fazla türetilmiş özel durum atma**</span><span class="sxs-lookup"><span data-stu-id="3b30b-238">**✔️ Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="3b30b-239">Yeni özel durum var olan bir özel durumun alt sınıfı olduğundan, önceki özel durum işleme kodu özel durumu işlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="3b30b-239">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="3b30b-240">Örneğin, .NET Framework 4 ' te kültür oluşturma ve alma yöntemleri, kültürün bulunamaması durumunda <xref:System.ArgumentException> yerine <xref:System.Globalization.CultureNotFoundException> oluşturmaya başlamıştır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-240">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="3b30b-241"><xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException>türediği için, bu kabul edilebilir bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="3b30b-241">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="3b30b-242">**✔️ <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException> daha özel bir özel durum atma**</span><span class="sxs-lookup"><span data-stu-id="3b30b-242">**✔️ Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="3b30b-243">**kurtarılamaz olarak kabul edilen bir özel durum ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-243">**✔️ Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="3b30b-244">Kurtarılamaz özel durumlar yakalanmamalıdır, bunun yerine üst düzey bir catch-all işleyicisi tarafından işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-244">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="3b30b-245">Bu nedenle, kullanıcıların bu açık özel durumları yakalayan kodun olması beklenmez.</span><span class="sxs-lookup"><span data-stu-id="3b30b-245">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="3b30b-246">Kurtarılamaz özel durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b30b-246">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="3b30b-247">**Yeni bir kod yolunda yeni bir özel durum oluşturma ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-247">**✔️ Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="3b30b-248">Özel durum yalnızca yeni parametre değerleri veya durumuyla yürütülen ve önceki sürümü hedefleyen mevcut kodla yürütülemeyen yeni bir kod yolu için geçerli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-248">The exception must apply only to a new code-path which is executed with new parameter values or state, and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="3b30b-249">**daha sağlam davranışı veya yeni senaryoları etkinleştirmek için bir özel durumu kaldırma ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-249">**✔️ Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="3b30b-250">Örneğin, daha önce yalnızca pozitif değerleri işlenmiş ve bir <xref:System.ArgumentOutOfRangeException> oluşturan `Divide` yöntemi, özel durum oluşturmadan hem negatif hem de pozitif değerleri destekleyecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-250">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="3b30b-251">**bir hata iletisinin metnini değiştirme ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-251">**✔️ Changing the text of an error message**</span></span>

  <span data-ttu-id="3b30b-252">Geliştiriciler, kullanıcının kültürüne göre de değişen hata iletilerinin metnine güvenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-252">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="3b30b-253">**Yukarıda listelenmeyen başka bir durumda özel durum ❌ oluşturma**</span><span class="sxs-lookup"><span data-stu-id="3b30b-253">**❌ Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="3b30b-254">**Yukarıda listelenmeyen başka bir durumda özel durumu kaldırmak ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-254">**❌ Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="3b30b-255">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b30b-255">Attributes</span></span>

- <span data-ttu-id="3b30b-256">**✔️, observable *olmayan* bir özniteliğin değerini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="3b30b-256">**✔️ Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="3b30b-257">***observable olan* bir özniteliğin değerini değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-257">**❌ Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="3b30b-258">**Özniteliği kaldırma ❓**</span><span class="sxs-lookup"><span data-stu-id="3b30b-258">**❓ Removing an attribute**</span></span>

  <span data-ttu-id="3b30b-259">Çoğu durumda, bir özniteliği kaldırmak (örneğin <xref:System.NonSerializedAttribute>), bir son değişiklik olur.</span><span class="sxs-lookup"><span data-stu-id="3b30b-259">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="3b30b-260">Platform desteği</span><span class="sxs-lookup"><span data-stu-id="3b30b-260">Platform support</span></span>

- <span data-ttu-id="3b30b-261">**daha önce desteklenmeyen bir platformda bir işlemi desteklemek ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-261">**✔️ Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="3b30b-262">**❌, bir platformda daha önce desteklenen bir işlem için belirli bir hizmet paketini desteklememe veya bu aşamada gerektirme**</span><span class="sxs-lookup"><span data-stu-id="3b30b-262">**❌ Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="3b30b-263">İç uygulama değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3b30b-263">Internal implementation changes</span></span>

- <span data-ttu-id="3b30b-264">**İç türün yüzey alanını değiştirme ❓**</span><span class="sxs-lookup"><span data-stu-id="3b30b-264">**❓ Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="3b30b-265">Bu tür değişikliklere genel olarak izin verilir, ancak özel yansımayı keser.</span><span class="sxs-lookup"><span data-stu-id="3b30b-265">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="3b30b-266">Bazı durumlarda, popüler üçüncü taraf kitaplıklarının veya çok sayıda geliştiricinin iç API 'Lere bağlı olduğu durumlarda, bu değişikliklere izin verilmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-266">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="3b30b-267">**Üyenin iç uygulamasını değiştirme ❓**</span><span class="sxs-lookup"><span data-stu-id="3b30b-267">**❓ Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="3b30b-268">Bu değişikliklere genel olarak izin verilir, ancak özel yansımayı keser.</span><span class="sxs-lookup"><span data-stu-id="3b30b-268">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="3b30b-269">Bazı durumlarda, müşteri kodunun genellikle özel yansımaya bağlı olması veya değişikliğin istenmeyen yan etkileri sağlaması durumunda bu değişikliklere izin verilmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-269">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="3b30b-270">**✔️ bir işlemin performansını artırma**</span><span class="sxs-lookup"><span data-stu-id="3b30b-270">**✔️ Improving the performance of an operation**</span></span>

   <span data-ttu-id="3b30b-271">Bir işlemin performansını değiştirme yeteneği zorunludur, ancak bu tür değişiklikler bir işlemin geçerli hızına bağlı kodu kesebilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-271">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="3b30b-272">Bu, özellikle de zaman uyumsuz işlemlerin zamanlamasına bağlı olan kodun bir doğrudur.</span><span class="sxs-lookup"><span data-stu-id="3b30b-272">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="3b30b-273">Performans değişikliğinin, söz konusu API 'nin diğer davranışları üzerinde hiçbir etkisi olmaması gerektiğini unutmayın; Aksi takdirde, değişiklik koparacaktır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-273">Note that the performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="3b30b-274">**bir işlemin performansını dolaylı olarak değiştirme (ve genellikle olumsuz yönde) ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-274">**✔️ Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="3b30b-275">Söz konusu değişiklik başka bir nedenden dolayı bölme olarak kategorilere ayrılmazsa, bu kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-275">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="3b30b-276">Genellikle, ek işlemleri içerebilen veya yeni işlevsellik ekleyen eylemlerin alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-276">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="3b30b-277">Bu, neredeyse her zaman performansı etkiler ancak API 'yi soru işlevinin beklendiği gibi yapmak için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-277">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="3b30b-278">**zaman uyumlu bir API 'yi zaman uyumsuz olarak değiştirme ❌ (ve tam tersi)**</span><span class="sxs-lookup"><span data-stu-id="3b30b-278">**❌ Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="3b30b-279">Kod değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3b30b-279">Code changes</span></span>

- <span data-ttu-id="3b30b-280">**parametreye [params](../../csharp/language-reference/keywords/params.md) ekleme ✔️**</span><span class="sxs-lookup"><span data-stu-id="3b30b-280">**✔️ Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="3b30b-281">**bir [yapıyı](../../csharp/language-reference/keywords/struct.md) bir [sınıfa](../../csharp/language-reference/keywords/class.md) değiştirme ❌ ve tam tersi**</span><span class="sxs-lookup"><span data-stu-id="3b30b-281">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="3b30b-282">**bir kod bloğuna [Checked](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğünü ekleme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-282">**❌ Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="3b30b-283">Bu değişiklik, daha önce yürütülen kodun bir <xref:System.OverflowException> oluşturması ve kabul edilemez olmasının oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b30b-283">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="3b30b-284">**[parametreleri bir parametreden kaldırmak ❌](../../csharp/language-reference/keywords/params.md)**</span><span class="sxs-lookup"><span data-stu-id="3b30b-284">**❌ Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="3b30b-285">**olayların tetiklenme sırasını değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-285">**❌ Changing the order in which events are fired**</span></span>

  <span data-ttu-id="3b30b-286">Geliştiriciler, olayların aynı sırayla tetiklenmesi makul bir şekilde bekleyebilir ve geliştirici kodu genellikle olayların tetikleneceği sıraya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b30b-286">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="3b30b-287">**belirli bir eylemde bir olayın bir kısmını kaldırma ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-287">**❌ Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="3b30b-288">**❌ olayların kaç kez çağrıldığını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="3b30b-288">**❌ Changing the number of times given events are called**</span></span>

- <span data-ttu-id="3b30b-289">**<xref:System.FlagsAttribute> bir numaralandırma türüne ekleme ❌**</span><span class="sxs-lookup"><span data-stu-id="3b30b-289">**❌ Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
