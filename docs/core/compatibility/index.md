---
title: Kesme değişiklik türleri
description: .NET Core'un .NET sürümlerinde geliştiriciler için uyumluluğu nasıl korumaya çalıştığı ve ne tür bir değişikliğin kırılma sı olarak kabul edilir.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628598"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="50c03-103">Uyumluluğu etkileyen değişiklikler</span><span class="sxs-lookup"><span data-stu-id="50c03-103">Changes that affect compatibility</span></span>

<span data-ttu-id="50c03-104">.NET, geçmişi boyunca sürümden sürüme ve .NET'in tatları arasında yüksek düzeyde uyumluluk sağlama girişiminde bulundu.</span><span class="sxs-lookup"><span data-stu-id="50c03-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="50c03-105">Bu ,NET Core için doğru olmaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="50c03-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="50c03-106">.NET Core,.NET Framework'den bağımsız yeni bir teknoloji olarak kabul edilse de, .NET Core'un .NET Framework'den sapma yeteneğini iki ana faktör sınırlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50c03-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="50c03-107">Çok sayıda geliştirici başlangıçta geliştirmiştir veya .NET Framework uygulamalarını geliştirmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="50c03-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="50c03-108">.NET uygulamaları arasında tutarlı davranış beklerler.</span><span class="sxs-lookup"><span data-stu-id="50c03-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="50c03-109">.NET Standart kitaplık projeleri, geliştiricilerin .NET Core ve .NET Framework tarafından paylaşılan ortak API'leri hedefleyen kitaplıklar oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="50c03-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="50c03-110">Geliştiriciler, .NET Core uygulamasında kullanılan bir kitaplığın .NET Framework uygulamasında kullanılan kitaplığın aynı şekilde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="50c03-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="50c03-111">.NET uygulamalarında uyumlulukla birlikte, geliştiriciler .NET Core sürümlerinde yüksek düzeyde uyumluluk beklerler.</span><span class="sxs-lookup"><span data-stu-id="50c03-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="50c03-112">Özellikle, .NET Core'un önceki bir sürümü için yazılan kod, .NET Core'un sonraki bir sürümünde sorunsuz bir şekilde çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50c03-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="50c03-113">Aslında, birçok geliştirici .NET Core'un yeni yayımlanan sürümlerinde bulunan yeni API'lerin, bu API'lerin sunulduğu ön sürüm sürümleriyle de uyumlu olmasını bekleyilmiştir.</span><span class="sxs-lookup"><span data-stu-id="50c03-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="50c03-114">Bu makalede, uyumluluk değişiklikleri (veya kesme değişiklikleri) kategorileri ve .NET ekibinin bu kategorilerin her birinde değişiklikleri değerlendirme şekli özetlendi.</span><span class="sxs-lookup"><span data-stu-id="50c03-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="50c03-115">.NET ekibinin olası kesme değişikliklerine nasıl yaklaştığını anlamak, özellikle varolan API'lerin davranışını değiştiren [dotnet/runtime](https://github.com/dotnet/runtime) GitHub deposunda çekme isteklerini açan geliştiriciler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="50c03-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="50c03-116">İkili uyumluluk ve geriye dönük uyumluluk gibi uyumluluk kategorilerinin tanımı [için](categories.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="50c03-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="50c03-117">Aşağıdaki bölümlerde .NET Core API'lerinde yapılan değişikliklerin kategorileri ve bunların uygulama uyumluluğu üzerindeki etkileri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="50c03-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="50c03-118">Değişikliklere ✔️ izin verilir, ❌izin verilmez veya önceki davranışın ne kadar öngörülebilir, açık ve tutarlı bir şekilde ❓ bir yargı ve değerlendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="50c03-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="50c03-119">.NET Core kitaplıklarındaki değişikliklerin nasıl değerlendirildiği konusunda bir rehber olarak hizmet vermenin yanı sıra, kitaplık geliştiricileri bu ölçütleri birden çok .NET uygulamasını ve sürümlerini hedefleyen kitaplıklarındaki değişiklikleri değerlendirmek için de kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="50c03-120">Kamu sözleşmesinde yapılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="50c03-120">Modifications to the public contract</span></span>

<span data-ttu-id="50c03-121">Bu kategorideki değişiklikler, bir türün ortak yüzey alanını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="50c03-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="50c03-122">Geriye *dönük uyumluluğu* ihlal ettikleri için bu kategorideki değişikliklerin çoğuna izin verilmez (bir API'nin önceki sürümüyle geliştirilen bir uygulamanın daha sonraki bir sürümde yeniden derleme olmadan yürütebilme yeteneği).</span><span class="sxs-lookup"><span data-stu-id="50c03-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="50c03-123">Türler</span><span class="sxs-lookup"><span data-stu-id="50c03-123">Types</span></span>

- <span data-ttu-id="50c03-124">✔️ **Izin verilir: Arabirim zaten bir temel türü tarafından uygulandığında bir türden arabirim uygulamasını kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="50c03-125">❓ **YARGI GEREKTIRIR: Bir türe yeni bir arayüz uygulaması ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="50c03-126">Varolan istemcileri olumsuz etkilemediği için bu kabul edilebilir bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="50c03-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="50c03-127">Türdeki herhangi bir değişikliğin, yeni uygulamanın kabul edilebilir kalması için burada tanımlanan kabul edilebilir değişikliklerin sınırları içinde çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="50c03-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="50c03-128">Bir tasarımcının veya seri göstericinin alt düzey tüketilemeyen kod veya veri oluşturma yeteneğini doğrudan etkileyen arabirimler eklerken çok dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="50c03-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="50c03-129">Bir örnek <xref:System.Runtime.Serialization.ISerializable> arayüzdür.</span><span class="sxs-lookup"><span data-stu-id="50c03-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="50c03-130">❓ **YARGI GEREKTIRIR: Yeni bir taban sınıf tanıtılması**</span><span class="sxs-lookup"><span data-stu-id="50c03-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="50c03-131">Bir tür, yeni [soyut](../../csharp/language-reference/keywords/abstract.md) üyeler tanımazsa veya varolan türlerin anlamlarını veya davranışını değiştirmiyorsa, varolan iki tür arasında bir hiyerarşiye dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="50c03-132">Örneğin, .NET Framework 2.0'da <xref:System.Data.Common.DbConnection> <xref:System.Data.SqlClient.SqlConnection>sınıf, daha önce doğrudan .'den <xref:System.ComponentModel.Component>türetilmiş olan yeni bir taban sınıf haline geldi.</span><span class="sxs-lookup"><span data-stu-id="50c03-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="50c03-133">**✔️ Izin verilir: Bir türbir derlemeden diğerine taşıma**</span><span class="sxs-lookup"><span data-stu-id="50c03-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="50c03-134">*Eski* derleme, yeni derlemeye işaret eden <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> noktalarla işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="50c03-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="50c03-135">✔️ **Izin VERILIR: [Yapı](../../csharp/language-reference/builtin-types/struct.md) türünü `readonly struct` bir türe değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="50c03-136">Bir `readonly struct` türü bir `struct` türle değiştirmek yasaktır.</span><span class="sxs-lookup"><span data-stu-id="50c03-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="50c03-137">✔️ **İzİn VERİlMESİ: *Erişilebilir* (ortak veya korumalı) yapıcılar olmadığında bir türe [mühürlü](../../csharp/language-reference/keywords/sealed.md) veya [soyut](../../csharp/language-reference/keywords/abstract.md) anahtar kelime ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="50c03-138">✔️ **IZIN VERİlDİ: Bir türün görünürlüğünü genişletme**</span><span class="sxs-lookup"><span data-stu-id="50c03-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="50c03-139">❌**ADVERİl: Bir türün ad alanını veya adını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="50c03-140">❌**ADVERİl: Genel bir türü yeniden adlandırma veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="50c03-141">Bu, yeniden adlandırılmış veya kaldırılan türü kullanan tüm kodu kırar.</span><span class="sxs-lookup"><span data-stu-id="50c03-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="50c03-142">❌**İzin VERİlMEMİş: Bir numaralandırmanın altında yatan türü değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="50c03-143">Bu derleme zamanı ve davranışsal kırılma değişikliğinin yanı sıra öznitelik bağımsız değişkenlerini ayrıştırılamaz hale getirebilecek ikili bir kırılma değişikliğidir.</span><span class="sxs-lookup"><span data-stu-id="50c03-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="50c03-144">❌**İzİn VERİlMEMİş: Daha önce mühürlenmemiş bir tür mühürleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="50c03-145">❌**İzin VERİlMEMİş: Bir arabirimin temel türleri kümesine arabirim ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="50c03-146">Bir arabirim daha önce uygulamadığı bir arabirim uygularsa, arabirimin özgün sürümünü uygulayan tüm türler bozulur.</span><span class="sxs-lookup"><span data-stu-id="50c03-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="50c03-147">❓ **YARGI GEREKTIRIR: Bir sınıfı temel sınıflar kümesinden veya uygulanan arabirimler kümesinden bir arabirimden kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="50c03-148">Arabirim kaldırma kuralının bir istisnası vardır: kaldırılan arabirimden türeyen bir arabirim uygulamasını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c03-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="50c03-149">Örneğin, tür veya <xref:System.IDisposable> arabirim şimdi uygular <xref:System.ComponentModel.IComponent>, hangi <xref:System.IDisposable>uygular kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50c03-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="50c03-150">❌**İzin VERİlMEMİş: Bir `readonly struct` türbirin [yapı](../../csharp/language-reference/builtin-types/struct.md) türüne değiştirilmesi**</span><span class="sxs-lookup"><span data-stu-id="50c03-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="50c03-151">Ancak, bir `struct` türün `readonly struct` bir türe değiştirilmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="50c03-152">❌**İzin VERİlMEMİş: [Bir](../../csharp/language-reference/builtin-types/struct.md) yapı `ref struct` türünü bir türe değiştirme ve bunun tersi**</span><span class="sxs-lookup"><span data-stu-id="50c03-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="50c03-153">❌**İzin VERİlMEMİş: Bir türün görünürlüğünü azaltmak**</span><span class="sxs-lookup"><span data-stu-id="50c03-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="50c03-154">Ancak, bir türün görünürlüğünü artırmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="50c03-155">Üyeler</span><span class="sxs-lookup"><span data-stu-id="50c03-155">Members</span></span>

- <span data-ttu-id="50c03-156">✔️ **Izin: [Sanal](../../csharp/language-reference/keywords/sealed.md) olmayan bir üyenin görünürlüğünü genişletme**</span><span class="sxs-lookup"><span data-stu-id="50c03-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="50c03-157">✔️ **Izin: *Erişilebilir* (ortak veya korumalı) oluşturucusu olmayan veya türü [mühürlü](../../csharp/language-reference/keywords/sealed.md) olan genel bir türe soyut bir üye ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="50c03-158">Ancak, erişilebilir (ortak veya korumalı) oluşturuculara sahip ve izin `sealed` verilmeyen bir türe soyut bir üye eklemek.</span><span class="sxs-lookup"><span data-stu-id="50c03-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="50c03-159">**✔️ Izin: Türü erişilebilir (ortak veya korumalı) yapıcılar olmadığında veya türü [mühürlendiğinde](../../csharp/language-reference/keywords/sealed.md) [korunan](../../csharp/language-reference/keywords/protected.md) bir üyenin görünürlüğünü kısıtlama**</span><span class="sxs-lookup"><span data-stu-id="50c03-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="50c03-160">**✔️ İzin ver: Bir üyeyi hiyerarşide kaldırıldığı türden daha yüksek bir sınıfa taşıma**</span><span class="sxs-lookup"><span data-stu-id="50c03-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="50c03-161">**✔️ İzNEdİlİr: Bir geçersiz kılma ekleme veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="50c03-162">Geçersiz kılmanın tanıtılması, önceki tüketicilerin [tabanı](../../csharp/language-reference/keywords/base.md)ararken geçersiz kılmayı atlayabına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="50c03-163">**✔️ İzİn VERİlMeSİ: Sınıfın daha önce oluşturucusu yoksa parametresiz bir yapıcı ile birlikte bir sınıfa yapıcı ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="50c03-164">Ancak, parametresiz oluşturucu *eklemeden* daha önce hiçbir oluşturucusu olan bir sınıfa bir oluşturucu eklenmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="50c03-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="50c03-165">**✔️ Izin: Bir üyeyi [soyuttan](../../csharp/language-reference/keywords/abstract.md) [sanala](../../csharp/language-reference/keywords/virtual.md) değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="50c03-166">**✔️ Izin: `ref readonly` A'dan `ref` dönüş değerine değiştirme (sanal yöntemler veya arabirimler hariç)**</span><span class="sxs-lookup"><span data-stu-id="50c03-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="50c03-167">✔️ **Izin verilmeyen: Alanın statik türü mutable değer türü olmadığı sürece, [yalnızca](../../csharp/language-reference/keywords/readonly.md) bir alandan okuma kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="50c03-168">✔️ **Izin verildi: Daha önce tanımlanmamış yeni bir olayı çağırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="50c03-169">❓ **YARGI GEREKTIRIR: Bir türe yeni bir örnek alanı ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="50c03-170">Bu değişiklik serileştirmeyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="50c03-170">This change impacts serialization.</span></span>

- <span data-ttu-id="50c03-171">❌**ADİZ: Bir kamu üyesinin veya parametrenin yeniden adlandırılması veya kaldırılması**</span><span class="sxs-lookup"><span data-stu-id="50c03-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="50c03-172">Bu, yeniden adlandırılmış veya kaldırılan üyeyi veya parametreyi kullanan tüm kodu kırar.</span><span class="sxs-lookup"><span data-stu-id="50c03-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="50c03-173">Bu, bir özellikten bir vericiyi veya ayarlayıcıyı kaldırmayı veya yeniden adlandırmayı ve numaralandırma üyelerini yeniden adlandırmayı veya kaldırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="50c03-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="50c03-174">❌**İzin VERİlMESİn: Arabirime üye ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="50c03-175">❌**İzin VERİlMEMİş: Genel sabit veya numaralandırma üyesinin değerini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="50c03-176">❌**İzin VERİlMEMİş: Bir özelliğin, alanın, parametrenin veya geri dönüş değerinin türünü değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="50c03-177">❌**İzin VERİlMEMİş: Parametrelerin sırasını ekleme, kaldırma veya değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="50c03-178">❌**İzin VERİlMEMİş: [Bir](../../csharp/language-reference/keywords/in.md)parametreden in , [out](../../csharp/language-reference/keywords/out.md) veya [ref](../../csharp/language-reference/keywords/ref.md) anahtar sözcüğü ekleme veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="50c03-179">❌**ADVERİl: Bir parametreyi yeniden adlandırma (servis talebinin değiştirilmesi dahil)**</span><span class="sxs-lookup"><span data-stu-id="50c03-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="50c03-180">Bu iki nedenden dolayı kırma olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="50c03-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="50c03-181">Visual Basic'te geç bağlama özelliği ve C#'da [dinamik](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) gibi geç giden senaryoları kırar.</span><span class="sxs-lookup"><span data-stu-id="50c03-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="50c03-182">Geliştiriciler [adlandırılmış bağımsız değişkenleri](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)kullandığında [kaynak uyumluluğunu](categories.md#source-compatibility) bozar.</span><span class="sxs-lookup"><span data-stu-id="50c03-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="50c03-183">❌**İzin VERİlMEMİş: `ref` İade `ref readonly` değerinden geri dönüş değerine değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="50c03-184">❌️**İzin VERİlMEMİş: Sanal bir yöntem veya arabirimde a'dan `ref readonly` `ref` geri dönüş değerine değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="50c03-185">❌**İzİn VERİlMESİ: Bir üyeden [özet](../../csharp/language-reference/keywords/abstract.md) ekleme veya kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="50c03-186">❌**İzin VERİlMESİn: [Sanal](../../csharp/language-reference/keywords/virtual.md) anahtar kelimeyi üyeden kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="50c03-187">C# derleyicisi sanal olmayan yöntemleri aramak için [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) yönergeleri yağlama eğilimindedir`callvirt` çünkü bu genellikle bir kırılma değişiklik olmasa da (normal bir arama yok, null denetim gerçekleştirir), bu davranış çeşitli nedenlerle değişmez değildir:</span><span class="sxs-lookup"><span data-stu-id="50c03-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="50c03-188">C# .NET'in hedef lemesi tek dil değildir.</span><span class="sxs-lookup"><span data-stu-id="50c03-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="50c03-189">C# derleyicisi, `callvirt` hedef yöntem sanal olmadığında ve büyük olasılıkla null olmadığında [(?. null yayılma işleci](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)aracılığıyla erişilen bir yöntem gibi) normal bir çağrıya giderek daha fazla optimizasyon yapmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="50c03-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="50c03-190">Bir yöntemi sanal hale getirmek, tüketici kodunun genellikle onu sanal olmayan olarak adlandırması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="50c03-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="50c03-191">❌**İzin VERİlMESİn: Bir üyeye [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar kelime ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="50c03-192">❌**DISALLOWED: Sanal üye soyut yapma**</span><span class="sxs-lookup"><span data-stu-id="50c03-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="50c03-193">[Sanal üye,](../../csharp/language-reference/keywords/virtual.md) türetilmiş bir sınıf tarafından geçersiz *kılınabilecek* bir yöntem uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="50c03-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="50c03-194">Soyut bir [üye](../../csharp/language-reference/keywords/abstract.md) hiçbir uygulama sağlar ve geçersiz *kılınmalıdır.*</span><span class="sxs-lookup"><span data-stu-id="50c03-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="50c03-195">❌**İzin VERİlMEMİş: Erişilebilir (ortak veya korumalı) oluşturuculara sahip ve [mühürlü](../../csharp/language-reference/keywords/sealed.md) olmayan bir genel türe soyut bir üye ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="50c03-196">❌**İZIN VERİlMESİn: [Statik](../../csharp/language-reference/keywords/static.md) anahtar kelimenin üyeden eklenmesi veya kaldırılması**</span><span class="sxs-lookup"><span data-stu-id="50c03-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="50c03-197">❌**İzİn VERİlMESİ: Varolan aşırı yüklemeyi engelleyen ve farklı bir davranışı tanımlayan** aşırı yük ekleme</span><span class="sxs-lookup"><span data-stu-id="50c03-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="50c03-198">Bu, önceki aşırı yüklemeye bağlı varolan istemcileri kırar.</span><span class="sxs-lookup"><span data-stu-id="50c03-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="50c03-199">Örneğin, bir sınıfın bir <xref:System.UInt32>yöntemi kabul eden tek bir sürümü varsa, varolan bir tüketici bir <xref:System.Int32> değeri geçerken bu aşırı yüke başarıyla bağlanır.</span><span class="sxs-lookup"><span data-stu-id="50c03-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="50c03-200">Ancak, yeniden derleme veya geç bağlama <xref:System.Int32>kullanırken bir , kabul eden bir aşırı yük eklerseniz, derleyici şimdi yeni aşırı yüke bağlanır.</span><span class="sxs-lookup"><span data-stu-id="50c03-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="50c03-201">Farklı davranış sonuçları, bu bir kırılma değişikliğidir.</span><span class="sxs-lookup"><span data-stu-id="50c03-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="50c03-202">❌**İzİn VERİlMEMİş: Parametresiz oluşturucueklemeden daha önce oluşturucu olmayan bir sınıfa yapıcı ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="50c03-203">❌️**İzİn VERİlMESİn: [Yalnızca](../../csharp/language-reference/keywords/readonly.md) bir alana okuma ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="50c03-204">❌**İzİn VERİlMESİ: Bir üyenin görünürlüğünü azaltmak**</span><span class="sxs-lookup"><span data-stu-id="50c03-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="50c03-205">Bu, *erişilebilir* `public` ( veya `protected`) oluşturucular olduğunda ve türü [mühürlü](../../csharp/language-reference/keywords/sealed.md) *olmadığında* [korunan](../../csharp/language-reference/keywords/protected.md) bir üyenin görünürlüğünü azaltmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="50c03-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="50c03-206">Bu durumda, korunan bir üyenin görünürlüğünü azaltmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="50c03-207">Bir üyenin görünürlüğünün artırılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="50c03-208">❌**İzin VERİlMEMİş: Üye nin türünü değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="50c03-209">Bir yöntemin veya bir özellik veya alanın türündeki geri dönüş değeri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="50c03-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="50c03-210">Örneğin, bir <xref:System.Object> döndürür bir yöntemin imzası bir <xref:System.String>, ya da tam tersi döndürmek için değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="50c03-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="50c03-211">❌**İzİn VERİlMEMİş: Daha önce durumu olmayan bir yapıya alan ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="50c03-212">Kesin atama kuralları, değişken türü durumsuz bir yapı olduğu sürece başharflenmemiş değişkenlerin kullanımına izin verir.</span><span class="sxs-lookup"><span data-stu-id="50c03-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="50c03-213">Yapı devlet seli yapılırsa, kod başharfe çözülmemiş verilerle sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="50c03-214">Bu hem potansiyel bir kaynak kırma ve ikili kırma değişikliğidir.</span><span class="sxs-lookup"><span data-stu-id="50c03-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="50c03-215">❌**İzİn VERİlMEMİz: Varolan bir olayı daha önce hiç ateşlemediğinde ateşlemek**</span><span class="sxs-lookup"><span data-stu-id="50c03-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="50c03-216">Davranış değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="50c03-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="50c03-217">Bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="50c03-217">Assemblies</span></span>

- <span data-ttu-id="50c03-218">✔️ **Izin VERILIR: Aynı platformlar hala desteklendiğinde montajı taşınabilir hale getirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="50c03-219">❌**İzin VERİlMEMİş: Bir derlemenin adını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="50c03-220">❌**İzİn VERİlMESİn: Bir derlemenin ortak anahtarını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="50c03-221">Özellikler, alanlar, parametreler ve iade değerleri</span><span class="sxs-lookup"><span data-stu-id="50c03-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="50c03-222">**✔️ Izin verilir: Bir özelliğin, alanın, geri dönüş değerinin veya [çıkış](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresinin değerini daha türetilmiş bir türe değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="50c03-223">Örneğin, bir tür döndüren <xref:System.Object> bir <xref:System.String> yöntem bir örneği döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="50c03-224">(Ancak, yöntem imzası değiştirilemez.)</span><span class="sxs-lookup"><span data-stu-id="50c03-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="50c03-225">✔️ **Izin: Üye [sanal](../../csharp/language-reference/keywords/virtual.md) değilse, bir özellik veya parametre için kabul edilen değerlerin aralığının artırılması**</span><span class="sxs-lookup"><span data-stu-id="50c03-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="50c03-226">Yönteme geçirilebilen veya üye tarafından döndürülebilen değerler aralığı genişletilebilirken, parametre veya üye türü genişletilemez.</span><span class="sxs-lookup"><span data-stu-id="50c03-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="50c03-227">Örneğin, bir yönteme geçirilen değerler 0-124'ten 0-255'e kadar genişletilebilirken, parametre türü ' den <xref:System.Byte> ' e <xref:System.Int32>değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="50c03-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="50c03-228">❌**İzin VERİlMEMİş: Üye sanalsa, bir özellik veya [virtual](../../csharp/language-reference/keywords/virtual.md) parametre için kabul edilen değerlerin aralığının artırılması**</span><span class="sxs-lookup"><span data-stu-id="50c03-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="50c03-229">Bu değişiklik, genişletilmiş değerler aralığı için doğru çalışmayacak varolan geçersiz kılınmış üyeleri kırar.</span><span class="sxs-lookup"><span data-stu-id="50c03-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="50c03-230">❌**İzin VERİlMEMİz: Bir özellik veya parametre için kabul edilen değerlerin aralığını azaltma**</span><span class="sxs-lookup"><span data-stu-id="50c03-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="50c03-231">❌**İzin VERİlMEMİş: Bir özellik, alan, geri dönüş değeri veya [çıkış](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerlerin aralığını artırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="50c03-232">❌**İzin VERİlMEMİş: Bir özellik, alan, yöntem dönüş değeri veya [çıkış](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerleri değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="50c03-233">❌**İzin VERİlMEMİş: Bir özelliğin, alanın veya parametrenin varsayılan değerini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="50c03-234">❌**İzin VERİlMEMİş: Sayısal bir iade değerinin kesinliği değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="50c03-235">❓ **YARGILAMA GEREKİr: Girdinin ayrıştırılmasında ve yeni istisnalar atılmasında bir değişiklik (belgelerde ayrıştırma davranışı belirtilmese bile**</span><span class="sxs-lookup"><span data-stu-id="50c03-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="50c03-236">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="50c03-236">Exceptions</span></span>

- <span data-ttu-id="50c03-237">**✔️ Izin verilir: Varolan bir özel durum daha türemiş bir özel durum atma**</span><span class="sxs-lookup"><span data-stu-id="50c03-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="50c03-238">Yeni özel durum varolan bir özel durum bir alt sınıf olduğundan, önceki özel durum işleme kodu özel durum işlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="50c03-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="50c03-239">Örneğin, .NET Framework 4'te kültür oluşturma ve alma yöntemleri, eğer <xref:System.ArgumentException> kültürü bulunamazsa yerine bir <xref:System.Globalization.CultureNotFoundException> atamaya başladı.</span><span class="sxs-lookup"><span data-stu-id="50c03-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="50c03-240">Çünkü <xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException>türetilmiştir, bu kabul edilebilir bir değişikliktir.</span><span class="sxs-lookup"><span data-stu-id="50c03-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="50c03-241">✔️ **Izin: Daha özel <xref:System.NotSupportedException>bir <xref:System.NotImplementedException> <xref:System.NullReferenceException> istisna atma , ,**</span><span class="sxs-lookup"><span data-stu-id="50c03-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="50c03-242">**✔️ Izin VERİlMeDİ: Kurtarılamaz olarak kabul edilen bir özel durum atma**</span><span class="sxs-lookup"><span data-stu-id="50c03-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="50c03-243">Kurtarılamayan özel durumlar yakalanmamalı, bunun yerine üst düzey catch-all işleyicisi tarafından işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="50c03-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="50c03-244">Bu nedenle, kullanıcıların bu açık özel durumları yakalayan bir kod olması beklenmez.</span><span class="sxs-lookup"><span data-stu-id="50c03-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="50c03-245">Kurtarılamayan özel durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="50c03-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="50c03-246">**✔️ Izin ver: Yeni bir kod yolunda yeni bir özel durum atma**</span><span class="sxs-lookup"><span data-stu-id="50c03-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="50c03-247">Özel durum yalnızca yeni parametre değerleri veya durumuyla yürütülen ve önceki sürümü hedefleyen varolan kod tarafından yürütülmeyen yeni bir kod yoluna uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50c03-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="50c03-248">✔️ **Izin: Daha sağlam davranışlar veya yeni senaryolar etkinleştirmek için bir özel durum kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="50c03-249">Örneğin, daha `Divide` önce yalnızca pozitif değerleri işleyen <xref:System.ArgumentOutOfRangeException> ve başka bir değer atan bir yöntem, özel durum atmadan hem negatif hem de pozitif değerleri destekleyecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="50c03-250">✔️ **İzİn VERİlMESİnE İzİn VERİlMESİnE: Hata iletisinin metnini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="50c03-251">Geliştiriciler, kullanıcının kültürüne bağlı olarak değişen hata iletilerinin metnine güvenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="50c03-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="50c03-252">❌**İzİn VERİlMEMİz: Yukarıda listelenmemiş başka bir durumda özel durum atma**</span><span class="sxs-lookup"><span data-stu-id="50c03-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="50c03-253">❌**İzİn VERİlMEMİz: Yukarıda listelenmemiş başka bir durumda bir özel durum kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="50c03-254">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="50c03-254">Attributes</span></span>

- <span data-ttu-id="50c03-255">✔️ **İzİn VERİlMEMİşTİr: Gözlemlenebilir *olmayan* bir özniteliğin değerini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="50c03-256">❌**İzin VERİlMEMİş: Gözlemlenebilir *is* bir özniteliğin değerini değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="50c03-257">❓ **YARGI GEREKTIRIR: Bir özniteliği kaldırma**</span><span class="sxs-lookup"><span data-stu-id="50c03-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="50c03-258">Çoğu durumda, bir öznitelik kaldırma <xref:System.NonSerializedAttribute>(gibi) bir kesme değişikliğidir.</span><span class="sxs-lookup"><span data-stu-id="50c03-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="50c03-259">Platform desteği</span><span class="sxs-lookup"><span data-stu-id="50c03-259">Platform support</span></span>

- <span data-ttu-id="50c03-260">✔️ **Izin verildi: Daha önce desteklenmeyen bir platformdaki bir operasyonu desteklemek**</span><span class="sxs-lookup"><span data-stu-id="50c03-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="50c03-261">❌**İzin VERİlMEMİş: Daha önce platformda desteklenen bir işlem için belirli bir hizmet paketini desteklememek veya şimdi gerektirmemek**</span><span class="sxs-lookup"><span data-stu-id="50c03-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="50c03-262">Dahili uygulama değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="50c03-262">Internal implementation changes</span></span>

- <span data-ttu-id="50c03-263">❓ **YARGI GEREKTIRIR: Bir iç tip yüzey alanı değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="50c03-264">Özel yansımayı kırsalar da, bu tür değişikliklere genellikle izin verilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="50c03-265">Popüler üçüncü taraf kitaplıklarının veya çok sayıda geliştiricinin dahili API'ler'e bağlı olduğu bazı durumlarda, bu tür değişikliklere izin verilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="50c03-266">❓ **KARAR GEREKTIRIR: Bir üyenin iç uygulama değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="50c03-267">Özel yansımayı kırsalar da, bu değişikliklere genellikle izin verilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="50c03-268">Müşteri kodunun sıklıkla özel yansımaya bağlı olduğu veya değişikliğin istenmeyen yan etkilere neden olduğu bazı durumlarda, bu değişikliklere izin verilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="50c03-269">✔️ **Izin: Bir operasyonun performansını artırmak**</span><span class="sxs-lookup"><span data-stu-id="50c03-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="50c03-270">Bir işlemin performansını değiştirme yeteneği önemlidir, ancak bu tür değişiklikler bir işlemin geçerli hızına dayanan kodu kırabilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="50c03-271">Bu, özellikle eşzamanlı işlemlerin zamanlamasına bağlı olarak kod için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="50c03-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="50c03-272">Performans değişikliğinin söz konusu API'nin diğer davranışları üzerinde hiçbir etkisi olmamalıdır; aksi takdirde, değişiklik kırılıyor olacak.</span><span class="sxs-lookup"><span data-stu-id="50c03-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="50c03-273">**✔️ Izin: Dolaylı olarak (ve genellikle olumsuz) bir operasyonun performansını değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="50c03-274">Söz konusu değişiklik başka bir nedenle kırılma olarak kategorize edilmezse, bu kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="50c03-275">Genellikle, ek işlemler içerebilir veya yeni işlevsellik eklemek eylemleri alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="50c03-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="50c03-276">Bu hemen hemen her zaman performansı etkileyecektir, ancak beklendiği gibi söz konusu API işlevi yapmak için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="50c03-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="50c03-277">❌**İzin VERİlMEZ: Senkron API'yi eşzamanlı olarak değiştirme (veya tam tersi)**</span><span class="sxs-lookup"><span data-stu-id="50c03-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="50c03-278">Kod değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="50c03-278">Code changes</span></span>

- <span data-ttu-id="50c03-279">**✔️ İzİn VERİlMESİ: Parametreye [param](../../csharp/language-reference/keywords/params.md) ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="50c03-280">❌**İzin VERİlMEMİş: Bir [yapıyı](../../csharp/language-reference/builtin-types/struct.md) [sınıfa](../../csharp/language-reference/keywords/class.md) değiştirme ve bunun tersi**</span><span class="sxs-lookup"><span data-stu-id="50c03-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="50c03-281">❌**İZIN VERİlMİş: [Denetlenen](../../csharp/language-reference/keywords/virtual.md) anahtar kelimeyi kod bloğuna ekleme**</span><span class="sxs-lookup"><span data-stu-id="50c03-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="50c03-282">Bu değişiklik, daha önce yürütülen <xref:System.OverflowException> kodun bir atamasına neden olabilir ve kabul edilemez.</span><span class="sxs-lookup"><span data-stu-id="50c03-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="50c03-283">❌**İzİn VERİlMESİ: [Parametreden paramların](../../csharp/language-reference/keywords/params.md) çıkarılması**</span><span class="sxs-lookup"><span data-stu-id="50c03-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="50c03-284">❌**İzİn VERİlMESİ: Olayların ateşlendiği sırayı değiştirme**</span><span class="sxs-lookup"><span data-stu-id="50c03-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="50c03-285">Geliştiriciler makul bir şekilde olayların aynı sırada ateş etmesini bekleyebilir ve geliştirici kodu sık sık olayların ateşlendiği sıraya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="50c03-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="50c03-286">❌**İzİn VERİlMEMİz: Belirli bir eylemde bir olayın yükseltilmesinin kaldırılması**</span><span class="sxs-lookup"><span data-stu-id="50c03-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="50c03-287">❌**İzin VERİlMEMİş: Verilen olayların kaç kez değiştirileceğinin değiştirilmesi**</span><span class="sxs-lookup"><span data-stu-id="50c03-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="50c03-288">❌**İzİn VERİlMESİn: Numaralandırma <xref:System.FlagsAttribute> türüne** ekleme</span><span class="sxs-lookup"><span data-stu-id="50c03-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
