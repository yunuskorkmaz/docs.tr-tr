---
title: .NET Core bozucu değişiklikleri - değerlendir
description: .NET Core, geliştiriciler için .NET sürümleri arasında uyumluluk sağlamak çalışır yolları hakkında bilgi edinin.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: b58edd9ff0bd56b12b861162cc92d484a3b36c8b
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307501"
---
# <a name="evaluate-breaking-changes-in-net-core"></a><span data-ttu-id="79a8c-103">.NET core'da bozucu değişiklikleri değerlendir</span><span class="sxs-lookup"><span data-stu-id="79a8c-103">Evaluate breaking changes in .NET Core</span></span>

<span data-ttu-id="79a8c-104">Buna ait geçmişi, sürüme ve .NET türü arasında uyumluluk sürümden yüksek bir düzeyde korumak .NET çalıştı.</span><span class="sxs-lookup"><span data-stu-id="79a8c-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="79a8c-105">Bu, .NET Core için doğru devam eder.</span><span class="sxs-lookup"><span data-stu-id="79a8c-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="79a8c-106">.NET Core .NET Framework bağımsız olan yeni bir teknoloji kabul edilebilir olsa da, .NET Core yeteneğini .NET Framework'ten ayırmak için iki ana Etkenler sınırla:</span><span class="sxs-lookup"><span data-stu-id="79a8c-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="79a8c-107">Geliştiricilerin çok sayıda ilk olarak geliştirilen veya .NET Framework uygulamaları geliştirmeye devam.</span><span class="sxs-lookup"><span data-stu-id="79a8c-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="79a8c-108">.NET uygulamaları arasında tutarlı bir davranış beklerler.</span><span class="sxs-lookup"><span data-stu-id="79a8c-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="79a8c-109">.NET standard kitaplığı projeleri, geliştiricilerin .NET Core ve .NET Framework tarafından paylaşılan ortak API'ler hedefleyen kitaplıklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="79a8c-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="79a8c-110">Geliştiriciler için kullanılan bir .NET Framework uygulamasında aynı kitaplığı bir .NET Core uygulamasında kullanılan bir kitaplık aynı şekilde davranır bekler.</span><span class="sxs-lookup"><span data-stu-id="79a8c-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="79a8c-111">.NET uygulamaları üzerinde daha fazla uyumluluk yanı sıra, geliştiricilerin .NET Core sürümleri arasında uyumluluk yüksek düzeyde bekler.</span><span class="sxs-lookup"><span data-stu-id="79a8c-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="79a8c-112">Özellikle, .NET Core önceki bir sürümü için yazılan kod sorunsuz bir şekilde .NET Core daha sonraki bir sürümünü çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="79a8c-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="79a8c-113">Aslında, geliştiricilerin çoğu, yeni yayımlanmış bir .NET Core sürümlerinde bulunan yeni API'ler Ayrıca, bu API'leri kullanıma sunulan yayın öncesi sürümleriyle uyumlu olacağını bekler.</span><span class="sxs-lookup"><span data-stu-id="79a8c-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="79a8c-114">Bu makalede, kategorileri uyumluluk değişiklikleri (veya önemli değişiklikler) ve değişiklikleri Bu kategorilerden her biri, .NET ekibi değerlendirir bir şekilde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79a8c-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="79a8c-115">.NET ekibi olası yeni değişikliklerin nasıl yaklaşıyor anlamak, çekme isteklerinde açmakta olduğunuz geliştiriciler için özellikle yararlı [dotnet/corefx'te](https://github.com/dotnet/corefx) mevcut API'lere davranışını değiştirmek GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="79a8c-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who are opening pull requests in the [dotnet/corefx](https://github.com/dotnet/corefx) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="79a8c-116">İkili uyumluluğu ve geriye dönük uyumluluk gibi uyumluluk kategori tanımı için bkz. [bozucu değişiklik kategorileri](categories.md).</span><span class="sxs-lookup"><span data-stu-id="79a8c-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="79a8c-117">Aşağıdaki bölümlerde, .NET Core API'ları ve bunların uygulama uyumluluğunu etkileyen değişiklikler kategorileri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79a8c-117">The following sections describes the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="79a8c-118">Belirli bir değişiklik türünü izin verilen, izin verilmez ve ❓ olabilir veya izin verilmemiş bir değişikliği belirtir ❌ gösterir ✔️ simgesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-118">The ✔️ icon indicates that a particular kind of change is allowed, ❌ indicates that it is disallowed, and  ❓ indicates a change that may or may not be allowed.</span></span> <span data-ttu-id="79a8c-119">Bu son kategori değişiklikler kararı gerektirir ve önceki davranışı nasıl öngörülebilir, açık ve tutarlı bir değerlendirme idi.</span><span class="sxs-lookup"><span data-stu-id="79a8c-119">Changes in this last category require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was.</span></span>

> [!NOTE]
> <span data-ttu-id="79a8c-120">.NET Core kitaplıklarda yapılan değişiklikler nasıl değerlendirilir yönelik bir kılavuz olarak hizmet veren yanı sıra kitaplığı geliştiriciler de bu ölçütleri birden çok .NET uygulamaları ve sürümlerini hedefleyen, kitaplıklarda yapılan değişiklikler değerlendirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79a8c-120">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="79a8c-121">Genel sözleşme değişiklikler</span><span class="sxs-lookup"><span data-stu-id="79a8c-121">Modifications to the public contract</span></span>

<span data-ttu-id="79a8c-122">Bu kategorideki değişiklikleri *değiştirme* genel yüzey alanı türü.</span><span class="sxs-lookup"><span data-stu-id="79a8c-122">Changes in this category *modify* the public surface area of a type.</span></span> <span data-ttu-id="79a8c-123">Bunlar ihlal olduğundan bu kategorideki değişikliklerin çoğu izin verilmeyen *geriye dönük uyumluluk* (gerekmeksizin sonraki sürüm üzerinde yürütme yeteneği geliştirilen bir uygulamanın bir API önceki bir sürümü ile).</span><span class="sxs-lookup"><span data-stu-id="79a8c-123">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="79a8c-124">Türler</span><span class="sxs-lookup"><span data-stu-id="79a8c-124">Types</span></span>

- <span data-ttu-id="79a8c-125">**Arabirim zaten bir taban türü tarafından uygulandığında, bir arabirim uygulaması bir türden kaldırmayı ✔️**</span><span class="sxs-lookup"><span data-stu-id="79a8c-125">**✔️ Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="79a8c-126">**❓ türüne yeni bir arabirim uygulaması ekleme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-126">**❓ Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="79a8c-127">Mevcut istemcilerin olumsuz etkilemez çünkü bu kabul edilebilir bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-127">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="79a8c-128">Herhangi bir değişiklik türü kabul edilebilir değişiklikler kabul edilebilir kalması için yeni uygulama burada tanımlanan sınırları içinde çalışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-128">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="79a8c-129">Bir tasarımcı yeteneğini doğrudan etkileyen arabirimleri eklerken son derece dikkatli olun gereklidir veya alt düzey seri hale getirici kod veya olamaz veri oluşturmak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="79a8c-129">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="79a8c-130">Bir örnek <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="79a8c-130">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="79a8c-131">**❓ Yeni bir temel sınıf ile tanışın**</span><span class="sxs-lookup"><span data-stu-id="79a8c-131">**❓ Introducing a new base class**</span></span>

  <span data-ttu-id="79a8c-132">Var olan iki tür arasında bir hiyerarşiye herhangi yeni tanıtmak değil, bir tür tanıtılabilir [soyut](../../csharp/language-reference/keywords/abstract.md) üyeleri veya semantiği ya da varolan türleri davranışını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="79a8c-132">A type can be introduced into an hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="79a8c-133">Örneğin, .NET Framework 2.0 içinde <xref:System.Data.Common.DbConnection> sınıfı için yeni bir temel sınıf dönüştü <xref:System.Data.SqlClient.SqlConnection>, hangi önceden türetilen doğrudan <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="79a8c-133">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="79a8c-134">**✔️ bir derlemeden bir tür taşıma**</span><span class="sxs-lookup"><span data-stu-id="79a8c-134">**✔️ Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="79a8c-135">Unutmayın *eski* derleme ile işaretlenmeli <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> işaret eden yeni bir derleme.</span><span class="sxs-lookup"><span data-stu-id="79a8c-135">Note that the *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="79a8c-136">**✔️ Değiştirme bir [yapı](../../csharp/language-reference/keywords/struct.md) için yazın bir `readonly struct` türü**</span><span class="sxs-lookup"><span data-stu-id="79a8c-136">**✔️ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="79a8c-137">Not Bu değiştirme bir `readonly struct` için yazın bir `struct` türüne izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="79a8c-137">Note that changing a `readonly struct` type to a `struct` type is not allowed.</span></span>
  
- <span data-ttu-id="79a8c-138">**✔️ Ekleme [korumalı](../../csharp/language-reference/keywords/sealed.md) veya [soyut](../../csharp/language-reference/keywords/abstract.md) anahtar sözcüğü bir tür olduğunda için hiçbir *erişilebilir* oluşturucular (ortak veya korumalı)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-138">**✔️ Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="79a8c-139">**Bir tür görünürlüğünü genişletme ✔️**</span><span class="sxs-lookup"><span data-stu-id="79a8c-139">**✔️ Expanding the visibility of a type**</span></span>

- <span data-ttu-id="79a8c-140">**❌ ad alanı veya bir türün adını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-140">**❌ Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="79a8c-141">**❌ yeniden adlandırma veya bir genel tür kaldırılıyor**</span><span class="sxs-lookup"><span data-stu-id="79a8c-141">**❌ Renaming or removing a public type**</span></span>

   <span data-ttu-id="79a8c-142">Bu, yeniden adlandırılmış veya kaldırılmış türünü kullanan tüm kodları keser.</span><span class="sxs-lookup"><span data-stu-id="79a8c-142">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="79a8c-143">**Temel alınan bir numaralandırma türünün değiştirilmesi ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-143">**❌ Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="79a8c-144">Öznitelik bağımsız değişkenleri ayrıştırılamayan yapabilen bir ikili değişiklik yanı sıra derleme zamanı ve değişiklik davranış budur.</span><span class="sxs-lookup"><span data-stu-id="79a8c-144">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="79a8c-145">**Daha önce korumasız bir tür mühürleme ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-145">**❌ Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="79a8c-146">**❌ Arabirim bir arabirimin temel türleri kümesine ekleme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-146">**❌ Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="79a8c-147">Bir arabirim, daha önce uygulamaz bir arabirim uygularsa, özgün sürümle arabirimin uygulanan tüm türleri kesilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-147">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="79a8c-148">**Bir sınıfın temel sınıf veya arabirimin uygulanan arabirimleri kümesinden kümesinden kaldırma ❓**</span><span class="sxs-lookup"><span data-stu-id="79a8c-148">**❓ Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="79a8c-149">Arabirimi kaldırma kuralı için bir istisna vardır: kaldırılan arabirimden türetilmiş bir arabirim uygulaması ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79a8c-149">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="79a8c-150">Örneğin, kaldırabilirsiniz <xref:System.IDisposable> türü veya arabirim artık uyguluyorsa <xref:System.ComponentModel.IComponent>, uygulayan <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="79a8c-150">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="79a8c-151">**❌ Değiştirme bir `readonly struct` için yazın bir [yapı](../../csharp/language-reference/keywords/struct.md) türü**</span><span class="sxs-lookup"><span data-stu-id="79a8c-151">**❌ Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="79a8c-152">Unutmayın, değişikliği bir `struct` için yazın bir `readonly struct` türüne izin verilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-152">Note that the change of a `struct` type to a `readonly struct` type is allowed.</span></span>

- <span data-ttu-id="79a8c-153">**❌ Değiştirme bir [yapı](../../csharp/language-reference/keywords/struct.md) için yazın bir `ref struct` türü ve bunun tersi de geçerlidir**</span><span class="sxs-lookup"><span data-stu-id="79a8c-153">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="79a8c-154">**Bir tür görünürlüğünü azaltma ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-154">**❌ Reducing the visibility of a type**</span></span>

   <span data-ttu-id="79a8c-155">Ancak, bir tür görünürlüğünü artırmak izin verilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-155">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="79a8c-156">Üyeler</span><span class="sxs-lookup"><span data-stu-id="79a8c-156">Members</span></span>

- <span data-ttu-id="79a8c-157">**Olmayan bir üye görünürlüğünü genişletme ✔️ [sanal](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-157">**✔️ Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="79a8c-158">**Bir soyut üye olmayan genel bir tür ekleme ✔️ *erişilebilir* (ortak veya korumalı) oluşturucular veya türündeki [korumalı](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-158">**✔️ Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="79a8c-159">Ancak, bir soyut üye (ortak veya korumalı) erişilebilir oluşturucuya sahip değil ve olmayan bir türe ekleme `sealed` izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="79a8c-159">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="79a8c-160">**Görünürlüğü kısıtlamak ✔️ bir [korumalı](../../csharp/language-reference/keywords/protected.md) türü (ortak veya korumalı) hiçbir erişilebilir oluşturucuya sahip veya bu tür, üye [korumalı](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-160">**✔️ Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="79a8c-161">**Bir sınıf içinden kaldırıldı türünden hiyerarşinin üst düzeylerindeki üyesi taşınmasını ✔️**</span><span class="sxs-lookup"><span data-stu-id="79a8c-161">**✔️ Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="79a8c-162">**✔️ Ekleme veya kaldırma bir geçersiz kılma**</span><span class="sxs-lookup"><span data-stu-id="79a8c-162">**✔️ Adding or removing an override**</span></span>

  <span data-ttu-id="79a8c-163">Bir geçersiz kılma ile tanışın çağırırken geçersiz kılma atlamak önceki tüketiciler yol açabileceğini unutmayın [temel](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="79a8c-163">Note that introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="79a8c-164">**✔️ sınıfı daha önce hiç Oluşturucusu varsa varsayılan (parametresiz) bir Oluşturucu ile birlikte bir sınıf oluşturucu ekleme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-164">**✔️ Adding a constructor to a class, along with a default (parameterless) constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="79a8c-165">Ancak, daha önce hiç Oluşturucusu olan bir sınıf için bir oluşturucu eklemesini *olmadan* varsayılan oluşturucu eklemesini izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="79a8c-165">However, adding a constructor to a class that previously had no constructors *without* adding the default constructor is not allowed.</span></span>

- <span data-ttu-id="79a8c-166">**Bir üye değiştirme ✔️ [soyut](../../csharp/language-reference/keywords/abstract.md) için [sanal](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-166">**✔️ Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="79a8c-167">**✔️ gelen değiştirerek bir `ref readonly` için bir `ref` dönüş değeri (hariç, sanal yöntemleri veya arabirimi)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-167">**✔️ Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="79a8c-168">**✔️ Kaldırma [salt okunur](../../csharp/language-reference/keywords/readonly.md) statik türü sürece bir alandan alan bir değişmez değer türü olduğu.**</span><span class="sxs-lookup"><span data-stu-id="79a8c-168">**✔️ Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="79a8c-169">**Daha önce tanımlanmadı yeni bir olayı çağırmak ✔️**</span><span class="sxs-lookup"><span data-stu-id="79a8c-169">**✔️ Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="79a8c-170">**❓ türüne yeni bir örneğini alan ekleme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-170">**❓ Adding a new instance field to a type**</span></span>

   <span data-ttu-id="79a8c-171">Bu değişiklik, serileştirme etkiler.</span><span class="sxs-lookup"><span data-stu-id="79a8c-171">This change impacts serialization.</span></span>

- <span data-ttu-id="79a8c-172">**❌ yeniden adlandırma veya bir ortak üye veya parametre kaldırılıyor**</span><span class="sxs-lookup"><span data-stu-id="79a8c-172">**❌ Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="79a8c-173">Bu yeniden adlandırılmış veya kaldırılmış üyesi veya parametre kullanan tüm kodları keser.</span><span class="sxs-lookup"><span data-stu-id="79a8c-173">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="79a8c-174">Bir alıcı veya ayarlayıcı yeniden adlandırma ya da kaldırma numaralandırma üyelerini yanı sıra bir özellik, yeniden adlandırma ya da kaldırma içerdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="79a8c-174">Note that this includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="79a8c-175">**❌ bir arabirim üye ekleme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-175">**❌ Adding a member to an interface**</span></span>

- <span data-ttu-id="79a8c-176">**Genel bir sabit veya sabit listesi üyesi değerinin değiştirilmesi ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-176">**❌ Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="79a8c-177">**❌ bir özellik, alan, parametre veya dönüş değeri türünü değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-177">**❌ Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="79a8c-178">**❌ Ekleme, kaldırma veya parametrelerinin sırasını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-178">**❌ Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="79a8c-179">**❌ Ekleme veya kaldırma [içinde](../../csharp/language-reference/keywords/in.md), [kullanıma](../../csharp/language-reference/keywords/out.md) , veya [ref](../../csharp/language-reference/keywords/ref.md) parametre from anahtar sözcüğü**</span><span class="sxs-lookup"><span data-stu-id="79a8c-179">**❌ Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="79a8c-180">**❌ (kasasının değiştirme dahil) bir parametre yeniden adlandırma**</span><span class="sxs-lookup"><span data-stu-id="79a8c-180">**❌ Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="79a8c-181">Bu, iki nedenden dolayı bozucu olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="79a8c-181">This is considered breaking for two reasons:</span></span>
  
  - <span data-ttu-id="79a8c-182">Visual Basic'te geç bağlama senaryoları geç bağlama özelliği gibi ayırır ve [dinamik](../../csharp/language-reference/keywords/dynamic.md) içinde C#.</span><span class="sxs-lookup"><span data-stu-id="79a8c-182">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/keywords/dynamic.md) in C#.</span></span>
  
  - <span data-ttu-id="79a8c-183">Bunu keser [kaynağı Uyumluluk](categories.md#source-compatibility) geliştiriciler kullandığınızda [adlandırılmış bağımsız değişkenler](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="79a8c-183">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="79a8c-184">**❌ gelen değiştirerek bir `ref` dönüş değeri için bir `ref readonly` dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="79a8c-184">**❌ Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="79a8c-185">**❌️ gelen değiştirerek bir `ref readonly` için bir `ref` dönüş değeri bir sanal yöntem veya arabirimi**</span><span class="sxs-lookup"><span data-stu-id="79a8c-185">**❌️ Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="79a8c-186">**❌ Ekleme veya kaldırma [soyut](../../csharp/language-reference/keywords/abstract.md) bir üyesinin**</span><span class="sxs-lookup"><span data-stu-id="79a8c-186">**❌ Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="79a8c-187">**❌ Kaldırma [sanal](../../csharp/language-reference/keywords/virtual.md) üyesi from anahtar sözcüğü**</span><span class="sxs-lookup"><span data-stu-id="79a8c-187">**❌ Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="79a8c-188">Bu genellikle bir değişiklik olmadığından sırada C# derleyici eğilimlidir yaymak için [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) sanal olmayan yöntemleri çağırmak için Ara dil (IL) yönergeleri (`callvirt` olmayan normal bir çağrı sırasında bir null kontrolü gerçekleştirir ), bu davranışı çeşitli nedenlerle invariable değil:</span><span class="sxs-lookup"><span data-stu-id="79a8c-188">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="79a8c-189">C#değil yalnızca .NET hedefleyen dilidir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-189">C# is not the only language that .NET targets.</span></span>
  
  - <span data-ttu-id="79a8c-190">C# Derleyici giderek çalıştığında en iyi duruma getirme `callvirt` hedef yöntemi sanal olmayan ve null büyük olasılıkla her bir normal arama (aracılığıyla erişilen bir yöntemi gibi [?. null yayılma işleci](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="79a8c-190">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>
  
  <span data-ttu-id="79a8c-191">Sanal bir yöntem yapma, sanal olmayan arama, tüketici kod genellikle umduğunuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-191">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="79a8c-192">**❌ Ekleme [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğü bir üye**</span><span class="sxs-lookup"><span data-stu-id="79a8c-192">**❌ Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="79a8c-193">**Bir sanal üye soyut yapmak ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-193">**❌ Making a virtual member abstract**</span></span>

  <span data-ttu-id="79a8c-194">A [sanal üye](../../csharp/language-reference/keywords/virtual.md) sağlayan bir yöntem uygulaması *olabilir* türetilmiş sınıf tarafından geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="79a8c-194">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="79a8c-195">Bir [soyut üye](../../csharp/language-reference/keywords/abstract.md) uygulaması sağlar ve *olmalıdır* geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="79a8c-195">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="79a8c-196">**Bir soyut üye ekleme ve erişilebilir (ortak veya korumalı) bir oluşturucuya sahip ortak bir türe ❌ değil [korumalı](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-196">**❌ Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="79a8c-197">**❌ Ekleme veya kaldırma [statik](../../csharp/language-reference/keywords/static.md) üyesi from anahtar sözcüğü**</span><span class="sxs-lookup"><span data-stu-id="79a8c-197">**❌ Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="79a8c-198">**Var olan bir aşırı ışığının ve farklı bir davranış tanımlayan bir aşırı yüklemesini eklemeyi ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-198">**❌ Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="79a8c-199">Bu, önceki aşırı yüklemesine bağlı olan mevcut istemcilerin keser.</span><span class="sxs-lookup"><span data-stu-id="79a8c-199">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="79a8c-200">Örneğin, bir sınıf yönteminin tek bir sürüm varsa kabul eden bir <xref:System.UInt32>, geçerken var olan bir tüketici başarıyla için aşırı yükleyen bağlayacaksınız bir <xref:System.Int32> değeri.</span><span class="sxs-lookup"><span data-stu-id="79a8c-200">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="79a8c-201">Ancak, bir aşırı eklerseniz kabul eden bir <xref:System.Int32>, yeniden derlemeden ya da geç bağlama kullanarak, derleyici artık yeni aşırı bağlar.</span><span class="sxs-lookup"><span data-stu-id="79a8c-201">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="79a8c-202">Farklı bir davranış sonuçlanırsa, bir değişiklik budur.</span><span class="sxs-lookup"><span data-stu-id="79a8c-202">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="79a8c-203">**❌ önceden varsayılan oluşturucu eklemeden hiçbir oluşturucu sahip olan bir sınıf oluşturucu ekleme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-203">**❌ Adding a constructor to a class that previously had no constructor without adding the default constructor**</span></span>

- <span data-ttu-id="79a8c-204">**❌️ Ekleme [salt okunur](../../csharp/language-reference/keywords/readonly.md) bir alana**</span><span class="sxs-lookup"><span data-stu-id="79a8c-204">**❌️ Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="79a8c-205">**Üye görünürlüğü azaltma ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-205">**❌ Reducing the visibility of a member**</span></span>

   <span data-ttu-id="79a8c-206">Bu görünürlüğünü azaltmayı içerir bir [korumalı](../../csharp/language-reference/keywords/protected.md) olduğunda üye *erişilebilir* (ortak veya korumalı) oluşturucular ve türü *değil* [ korumalı](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="79a8c-206">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (public or protected) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="79a8c-207">Durum bu değilse, korumalı bir üye görünürlüğünü azaltma izin verilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-207">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="79a8c-208">Üye görünürlüğünü artırmak izin verildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="79a8c-208">Note that increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="79a8c-209">**❌ üye türünü değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-209">**❌ Changing the type of a member**</span></span>

   <span data-ttu-id="79a8c-210">Bir yöntem veya özellik veya alan türünü dönüş değeri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="79a8c-210">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="79a8c-211">Örneğin, döndüren bir yöntem imzası bir <xref:System.Object> döndürülecek değiştirilemez bir <xref:System.String>, ya da tam tersi.</span><span class="sxs-lookup"><span data-stu-id="79a8c-211">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="79a8c-212">**❌ durumu olmadan önceden var olan bir yapı için bir alan ekleme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-212">**❌ Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="79a8c-213">Durum bilgisi olmayan bir yapı değişken türü olduğu sürece belirli atama onayına kuralları başlatılmamış değişkenler kullanımına izin verin.</span><span class="sxs-lookup"><span data-stu-id="79a8c-213">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="79a8c-214">Struct durum bilgisi olan yaptıysanız, kod ile başlatılmamış veri bulunabileceğini.</span><span class="sxs-lookup"><span data-stu-id="79a8c-214">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="79a8c-215">Potansiyel olarak yeni bir kaynak hem de yeni değişiklik bir ikili budur.</span><span class="sxs-lookup"><span data-stu-id="79a8c-215">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="79a8c-216">**❌ hiçbir zaman önce harekete geçirildi var olan bir olay tetikleme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-216">**❌ Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="79a8c-217">Davranış değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="79a8c-217">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="79a8c-218">Bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="79a8c-218">Assemblies</span></span>

- <span data-ttu-id="79a8c-219">**✔️ aynı platformlarda hala desteklendiğinde derleme taşınabilir hale getirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-219">**✔️ Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="79a8c-220">**Bir derleme adının değiştirilmesi ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-220">**❌ Changing the name of an assembly**</span></span>
- <span data-ttu-id="79a8c-221">**Bir derlemenin ortak anahtarı değiştirme ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-221">**❌ Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="79a8c-222">Özellikler, alanlar, parametreler ve dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="79a8c-222">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="79a8c-223">**Bir özellik, alan, dönüş değeri değerinin değiştirilmesi ✔️ veya [kullanıma](../../csharp/language-reference/keywords/out-parameter-modifier.md) daha türetilmiş bir tür parametresi**</span><span class="sxs-lookup"><span data-stu-id="79a8c-223">**✔️ Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="79a8c-224">Örneğin, bir tür döndüren bir yöntem <xref:System.Object> döndürebilir bir <xref:System.String> örneği.</span><span class="sxs-lookup"><span data-stu-id="79a8c-224">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="79a8c-225">(Ancak, yöntem imzası değiştiremezsiniz.)</span><span class="sxs-lookup"><span data-stu-id="79a8c-225">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="79a8c-226">**Aralığını artırma ✔️ üyesi değilse, özelliği veya parametre değerlerini kabul [sanal](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-226">**✔️ Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="79a8c-227">Not yönteme geçirilen veya üye tarafından döndürülen değer aralığını genişletebilirsiniz olsa da parametre veya üye türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="79a8c-227">Note that while the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="79a8c-228">Bir yönteme değerleri 0-124 0-255'e genişletebilirsiniz kullanılırken, örneğin, parametre türü alanından değiştirilemez <xref:System.Byte> için <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="79a8c-228">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="79a8c-229">**Aralığını artırma ❌ üyesiyse bir özellik veya parametre değerlerini kabul [sanal](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="79a8c-229">**❌ Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="79a8c-230">Bu değişiklik, genişletilmiş değer aralığı için düzgün şekilde çalışmaz mevcut geçersiz kılınan üye keser.</span><span class="sxs-lookup"><span data-stu-id="79a8c-230">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="79a8c-231">**Bir özellik veya parametresi için kabul edilen değerler aralığının azaltılması ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-231">**❌ Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="79a8c-232">**Aralığını artırma ❌ döndürülen değerlerin bir özellik, alan, dönüş değeri veya [kullanıma](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi**</span><span class="sxs-lookup"><span data-stu-id="79a8c-232">**❌ Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="79a8c-233">**❌ döndürülen bir özellik, alan, yöntem dönüş değeri, değiştirerek veya [kullanıma](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi**</span><span class="sxs-lookup"><span data-stu-id="79a8c-233">**❌ Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="79a8c-234">**Bir özellik, alan veya parametre varsayılan değerinin değiştirilmesi ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-234">**❌ Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="79a8c-235">**❌ sayısal dönüş değeri duyarlığını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-235">**❌ Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="79a8c-236">**Giriş ayrıştırma ve (ayrıştırma davranışının belgelerinde belirtilmemiş olsa bile, yeni özel durumları atma ❓ bir değişim**</span><span class="sxs-lookup"><span data-stu-id="79a8c-236">**❓ A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="79a8c-237">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="79a8c-237">Exceptions</span></span>

- <span data-ttu-id="79a8c-238">**Var olan bir özel durum daha fazla türetilmiş bir özel durum ✔️**</span><span class="sxs-lookup"><span data-stu-id="79a8c-238">**✔️ Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="79a8c-239">Yeni özel durum var olan bir özel durum öğesinin olduğundan, önceki özel durum işleme kodunu özel durumu işlemek üzere devam eder.</span><span class="sxs-lookup"><span data-stu-id="79a8c-239">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="79a8c-240">Örneğin, .NET Framework 4'te kültürü oluşturma ve alma yöntemleri throw başladığı bir <xref:System.Globalization.CultureNotFoundException> yerine bir <xref:System.ArgumentException> , kültür bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="79a8c-240">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="79a8c-241">Çünkü <xref:System.Globalization.CultureNotFoundException> türetildiği <xref:System.ArgumentException>, bu kabul edilebilir bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-241">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="79a8c-242">**Daha fazla belirli bir özel durum ✔️ <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="79a8c-242">**✔️ Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="79a8c-243">**✔️ kurtarılamaz olarak kabul edilen bir özel durum**</span><span class="sxs-lookup"><span data-stu-id="79a8c-243">**✔️ Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="79a8c-244">Kurtarılamaz bir özel durum yakalanmadı, ancak bunun yerine üst düzey bir genel işleyici tarafından yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-244">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="79a8c-245">Bu nedenle, kullanıcıların açık bu özel durumlarını yakalayan kodu olması beklenmez.</span><span class="sxs-lookup"><span data-stu-id="79a8c-245">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="79a8c-246">Kurtarılamaz bir özel durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="79a8c-246">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="79a8c-247">**Yeni bir kod yolunda yeni bir özel durum atma ✔️**</span><span class="sxs-lookup"><span data-stu-id="79a8c-247">**✔️ Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="79a8c-248">Özel durum yalnızca yeni bir kod-yeni parametre değerlerini veya durumu ile yürütülür ve varolan kodu tarafından yürütülemez yol hedefleyen önceki sürümü uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-248">The exception must apply only to a new code-path which is executed with new parameter values or state, and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="79a8c-249">**✔️ daha sağlam bir davranış veya yeni senaryoları etkinleştirmek için bir özel durum kaldırılıyor**</span><span class="sxs-lookup"><span data-stu-id="79a8c-249">**✔️ Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="79a8c-250">Örneğin, bir `Divide` daha önce yalnızca pozitif değerlere işlenmiş ve oluşturdu yöntemi bir <xref:System.ArgumentOutOfRangeException> yoksa bir özel durum oluşturmadan hem negatif hem pozitif değerleri destekleyecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-250">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="79a8c-251">**✔️ bir hata iletisinin metni değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-251">**✔️ Changing the text of an error message**</span></span>

  <span data-ttu-id="79a8c-252">Geliştiriciler, kullanıcının kültüre göre de değişir hata iletileri metin dayanarak doğrulamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="79a8c-252">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="79a8c-253">**Yukarıda örnekte bir özel durum ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-253">**❌ Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="79a8c-254">**❌ Yukarıda listelenmeyen diğer durumda bir özel durum kaldırılıyor**</span><span class="sxs-lookup"><span data-stu-id="79a8c-254">**❌ Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="79a8c-255">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79a8c-255">Attributes</span></span>

- <span data-ttu-id="79a8c-256">**Bir öznitelik değerinin değiştirilmesi ✔️ *değil* observable**</span><span class="sxs-lookup"><span data-stu-id="79a8c-256">**✔️ Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="79a8c-257">**Bir öznitelik değerinin değiştirilmesi ❌, *olduğu* observable**</span><span class="sxs-lookup"><span data-stu-id="79a8c-257">**❌ Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="79a8c-258">**Bir öznitelik kaldırma ❓**</span><span class="sxs-lookup"><span data-stu-id="79a8c-258">**❓ Removing an attribute**</span></span>

  <span data-ttu-id="79a8c-259">Çoğu durumda, bir öznitelik kaldırma (gibi <xref:System.NonSerializedAttribute>) bölünmesi farklıdır.</span><span class="sxs-lookup"><span data-stu-id="79a8c-259">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="79a8c-260">Platform desteği</span><span class="sxs-lookup"><span data-stu-id="79a8c-260">Platform support</span></span>

- <span data-ttu-id="79a8c-261">**Bir işlem daha önce desteklenmeyen bir platformda destekleyen ✔️**</span><span class="sxs-lookup"><span data-stu-id="79a8c-261">**✔️ Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="79a8c-262">**Desteklemenin veya artık bir platformda desteklemiş bir işlem için belirli hizmet paketini gerektiren ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-262">**❌ Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="79a8c-263">İç uygulama değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="79a8c-263">Internal implementation changes</span></span>

- <span data-ttu-id="79a8c-264">**❓ İç tür'ın yüzey alanını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-264">**❓ Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="79a8c-265">Özel yansıma kesintiye olsa da bu tür değişiklikleri genel olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-265">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="79a8c-266">Burada popüler üçüncü taraf kitaplıkları veya çok sayıda geliştiriciler, iç API'leri bağlıdır, bazı durumlarda, bu değişikliklere izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="79a8c-266">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="79a8c-267">**❓ bir üye iç uygulamasını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-267">**❓ Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="79a8c-268">Özel yansıma kesintiye olsa da bu değişiklikleri genel olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-268">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="79a8c-269">Burada özel yansıma veya değişiklik istenmeyen yan etkileri olduğu tanıtır müşteri kodu sık bağlıdır, bazı durumlarda, bu değişiklikleri izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="79a8c-269">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="79a8c-270">**✔️ bir işlem performansını iyileştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-270">**✔️ Improving the performance of an operation**</span></span>

   <span data-ttu-id="79a8c-271">Bir işlem performansını değiştirme becerisi gereklidir, ancak bu tür değişiklikler geçerli bir işlem hızına olan kod bozabilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-271">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="79a8c-272">Bu zaman uyumsuz işlemler zamanlaması üzerinde bağlı olan kod, özellikle geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-272">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="79a8c-273">Performans değişikliği diğer söz konusu API'nin davranışını üzerinde hiçbir etkisi olması gerektiğini unutmayın; Aksi takdirde, değişiklik bozucu.</span><span class="sxs-lookup"><span data-stu-id="79a8c-273">Note that the performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="79a8c-274">**✔️ dolaylı olarak (ve genellikle olumsuz) bir işlem performansını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-274">**✔️ Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="79a8c-275">Bu, söz konusu değişikliğin başka bir nedenle son olarak kategorilere ayrılmamış, kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-275">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="79a8c-276">Genellikle, gerçekleştirilecek eylemler içir ek işlemleri içerebilir veya yeni işlevler eklemek.</span><span class="sxs-lookup"><span data-stu-id="79a8c-276">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="79a8c-277">Bu, neredeyse her zaman performansını etkiler ancak beklendiği gibi soru işlevinde API'nizi hale getirmek için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-277">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="79a8c-278">**❌ zaman uyumlu bir API için zaman uyumsuz (ve tersi) değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-278">**❌ Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="79a8c-279">Kod değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="79a8c-279">Code changes</span></span>

- <span data-ttu-id="79a8c-280">**✔️ Ekleme [params](../../csharp/language-reference/keywords/params.md) bir parametre**</span><span class="sxs-lookup"><span data-stu-id="79a8c-280">**✔️ Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="79a8c-281">**❌ Değiştirme bir [yapı](../../csharp/language-reference/keywords/struct.md) için bir [sınıfı](../../csharp/language-reference/keywords/class.md) ve bunun tersi de geçerlidir**</span><span class="sxs-lookup"><span data-stu-id="79a8c-281">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="79a8c-282">**❌ Ekleme [işaretli](../../csharp/language-reference/keywords/virtual.md) kod bloğu için anahtar sözcüğü**</span><span class="sxs-lookup"><span data-stu-id="79a8c-282">**❌ Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="79a8c-283">Bu değişikliği atmak için daha önce yürütülen kodu neden olabilir bir <xref:System.OverflowException> ve kabul edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="79a8c-283">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="79a8c-284">**❌ Kaldırma [params](../../csharp/language-reference/keywords/params.md) bir parametre**</span><span class="sxs-lookup"><span data-stu-id="79a8c-284">**❌ Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="79a8c-285">**❌ olaylar sırasını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="79a8c-285">**❌ Changing the order in which events are fired**</span></span>

  <span data-ttu-id="79a8c-286">Geliştiricilerin makul olayların aynı sırayla ateşlenmesine bekleyebileceğiniz ve geliştirici kod sık olaylar sıraya göre değişir.</span><span class="sxs-lookup"><span data-stu-id="79a8c-286">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="79a8c-287">**Belirli bir eylemi bir olayı tetiklenmeden kaldırma ❌**</span><span class="sxs-lookup"><span data-stu-id="79a8c-287">**❌ Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="79a8c-288">**Olayları verilen sayıda değiştirme ❌ çağırılır**</span><span class="sxs-lookup"><span data-stu-id="79a8c-288">**❌ Changing the number of times given events are called**</span></span>

- <span data-ttu-id="79a8c-289">**❌ Ekleme <xref:System.FlagsAttribute> bir numaralandırma türü için**</span><span class="sxs-lookup"><span data-stu-id="79a8c-289">**❌ Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
