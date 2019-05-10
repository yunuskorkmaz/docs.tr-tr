---
title: Yerel birlikte çalışabilirliği en iyi uygulamalar - .NET
description: . NET'te yerel bileşenleriyle arabirim için en iyi uygulamaları öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 09b25ed10958142f8eead6761f18bccbe2645448
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063088"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="18a23-103">Yerel birlikte çalışabilirliği en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="18a23-103">Native interoperability best practices</span></span>

<span data-ttu-id="18a23-104">.NET yerel birlikte çalışabilirliği kodunuzu özelleştirmek için yol çeşitli sağlar.</span><span class="sxs-lookup"><span data-stu-id="18a23-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="18a23-105">Bu makalede, Microsoft'un .NET ekipleri için yerel birlikte çalışabilirliği izleyin kılavuz içerir.</span><span class="sxs-lookup"><span data-stu-id="18a23-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="18a23-106">Genel rehber</span><span class="sxs-lookup"><span data-stu-id="18a23-106">General guidance</span></span>

<span data-ttu-id="18a23-107">Birlikte çalışma tüm senaryolarda bu bölümdeki yönergeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="18a23-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="18a23-108">**✔️ YAPMAK** yöntem ve parametreler için çağırmak istediğiniz yerel yöntemi olarak aynı adlandırma ve büyük/küçük harf kullanın.</span><span class="sxs-lookup"><span data-stu-id="18a23-108">**✔️ DO** use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="18a23-109">**✔️ DÜŞÜNÜN** aynı adlandırma ve büyük/küçük harf sabit değerleri için kullanma.</span><span class="sxs-lookup"><span data-stu-id="18a23-109">**✔️ CONSIDER** using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="18a23-110">**✔️ YAPMAK** yakın eşleme için yerel türü .NET türlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="18a23-110">**✔️ DO** use .NET types that map closest to the native type.</span></span> <span data-ttu-id="18a23-111">Örneğin, C#, kullanın `uint` yerel bir tür olduğunda `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="18a23-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="18a23-112">**✔️ YAPMAK** yalnızca `[In]` ve `[Out]` istediğiniz davranışı varsayılan davranışı farklılık gösterdiğinde öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="18a23-112">**✔️ DO** only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="18a23-113">**✔️ DÜŞÜNÜN** kullanarak <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> , yerel bir dizi arabellek havuzu için.</span><span class="sxs-lookup"><span data-stu-id="18a23-113">**✔️ CONSIDER** using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="18a23-114">**✔️ DÜŞÜNÜN** , P/Invoke bildirimleri ile aynı ada ve büyük/küçük harf, yerel kitaplık olarak sınıfında kaydırma.</span><span class="sxs-lookup"><span data-stu-id="18a23-114">**✔️ CONSIDER** wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="18a23-115">Böylece, `[DllImport]` öznitelikler C# `nameof` yerel kitaplık adını geçirin ve yerel kitaplık adını yazsanız yaramadı emin olmak için dil özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="18a23-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="18a23-116">DllImport özniteliği ayarları</span><span class="sxs-lookup"><span data-stu-id="18a23-116">DllImport attribute settings</span></span>

| <span data-ttu-id="18a23-117">Ayar</span><span class="sxs-lookup"><span data-stu-id="18a23-117">Setting</span></span> | <span data-ttu-id="18a23-118">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="18a23-118">Default</span></span> | <span data-ttu-id="18a23-119">Öneri</span><span class="sxs-lookup"><span data-stu-id="18a23-119">Recommendation</span></span> | <span data-ttu-id="18a23-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="18a23-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="18a23-121">Varsayılan koruyun</span><span class="sxs-lookup"><span data-stu-id="18a23-121">keep default</span></span>  | <span data-ttu-id="18a23-122">Bu açıkça false, başarısız HRESULT dönüş değerine ayarlandığında, özel durumları kapatılacak (ve sonuç olarak tanımındaki dönüş değeri null olur).</span><span class="sxs-lookup"><span data-stu-id="18a23-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="18a23-123">API'ye bağlıdır</span><span class="sxs-lookup"><span data-stu-id="18a23-123">depends on the API</span></span>  | <span data-ttu-id="18a23-124">Bunu Marshal.GetLastWin32Error değerini almak için kullanın ve API GetLastError kullanıyorsa true olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="18a23-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="18a23-125">API hata var olmadığını belirten bir koşul ayarlar, yanlışlıkla üzerine zorunda kalmamak için diğer aramaları yapmadan önce hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="18a23-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="18a23-126">`CharSet.None`, hangi gördükleri `CharSet.Ansi` davranışı</span><span class="sxs-lookup"><span data-stu-id="18a23-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="18a23-127">Açıkça kullanın `CharSet.Unicode` veya `CharSet.Ansi` dize ve karakter olduğunda tanımında mevcut</span><span class="sxs-lookup"><span data-stu-id="18a23-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="18a23-128">Bu dizeler ve hangi sıralama davranışını belirtir `ExactSpelling` ne zaman mu `false`.</span><span class="sxs-lookup"><span data-stu-id="18a23-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="18a23-129">Unutmayın `CharSet.Ansi` gerçekten UNIX üzerinde UTF8'dir.</span><span class="sxs-lookup"><span data-stu-id="18a23-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="18a23-130">_Çoğu_ UNIX UTF8 kullanırken saati Unicode Windows kullanır.</span><span class="sxs-lookup"><span data-stu-id="18a23-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="18a23-131">Daha fazla bilgi görmek [charsets belgelerine](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="18a23-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="18a23-132">Doğru ve çalışma zamanı değerine bağlı olarak bir "A" veya "W" soneki ile alternatif işlev adlarını aramaz gibi küçük bir performans kazancı elde etmek için bunu ayarlayın `CharSet` ayarı ("A" `CharSet.Ansi` ve "W" `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="18a23-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="18a23-133">Dizesi parametreleri</span><span class="sxs-lookup"><span data-stu-id="18a23-133">String parameters</span></span>

<span data-ttu-id="18a23-134">Ne zaman karakter Unicode veya bağımsız değişken olarak açıkça işaretlenmiş `[MarshalAs(UnmanagedType.LPWSTR)]` _ve_ dizeyi değere göre geçirilir (değil `ref` veya `out`), dize sabitlenebilir ve doğrudan yerel kod tarafından kullanılan (yerine kopyalandı).</span><span class="sxs-lookup"><span data-stu-id="18a23-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="18a23-135">İşaretlenecek unutmayın `[DllImport]` olarak `Charset.Unicode` , dizeleri ANSI işleme açıkça istemediğiniz sürece.</span><span class="sxs-lookup"><span data-stu-id="18a23-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="18a23-136">**❌ SAĞLAMADIĞI** kullanın `[Out] string` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="18a23-136">**❌ DO NOT** use `[Out] string` parameters.</span></span> <span data-ttu-id="18a23-137">Dize değeri ile tarafından geçirilen parametreler `[Out]` dize interned bir dize ise, öznitelik çalışma zamanı kararlılığını.</span><span class="sxs-lookup"><span data-stu-id="18a23-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="18a23-138">Belgelerindeki dize kopyası kullanımı hakkında daha fazla bilgi <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="18a23-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="18a23-139">**❌ KAÇININ** `StringBuilder` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="18a23-139">**❌ AVOID** `StringBuilder` parameters.</span></span> <span data-ttu-id="18a23-140">`StringBuilder` hazırlama *her zaman* yerel arabellek kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18a23-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="18a23-141">Bu nedenle, son derece verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="18a23-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="18a23-142">Bir dize alır bir Windows API'si çağırma tipik bir senaryo uygulayın:</span><span class="sxs-lookup"><span data-stu-id="18a23-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="18a23-143">Bir SB (yönetilen kapasite ayırır) istenen kapasite oluşturma **{1}**</span><span class="sxs-lookup"><span data-stu-id="18a23-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="18a23-144">Çağır</span><span class="sxs-lookup"><span data-stu-id="18a23-144">Invoke</span></span>
   1. <span data-ttu-id="18a23-145">Yerel bir arabelleği ayırır **{2}**</span><span class="sxs-lookup"><span data-stu-id="18a23-145">Allocates a native buffer **{2}**</span></span>  
   2. <span data-ttu-id="18a23-146">İçeriği kopyalar `[In]` _(için varsayılan bir `StringBuilder` parametresi)_</span><span class="sxs-lookup"><span data-stu-id="18a23-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>  
   3. <span data-ttu-id="18a23-147">Yerel arabellek yönetilen yeni ayrılan bir diziye kopyalar `[Out]` **{3}** _(aynı zamanda varsayılan `StringBuilder`)_</span><span class="sxs-lookup"><span data-stu-id="18a23-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>  
3. <span data-ttu-id="18a23-148">`ToString()` henüz başka yönetilen diziye ayırır **{4}**</span><span class="sxs-lookup"><span data-stu-id="18a23-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="18a23-149">Diğer bir deyişle *{4}* yerel kodunun dışında bir dizesini almak için ayırma.</span><span class="sxs-lookup"><span data-stu-id="18a23-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="18a23-150">Yeniden kullanmak için bunu sınırlandırmak için yapabileceğiniz en iyi olduğu `StringBuilder` başka bir çağrı ancak yine de yalnızca kazandırır *1* ayırma.</span><span class="sxs-lookup"><span data-stu-id="18a23-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="18a23-151">Karakter arabellek önbellek ve kullanmak çok daha iyi `ArrayPool`-ardından ayırma için ulaşmak için `ToString()` arka arkaya çağrı.</span><span class="sxs-lookup"><span data-stu-id="18a23-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="18a23-152">Diğer sorun `StringBuilder` olduğundan, her zaman ilk null kadar geri dönüş arabelleğine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="18a23-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="18a23-153">Geçirilen geri dizeyi sonlandırılmış değil veya çift null ile sonlandırılmış bir dize ise, P/Invoke en iyi şekilde doğru değil.</span><span class="sxs-lookup"><span data-stu-id="18a23-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="18a23-154">Varsa, *yapmak* kullanın `StringBuilder`, bir son sorunu olan kapasite uğramadığını **değil** her zaman için birlikte çalışabilirlik alındığından bir gizli null içerir.</span><span class="sxs-lookup"><span data-stu-id="18a23-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="18a23-155">Arabellek boyutu çoğu API'ler istediğiniz gibi yanlış bu kişiler için ortak olan *dahil olmak üzere* null.</span><span class="sxs-lookup"><span data-stu-id="18a23-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="18a23-156">Bu boşa/gereksiz ayırmaları sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="18a23-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="18a23-157">Ayrıca, bu sorunu en iyi duruma getirmesini çalışma zamanı engeller `StringBuilder` kopyaları en aza indirmek için hazırlama.</span><span class="sxs-lookup"><span data-stu-id="18a23-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="18a23-158">**✔️ DÜŞÜNÜN** kullanarak `char[]`s bir `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="18a23-158">**✔️ CONSIDER** using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="18a23-159">Dize sıralama ile ilgili daha fazla bilgi için bkz: [dizeler için varsayılan hazırlama](../../framework/interop/default-marshaling-for-strings.md) ve [dize sıralama özelleştirme](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="18a23-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="18a23-160">__Windows özel__</span><span class="sxs-lookup"><span data-stu-id="18a23-160">__Windows Specific__</span></span>  
> <span data-ttu-id="18a23-161">İçin `[Out]` CLR dizeleri kullanacağı `CoTaskMemFree` boş dizeler için varsayılan veya `SysStringFree` olarak işaretlenmiş dizeler `UnmanagedType.BSTR`.</span><span class="sxs-lookup"><span data-stu-id="18a23-161">For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>  
<span data-ttu-id="18a23-162">**Bir çıkış dizesi arabelleği ile çoğu API'ler için:**</span><span class="sxs-lookup"><span data-stu-id="18a23-162">**For most APIs with an output string buffer:**</span></span>  
> <span data-ttu-id="18a23-163">Geçirilen null karakter sayısı içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a23-163">The passed in character count must include the null.</span></span> <span data-ttu-id="18a23-164">Döndürülen değer geçirilen küçükse karakter sayısına çağrısı başarılı oldu ve karakter sayısını değerdir *olmadan* sondaki null.</span><span class="sxs-lookup"><span data-stu-id="18a23-164">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="18a23-165">Aksi takdirde sayısı gerekli arabellek boyutu: *dahil olmak üzere* null karakteri.</span><span class="sxs-lookup"><span data-stu-id="18a23-165">Otherwise the count is the required size of the buffer *including* the null character.</span></span>  
> - <span data-ttu-id="18a23-166">5'te geçmek için 4 alın: 4 dizedir ile uzun sondaki null karakter.</span><span class="sxs-lookup"><span data-stu-id="18a23-166">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="18a23-167">5'te geçmek için 6 alın: Bir dizedir 5 karakter uzunluğunda olmalı, boş tutmak için 6 karakter arabelleği gerekir.</span><span class="sxs-lookup"><span data-stu-id="18a23-167">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>  
> [<span data-ttu-id="18a23-168">Windows veri türleri için dizeleri</span><span class="sxs-lookup"><span data-stu-id="18a23-168">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="18a23-169">Boole parametreler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="18a23-169">Boolean parameters and fields</span></span>

<span data-ttu-id="18a23-170">Boole değerlerini uğraşmanız kolaydır.</span><span class="sxs-lookup"><span data-stu-id="18a23-170">Booleans are easy to mess up.</span></span> <span data-ttu-id="18a23-171">Varsayılan olarak, bir .NET `bool` için bir Windows sıralanmış `BOOL`, bir 4 baytlık değer olduğu.</span><span class="sxs-lookup"><span data-stu-id="18a23-171">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="18a23-172">Ancak, `_Bool`, ve `bool` türleri C ve C++'ta bir *tek* bayt.</span><span class="sxs-lookup"><span data-stu-id="18a23-172">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="18a23-173">Bu sabit yarı dönüş değeri, hangi yalnızca atılacak olarak hataları izlemek için açabilir *potansiyel olarak* sonucu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="18a23-173">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="18a23-174">.NET hazırlama hakkında bilgi için daha fazla bilgi için `bool` C değerleri veya C++ `bool` türleri, şirket belgelerine bakın [Boole alanı hazırlama özelleştirme](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="18a23-174">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="18a23-175">GUID'ler</span><span class="sxs-lookup"><span data-stu-id="18a23-175">GUIDs</span></span>

<span data-ttu-id="18a23-176">GUID'ler, dosyalardaki imzaları doğrudan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18a23-176">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="18a23-177">Birçok Windows apı'lerinizle `GUID&` tür diğer adları gibi `REFIID`.</span><span class="sxs-lookup"><span data-stu-id="18a23-177">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="18a23-178">Başvuru tarafından geçirilen, bunlar ya da geçirilebilir `ref` veya `[MarshalAs(UnmanagedType.LPStruct)]` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="18a23-178">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="18a23-179">GUID</span><span class="sxs-lookup"><span data-stu-id="18a23-179">GUID</span></span> | <span data-ttu-id="18a23-180">Başvuru tarafından GUID</span><span class="sxs-lookup"><span data-stu-id="18a23-180">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="18a23-181">**❌ SAĞLAMADIĞI** kullanım `[MarshalAs(UnmanagedType.LPStruct)]` dışındaki her şey için `ref` GUID parametreleri.</span><span class="sxs-lookup"><span data-stu-id="18a23-181">**❌ DO NOT** Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="18a23-182">Blok halinde kopyalanabilir türler</span><span class="sxs-lookup"><span data-stu-id="18a23-182">Blittable types</span></span>

<span data-ttu-id="18a23-183">Blittable türleri aynı bit düzeyinde gösterimine sahip yönetilen ve yerel kodda türleridir.</span><span class="sxs-lookup"><span data-stu-id="18a23-183">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="18a23-184">Bu nedenle bunlar için ve yerel koddan sıralanması başka bir biçime dönüştürülüp gerekmez ve bu performansı artırmak amacıyla, tercih edilen olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18a23-184">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="18a23-185">**Blittable türleri:**</span><span class="sxs-lookup"><span data-stu-id="18a23-185">**Blittable types:**</span></span>

- <span data-ttu-id="18a23-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="18a23-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="18a23-187">iç içe olmayan tek boyutlu diziler blittable türleri (örneğin, `int[]`)</span><span class="sxs-lookup"><span data-stu-id="18a23-187">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="18a23-188">yapıları ve sınıfları sabit düzen ile yalnızca blittable değere sahip türleri örneği için alanları</span><span class="sxs-lookup"><span data-stu-id="18a23-188">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="18a23-189">Sabit Düzen gerektirir `[StructLayout(LayoutKind.Sequential)]` veya `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="18a23-189">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="18a23-190">Yapı birimleridir `LayoutKind.Sequential` varsayılan olarak, sınıflardır. `LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="18a23-190">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="18a23-191">**Blittable değil:**</span><span class="sxs-lookup"><span data-stu-id="18a23-191">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="18a23-192">**BAZEN blittable:**</span><span class="sxs-lookup"><span data-stu-id="18a23-192">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="18a23-193">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="18a23-193">`char`, `string`</span></span>

<span data-ttu-id="18a23-194">Blittable türleri başvuruya göre geçirildiğinde, bunlar yalnızca bir ara arabelleğe kopyalanan yerine marshaller tarafından sabitlenmiş.</span><span class="sxs-lookup"><span data-stu-id="18a23-194">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="18a23-195">(Sınıflar kendiliğinden başvuruya göre geçirilen, yapılar ile kullanıldığında başvuruyla geçirilir `ref` veya `out`.)</span><span class="sxs-lookup"><span data-stu-id="18a23-195">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="18a23-196">`char` Blittable bir tek boyutlu dizisi olan **veya** parçası ise onu içeren bir türe açıkça ile işaretlenmiş `[StructLayout]` ile `CharSet = CharSet.Unicode`.</span><span class="sxs-lookup"><span data-stu-id="18a23-196">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="18a23-197">`string` Blittable başka bir tür içinde yer alan değildir ve bu ile işaretlenmiş bir bağımsız değişken olarak Geçirilmekte olan `[MarshalAs(UnmanagedType.LPWStr)]` veya `[DllImport]` sahip `CharSet = CharSet.Unicode` ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="18a23-197">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="18a23-198">Sabitlenmiş oluşturulmaya çalışılırken tarafından bir türü blok halinde kopyalanabilir olup olmadığını görebilirsiniz `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="18a23-198">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="18a23-199">Türü bir dize değilse veya kabul blittable, `GCHandle.Alloc` oluşturmaz bir `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="18a23-199">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="18a23-200">**✔️ YAPMAK** mümkün olduğunda, yapıları blittable olun.</span><span class="sxs-lookup"><span data-stu-id="18a23-200">**✔️ DO** make your structures blittable when possible.</span></span>

<span data-ttu-id="18a23-201">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="18a23-201">For more information, see:</span></span>

- [<span data-ttu-id="18a23-202">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="18a23-202">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)  
- [<span data-ttu-id="18a23-203">Sıralama türü</span><span class="sxs-lookup"><span data-stu-id="18a23-203">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="18a23-204">Canlı tutma yönetilen nesneler</span><span class="sxs-lookup"><span data-stu-id="18a23-204">Keeping managed objects alive</span></span>

<span data-ttu-id="18a23-205">`GC.KeepAlive()` KeepAlive yöntemi isabet kadar nesne kapsam içinde kalır sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="18a23-205">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="18a23-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) bir nesne bir P/Invoke süresi boyunca Canlı tutmak marshaller sağlar.</span><span class="sxs-lookup"><span data-stu-id="18a23-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="18a23-207">Yerine kullanılabilir `IntPtr` yöntem imzaları içinde.</span><span class="sxs-lookup"><span data-stu-id="18a23-207">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="18a23-208">`SafeHandle` etkili bir şekilde bu sınıfı değiştirir ve bunun yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18a23-208">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="18a23-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) yönetilen bir nesnenin sabitleme ve yerel işaretçi kendisine alma sağlar.</span><span class="sxs-lookup"><span data-stu-id="18a23-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="18a23-210">Temel modelidir:</span><span class="sxs-lookup"><span data-stu-id="18a23-210">The basic pattern is:</span></span>  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="18a23-211">İçin varsayılan olmayan sabitleme `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="18a23-211">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="18a23-212">Diğer önemli bir başvuru yerel kod aracılığıyla yönetilen bir nesne ve genellikle bir geri çağırma ile yönetilen kod için geri geçirmek için modelidir.</span><span class="sxs-lookup"><span data-stu-id="18a23-212">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="18a23-213">Bu düzen aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="18a23-213">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="18a23-214">Gerektiğini unutmayın `GCHandle` bellek sızıntılarını önlemek için açıkça boşaltılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="18a23-214">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="18a23-215">Ortak Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="18a23-215">Common Windows data types</span></span>

<span data-ttu-id="18a23-216">İşte sık kullanılan Windows API'leri ve hangi veri türlerinin bir listesi C# Windows koda çağrılırken kullanılacak türleri.</span><span class="sxs-lookup"><span data-stu-id="18a23-216">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="18a23-217">Aynı boyutta adlarını rağmen 32-bit ve 64-bit Windows üzerinde türleridir.</span><span class="sxs-lookup"><span data-stu-id="18a23-217">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="18a23-218">Genişlik</span><span class="sxs-lookup"><span data-stu-id="18a23-218">Width</span></span> | <span data-ttu-id="18a23-219">Windows</span><span class="sxs-lookup"><span data-stu-id="18a23-219">Windows</span></span>          | <span data-ttu-id="18a23-220">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="18a23-220">C (Windows)</span></span>          | <span data-ttu-id="18a23-221">C#</span><span class="sxs-lookup"><span data-stu-id="18a23-221">C#</span></span>       | <span data-ttu-id="18a23-222">Alternatif</span><span class="sxs-lookup"><span data-stu-id="18a23-222">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="18a23-223">32</span><span class="sxs-lookup"><span data-stu-id="18a23-223">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="18a23-224">8</span><span class="sxs-lookup"><span data-stu-id="18a23-224">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="18a23-225">8</span><span class="sxs-lookup"><span data-stu-id="18a23-225">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="18a23-226">8</span><span class="sxs-lookup"><span data-stu-id="18a23-226">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="18a23-227">8</span><span class="sxs-lookup"><span data-stu-id="18a23-227">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="18a23-228">16</span><span class="sxs-lookup"><span data-stu-id="18a23-228">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="18a23-229">16</span><span class="sxs-lookup"><span data-stu-id="18a23-229">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="18a23-230">16</span><span class="sxs-lookup"><span data-stu-id="18a23-230">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="18a23-231">16</span><span class="sxs-lookup"><span data-stu-id="18a23-231">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="18a23-232">16</span><span class="sxs-lookup"><span data-stu-id="18a23-232">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="18a23-233">32</span><span class="sxs-lookup"><span data-stu-id="18a23-233">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="18a23-234">32</span><span class="sxs-lookup"><span data-stu-id="18a23-234">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="18a23-235">32</span><span class="sxs-lookup"><span data-stu-id="18a23-235">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="18a23-236">32</span><span class="sxs-lookup"><span data-stu-id="18a23-236">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="18a23-237">64</span><span class="sxs-lookup"><span data-stu-id="18a23-237">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="18a23-238">64</span><span class="sxs-lookup"><span data-stu-id="18a23-238">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="18a23-239">64</span><span class="sxs-lookup"><span data-stu-id="18a23-239">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="18a23-240">64</span><span class="sxs-lookup"><span data-stu-id="18a23-240">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="18a23-241">64</span><span class="sxs-lookup"><span data-stu-id="18a23-241">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="18a23-242">32</span><span class="sxs-lookup"><span data-stu-id="18a23-242">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="18a23-243">32</span><span class="sxs-lookup"><span data-stu-id="18a23-243">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="18a23-244">İşaretçisi olan aşağıdaki türleri, platform genişliğini izleyin.</span><span class="sxs-lookup"><span data-stu-id="18a23-244">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="18a23-245">Kullanım `IntPtr` / `UIntPtr` bu.</span><span class="sxs-lookup"><span data-stu-id="18a23-245">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="18a23-246">İşaretçi türleri imzalı (kullanın `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="18a23-246">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="18a23-247">İşaretsiz işaretçi türleri (kullanın `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="18a23-247">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="18a23-248">Bir Windows `PVOID` C olduğu `void*` olarak sıralanabilir `IntPtr` veya `UIntPtr`, ancak tercih `void*` mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="18a23-248">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="18a23-249">Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="18a23-249">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="18a23-250">Veri Türü Aralıkları</span><span class="sxs-lookup"><span data-stu-id="18a23-250">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="18a23-251">Yapılar</span><span class="sxs-lookup"><span data-stu-id="18a23-251">Structs</span></span>

<span data-ttu-id="18a23-252">Yönetilen yapıları yığında oluşturulur ve yöntem dönene kadar kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="18a23-252">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="18a23-253">Ardından tanımı gereği, bunlar "Sabitlenen" (atık toplama tarafından taşınması gerekmez).</span><span class="sxs-lookup"><span data-stu-id="18a23-253">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="18a23-254">Yerel kod geçerli yönteminin sonuna işaretçiyi kullanmaz, blok içinde güvenli olmayan kod adresi kısaca alabilir.</span><span class="sxs-lookup"><span data-stu-id="18a23-254">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="18a23-255">Blok halinde kopyalanabilir, yalnızca doğrudan hazırlama katmanı tarafından kullanılabilmesi için çok daha yüksek performanslı birimleridir.</span><span class="sxs-lookup"><span data-stu-id="18a23-255">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="18a23-256">Yapılar blittable yapmayı denerseniz (örneğin, kaçının `bool`).</span><span class="sxs-lookup"><span data-stu-id="18a23-256">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="18a23-257">Daha fazla bilgi için [türlerse](#blittable-types) bölümü.</span><span class="sxs-lookup"><span data-stu-id="18a23-257">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="18a23-258">*Varsa* blittable struct, kullanın `sizeof()` yerine `Marshal.SizeOf<MyStruct>()` daha iyi performans için.</span><span class="sxs-lookup"><span data-stu-id="18a23-258">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="18a23-259">Yukarıda belirtildiği gibi bir sabitlenmiş oluşturulmaya çalışılırken tarafından türü blittable olduğunu doğrulayabilirsiniz `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="18a23-259">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="18a23-260">Türü bir dize değilse veya kabul blittable, `GCHandle.Alloc` oluşturmaz bir `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="18a23-260">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="18a23-261">Yapılar tanımlarında işaretçileri ya da geçirilmelidir `ref` veya `unsafe` ve `*`.</span><span class="sxs-lookup"><span data-stu-id="18a23-261">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="18a23-262">**✔️ YAPMAK** yönetilen yapı şekil ve resmi platformu belgeleri veya üstbilgi kullanılan adları için mümkün olduğunca aynı.</span><span class="sxs-lookup"><span data-stu-id="18a23-262">**✔️ DO** match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="18a23-263">**✔️ YAPMAK** kullanın C# `sizeof()` yerine `Marshal.SizeOf<MyStruct>()` performansını artırmak blittable yapıları için.</span><span class="sxs-lookup"><span data-stu-id="18a23-263">**✔️ DO** use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="18a23-264">Bir dizi ister `INT_PTR Reserved1[2]` iki olarak sıralanması gereken `IntPtr` alanları `Reserved1a` ve `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="18a23-264">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="18a23-265">Yerel bir dizi temel bir tür olduğunda, kullanabiliriz `fixed` biraz daha temiz bir şekilde yazmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="18a23-265">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="18a23-266">Örneğin, `SYSTEM_PROCESS_INFORMATION` şöyle görünür yerel başlığı:</span><span class="sxs-lookup"><span data-stu-id="18a23-266">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="18a23-267">İçinde C#, şöyle yazabiliriz:</span><span class="sxs-lookup"><span data-stu-id="18a23-267">In C#, we can write it like this:</span></span>

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

<span data-ttu-id="18a23-268">Ancak, bazı tuzakları sabit arabellekler ile vardır.</span><span class="sxs-lookup"><span data-stu-id="18a23-268">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="18a23-269">Yerinde dizi kullanıma birden çok ayrı ayrı alanlara genişletilmesi gerekir kopyalanamaz türler, sabit arabellekleri doğru sıralanması olmaz.</span><span class="sxs-lookup"><span data-stu-id="18a23-269">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="18a23-270">Bir sabit arabellek alanı içeren bir yapı kopyalanamaz yapı birimi içinde iç içe ek olarak, .NET Framework ve .NET Core 3.0 önce sabit arabellek alanı doğru yerel kod olarak sıralanması olmaz.</span><span class="sxs-lookup"><span data-stu-id="18a23-270">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
