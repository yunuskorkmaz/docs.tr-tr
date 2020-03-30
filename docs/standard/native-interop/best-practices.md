---
title: Yerli birlikte çalışabilirlik en iyi uygulamalar - .NET
description: .NET'te yerel bileşenlerle etkileşim için en iyi uygulamaları öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391227"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="e55e5-103">Yerel birlikte çalışabilirlik en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="e55e5-103">Native interoperability best practices</span></span>

<span data-ttu-id="e55e5-104">.NET, yerel birlikte çalışabilirlik kodunuzu özelleştirmeniz için çeşitli yollar sunar.</span><span class="sxs-lookup"><span data-stu-id="e55e5-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="e55e5-105">Bu makalede, Microsoft'un .NET ekiplerinin yerel birlikte çalışabilirlik için izlediği kılavuz yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="e55e5-106">Genel rehber</span><span class="sxs-lookup"><span data-stu-id="e55e5-106">General guidance</span></span>

<span data-ttu-id="e55e5-107">Bu bölümdeki kılavuz tüm interop senaryoları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="e55e5-108">✔️ DO, aramak istediğiniz yerel yöntemle yöntemleriniz ve parametreleriniz için aynı adlandırma ve büyük harf kullanır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="e55e5-109">✔️ sabit değerler için aynı adlandırma ve büyük harf kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e55e5-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="e55e5-110">✔️ DO, yerel türe en yakın eşlenebilen .NET türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="e55e5-111">Örneğin, C#'da, `uint` yerel tür `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="e55e5-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="e55e5-112">✔️ yalnızca `[In]` istediğiniz `[Out]` davranış varsayılan davranıştan farklı olduğunda kullanın ve öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e55e5-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="e55e5-113">✔️ yerel <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> dizi arabelleklerinizi bir araya getirmek için kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e55e5-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="e55e5-114">✔️ P/Invoke bildirimlerinizi yerel kitaplığınız ile aynı ada ve büyük harfe sahip bir sınıfa sarmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e55e5-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="e55e5-115">Bu, `[DllImport]` özniteliklerinizin yerel `nameof` kitaplığın adına geçmek ve yerel kitaplığın adını yanlış yazmadığınızdan emin olmak için C# dil özelliğini kullanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="e55e5-116">DllImport öznitelik ayarları</span><span class="sxs-lookup"><span data-stu-id="e55e5-116">DllImport attribute settings</span></span>

| <span data-ttu-id="e55e5-117">Ayar</span><span class="sxs-lookup"><span data-stu-id="e55e5-117">Setting</span></span> | <span data-ttu-id="e55e5-118">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="e55e5-118">Default</span></span> | <span data-ttu-id="e55e5-119">Öneri</span><span class="sxs-lookup"><span data-stu-id="e55e5-119">Recommendation</span></span> | <span data-ttu-id="e55e5-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e55e5-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="e55e5-121">varsayılan tutma</span><span class="sxs-lookup"><span data-stu-id="e55e5-121">keep default</span></span>  | <span data-ttu-id="e55e5-122">Bu açıkça yanlış olarak ayarlandığında, başarısız HRESULT iade değerleri özel durumlara dönüştürülür (ve tanımdaki iade değeri sonuç olarak null olur).</span><span class="sxs-lookup"><span data-stu-id="e55e5-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="e55e5-123">API bağlıdır</span><span class="sxs-lookup"><span data-stu-id="e55e5-123">depends on the API</span></span>  | <span data-ttu-id="e55e5-124">API GetLastError kullanıyorsa bunu doğru olarak ayarlayın ve değeri almak için Marshal.GetLastWin32Error'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="e55e5-125">API bir hata olduğunu söyleyen bir koşul ayarlarsa, yanlışlıkla üzerine yazılmasını önlemek için diğer aramaları yapmadan önce hatayı alın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="e55e5-126">`CharSet.None`, davranışa `CharSet.Ansi` geri döner</span><span class="sxs-lookup"><span data-stu-id="e55e5-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="e55e5-127">Tanımda `CharSet.Unicode` açıkça `CharSet.Ansi` veya dizeleri veya karakterleri mevcut olduğunda</span><span class="sxs-lookup"><span data-stu-id="e55e5-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="e55e5-128">Bu dizeleri mareşal davranışını `ExactSpelling` belirtir `false`ve ne zaman .</span><span class="sxs-lookup"><span data-stu-id="e55e5-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="e55e5-129">Unix'te utf8 olduğunu `CharSet.Ansi` unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="e55e5-130">_Unix_ UTF8 kullanırken Çoğu zaman Windows Unicode kullanır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="e55e5-131">[Charsets üzerinde belgeler](./charset.md)hakkında daha fazla bilgi bakın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="e55e5-132">Çalışma zamanı `CharSet` ayarın değerine bağlı olarak "A" veya "W" soneki ("A" için `CharSet.Ansi` ve "W" için) ile alternatif işlev adları aramaz gibi bunu doğru ayarlayın ve hafif bir perf yararı elde edin. `CharSet.Unicode`</span><span class="sxs-lookup"><span data-stu-id="e55e5-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="e55e5-133">Dize parametreleri</span><span class="sxs-lookup"><span data-stu-id="e55e5-133">String parameters</span></span>

<span data-ttu-id="e55e5-134">CharSet Unicode olduğunda veya bağımsız değişken açıkça `[MarshalAs(UnmanagedType.LPWSTR)]` olarak işaretlendiğinde _ve_ dize `out`değere göre geçirildiğinde (değil veya), `ref` dize sabitlenir ve doğrudan yerel kod tarafından kullanılır (kopyalanmak yerine).</span><span class="sxs-lookup"><span data-stu-id="e55e5-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="e55e5-135">`[DllImport]` Dizelerinizin `Charset.Unicode` ANSI tedavisini açıkça istemediğiniz sürece işaretlemeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="e55e5-136">❌PARAMETRELERİ `[Out] string` KULLANMAYIN.</span><span class="sxs-lookup"><span data-stu-id="e55e5-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="e55e5-137">Dize interned dize ise öznitelik ile `[Out]` değer tarafından geçirilen dize parametreleri çalışma süresini bozabilir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="e55e5-138">Için belgelerde dize stajı <xref:System.String.Intern%2A?displayProperty=nameWithType>hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e55e5-139">❌PARAMETRELERDEN KAÇıN. `StringBuilder`</span><span class="sxs-lookup"><span data-stu-id="e55e5-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="e55e5-140">`StringBuilder`mareşallik *her zaman* yerel bir arabellek kopyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e55e5-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="e55e5-141">Bu nedenle, son derece verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="e55e5-142">Dize alan bir Windows API'yi arama nın tipik senaryosunu ele alalım:</span><span class="sxs-lookup"><span data-stu-id="e55e5-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="e55e5-143">İstenilen kapasitede bir SB oluşturma (yönetilen kapasiteyi tahsis eder)**{1}**</span><span class="sxs-lookup"><span data-stu-id="e55e5-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="e55e5-144">Çağır</span><span class="sxs-lookup"><span data-stu-id="e55e5-144">Invoke</span></span>
   1. <span data-ttu-id="e55e5-145">Yerel arabellek ayırır**{2}**</span><span class="sxs-lookup"><span data-stu-id="e55e5-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="e55e5-146">Eğer içeriği `[In]` kopyalar _(parametre `StringBuilder` için varsayılan)_</span><span class="sxs-lookup"><span data-stu-id="e55e5-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="e55e5-147">Yerel arabelleği yeni ayrılan yönetilen bir `[Out]` **{3}** diziye kopyalar _(ayrıca `StringBuilder`varsayılan)_</span><span class="sxs-lookup"><span data-stu-id="e55e5-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="e55e5-148">`ToString()`başka bir yönetilen dizi ayırır**{4}**</span><span class="sxs-lookup"><span data-stu-id="e55e5-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="e55e5-149">Bu, *{4}* yerel koddan bir dize çıkarmak için ayırmalar.</span><span class="sxs-lookup"><span data-stu-id="e55e5-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="e55e5-150">Bunu sınırlamak için yapabileceğiniz en iyi şey `StringBuilder` başka bir aramayı yeniden kullanmaktır, ancak bu yine de yalnızca *1* ayırma kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e55e5-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="e55e5-151">Bir karakter arabelleğini kullanmak ve önbelleğe `ArrayPool`almak çok daha iyidir - daha `ToString()` sonra sonraki aramalariçin sadece tahsisata inebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="e55e5-152">Diğer `StringBuilder` bir sorun ise, iade arabelleği her zaman ilk null'a kadar kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e55e5-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="e55e5-153">Geçirilen geri dize sonlandırılmazsa veya çift null-sonlandırılan dize ise, P/Invoke'ınız en iyi şekilde yanlıştır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="e55e5-154">*Eğer* kullanırsanız `StringBuilder`, son bir gotcha kapasite her zaman interop için muhasebeleştirilmiş gizli bir null, **içermemelidir.**</span><span class="sxs-lookup"><span data-stu-id="e55e5-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="e55e5-155">Çoğu API null *dahil* arabellek boyutunu istediğiniz gibi insanların bu yanlış almak için yaygındır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="e55e5-156">Bu, boşa/gereksiz ayırmalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="e55e5-157">Ayrıca, bu gotcha kopyaları en aza `StringBuilder` indirmek için mareşal optimize çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="e55e5-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="e55e5-158">✔️ s `char[]`kullanarak `ArrayPool`DÜŞÜNÜN bir .</span><span class="sxs-lookup"><span data-stu-id="e55e5-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="e55e5-159">Dize mareşalliği hakkında daha fazla bilgi için, [Strings için Varsayılan Mareşalve](../../framework/interop/default-marshaling-for-strings.md) [Özelleştirstring mareşalleme](customize-parameter-marshaling.md#customizing-string-parameters)bakın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="e55e5-160">__Windows'a Özel__ `[Out]` Dizeleri için CLR `CoTaskMemFree` varsayılan olarak serbest dizeleri veya `SysStringFree` olarak `UnmanagedType.BSTR`işaretlenmiş dizeleri için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="e55e5-161">**Çıktı dize arabelleği olan çoğu API için:** Karakter sayısında geçen null içermelidir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="e55e5-162">Döndürülen değer karakter sayısında geçirilenden daha azsa, çağrı başarılı oldu ve değer, azalan null *olmayan* karakter sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="e55e5-163">Aksi takdirde sayım, null karakteri *de dahil olmak üzere* arabelleğe gereken boyuttur.</span><span class="sxs-lookup"><span data-stu-id="e55e5-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="e55e5-164">5 pass, 4 olsun: dize bir iz null ile 4 karakter uzunluğundadır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="e55e5-165">Pass 5, 6 olsun: dize 5 karakter uzunluğunda, null tutmak için 6 karakter arabellek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="e55e5-166">Dizeleri için Windows Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="e55e5-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="e55e5-167">Boolean parametreleri ve alanları</span><span class="sxs-lookup"><span data-stu-id="e55e5-167">Boolean parameters and fields</span></span>

<span data-ttu-id="e55e5-168">Booleans berbat etmek kolaydır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="e55e5-169">Varsayılan olarak, bir `bool` .NET, 4 `BOOL`bayt değerinde olan bir Windows'a marshaled.</span><span class="sxs-lookup"><span data-stu-id="e55e5-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="e55e5-170">Ancak, `_Bool`C `bool` ve C++'daki , ve türleri *tek* bir baytdır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="e55e5-171">Bu, geri dönüş değerinin yarısı atıldığından hataların izlenmesi zor olabilir ve bu da sonucu *yalnızca değiştirebilir.*</span><span class="sxs-lookup"><span data-stu-id="e55e5-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="e55e5-172">.NET `bool` değerlerini C veya C++ `bool` türlerine göre mareşalleme hakkında daha fazla bilgi için [boolean mareşallemesini özelleştirmeyle](customize-struct-marshaling.md#customizing-boolean-field-marshaling)ilgili belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="e55e5-173">Guıd</span><span class="sxs-lookup"><span data-stu-id="e55e5-173">GUIDs</span></span>

<span data-ttu-id="e55e5-174">GUID'ler doğrudan imzalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="e55e5-175">Birçok Windows API's i `REFIID`gibi `GUID&` tür takma alır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="e55e5-176">Ref tarafından geçirildiğinde, onlar ya `ref` tarafından `[MarshalAs(UnmanagedType.LPStruct)]` geçirilebilir ya da özniteliği ile.</span><span class="sxs-lookup"><span data-stu-id="e55e5-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="e55e5-177">GUID</span><span class="sxs-lookup"><span data-stu-id="e55e5-177">GUID</span></span> | <span data-ttu-id="e55e5-178">By-ref GUID</span><span class="sxs-lookup"><span data-stu-id="e55e5-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="e55e5-179">❌GUID parametreleri dışında `[MarshalAs(UnmanagedType.LPStruct)]` `ref` başka bir şey için KULLANMAYIN.</span><span class="sxs-lookup"><span data-stu-id="e55e5-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="e55e5-180">Blittable türleri</span><span class="sxs-lookup"><span data-stu-id="e55e5-180">Blittable types</span></span>

<span data-ttu-id="e55e5-181">Blittable türleri yönetilen ve yerel kod aynı bit düzeyi gösterimi olan türleridir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="e55e5-182">Bu nedenle, yerel koda ve yerel koddan mareşalolmak üzere başka bir biçime dönüştürülmelerine gerek yoktur ve bu performansı artırdığı için tercih edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="e55e5-183">**Blittable türleri:**</span><span class="sxs-lookup"><span data-stu-id="e55e5-183">**Blittable types:**</span></span>

- <span data-ttu-id="e55e5-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="e55e5-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="e55e5-185">blittable türleri iç içe olmayan tek boyutlu diziler `int[]`(örneğin, )</span><span class="sxs-lookup"><span data-stu-id="e55e5-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="e55e5-186">örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzene sahip yapı ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="e55e5-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="e55e5-187">sabit düzen `[StructLayout(LayoutKind.Sequential)]` gerektirir veya`[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="e55e5-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="e55e5-188">structs `LayoutKind.Sequential` varsayılan olarak, sınıflar`LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="e55e5-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="e55e5-189">**NOT blittable:**</span><span class="sxs-lookup"><span data-stu-id="e55e5-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="e55e5-190">**BAZEN blittable:**</span><span class="sxs-lookup"><span data-stu-id="e55e5-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="e55e5-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="e55e5-191">`char`, `string`</span></span>

<span data-ttu-id="e55e5-192">Blittable türleri başvuru ile geçirildiğinde, bir ara arabelleğe kopyalanmak yerine yalnızca marshaller tarafından sabitlenirler.</span><span class="sxs-lookup"><span data-stu-id="e55e5-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="e55e5-193">(Sınıflar doğal olarak referans la geçirilir, structs `ref` ile `out`kullanıldığında referans tarafından geçirilir veya .)</span><span class="sxs-lookup"><span data-stu-id="e55e5-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="e55e5-194">`char`tek boyutlu bir **dizide** veya açıkça 'ile `[StructLayout]` `CharSet = CharSet.Unicode`işaretlenmiş içeren bir türün parçası ise blittable.</span><span class="sxs-lookup"><span data-stu-id="e55e5-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="e55e5-195">`string`başka bir türde içermiyorsa ve işaretli `[MarshalAs(UnmanagedType.LPWStr)]` veya `[DllImport]` ayarlanmış `CharSet = CharSet.Unicode` bir bağımsız değişken olarak geçiriliyorsa blittable olur.</span><span class="sxs-lookup"><span data-stu-id="e55e5-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="e55e5-196">Sabitlenmiş `GCHandle`bir tür oluşturmaya çalışarak bir türün blittable olup olmadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="e55e5-197">Tür bir dize değilse veya blittable `GCHandle.Alloc` olarak `ArgumentException`kabul edilirse, bir .</span><span class="sxs-lookup"><span data-stu-id="e55e5-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="e55e5-198">✔️ yapılarınızı mümkün olduğunda blittable olun.</span><span class="sxs-lookup"><span data-stu-id="e55e5-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="e55e5-199">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-199">For more information, see:</span></span>

- [<span data-ttu-id="e55e5-200">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="e55e5-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="e55e5-201">Tip Mareşallik</span><span class="sxs-lookup"><span data-stu-id="e55e5-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="e55e5-202">Yönetilen nesneleri canlı tutma</span><span class="sxs-lookup"><span data-stu-id="e55e5-202">Keeping managed objects alive</span></span>

<span data-ttu-id="e55e5-203">`GC.KeepAlive()`KeepAlive yöntemi vuruluna kadar bir nesnenin kapsamda kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e55e5-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="e55e5-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)marshaller'ın bir nesneyi P/Invoke süresince canlı tutmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e55e5-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="e55e5-205">Yöntem imzaları yerine `IntPtr` kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="e55e5-206">`SafeHandle`bu sınıfın yerini alır ve bunun yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="e55e5-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)yönetilen bir nesneyi sabitlemeye ve yerel işaretçinin ona yerlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="e55e5-208">Temel desen:</span><span class="sxs-lookup"><span data-stu-id="e55e5-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="e55e5-209">Sabitleme için varsayılan `GCHandle`değildir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="e55e5-210">Diğer önemli desen, yönetilen bir nesneye yerel kod üzerinden başvuru aktarmak ve genellikle geri arama ile yönetilen koda geri dönmek içindir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="e55e5-211">İşte desen:</span><span class="sxs-lookup"><span data-stu-id="e55e5-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="e55e5-212">Bellek sızıntılarını `GCHandle` önlemek için açıkça serbest bırakılmaları gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="e55e5-213">Ortak Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="e55e5-213">Common Windows data types</span></span>

<span data-ttu-id="e55e5-214">Windows API'larında yaygın olarak kullanılan ve Windows koduna ararken hangi C# türlerinin kullanılacağı veri türlerinin bir listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="e55e5-215">Aşağıdaki türler, adlarına rağmen 32 bit ve 64 bit Windows'da aynı boyuttadır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="e55e5-216">Genişlik</span><span class="sxs-lookup"><span data-stu-id="e55e5-216">Width</span></span> | <span data-ttu-id="e55e5-217">Windows</span><span class="sxs-lookup"><span data-stu-id="e55e5-217">Windows</span></span>          | <span data-ttu-id="e55e5-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="e55e5-218">C (Windows)</span></span>          | <span data-ttu-id="e55e5-219">C#</span><span class="sxs-lookup"><span data-stu-id="e55e5-219">C#</span></span>       | <span data-ttu-id="e55e5-220">Alternatif</span><span class="sxs-lookup"><span data-stu-id="e55e5-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="e55e5-221">32</span><span class="sxs-lookup"><span data-stu-id="e55e5-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="e55e5-222">8</span><span class="sxs-lookup"><span data-stu-id="e55e5-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="e55e5-223">8</span><span class="sxs-lookup"><span data-stu-id="e55e5-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="e55e5-224">8</span><span class="sxs-lookup"><span data-stu-id="e55e5-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="e55e5-225">8</span><span class="sxs-lookup"><span data-stu-id="e55e5-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="e55e5-226">16</span><span class="sxs-lookup"><span data-stu-id="e55e5-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="e55e5-227">16</span><span class="sxs-lookup"><span data-stu-id="e55e5-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="e55e5-228">16</span><span class="sxs-lookup"><span data-stu-id="e55e5-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="e55e5-229">16</span><span class="sxs-lookup"><span data-stu-id="e55e5-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="e55e5-230">16</span><span class="sxs-lookup"><span data-stu-id="e55e5-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="e55e5-231">32</span><span class="sxs-lookup"><span data-stu-id="e55e5-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="e55e5-232">32</span><span class="sxs-lookup"><span data-stu-id="e55e5-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="e55e5-233">32</span><span class="sxs-lookup"><span data-stu-id="e55e5-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="e55e5-234">32</span><span class="sxs-lookup"><span data-stu-id="e55e5-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="e55e5-235">64</span><span class="sxs-lookup"><span data-stu-id="e55e5-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="e55e5-236">64</span><span class="sxs-lookup"><span data-stu-id="e55e5-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="e55e5-237">64</span><span class="sxs-lookup"><span data-stu-id="e55e5-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="e55e5-238">64</span><span class="sxs-lookup"><span data-stu-id="e55e5-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="e55e5-239">64</span><span class="sxs-lookup"><span data-stu-id="e55e5-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="e55e5-240">32</span><span class="sxs-lookup"><span data-stu-id="e55e5-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="e55e5-241">32</span><span class="sxs-lookup"><span data-stu-id="e55e5-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="e55e5-242">İşaretçiler olmak üzere aşağıdaki türler platformun genişliğini izler.</span><span class="sxs-lookup"><span data-stu-id="e55e5-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="e55e5-243">Bunları `IntPtr` / `UIntPtr` kullan.</span><span class="sxs-lookup"><span data-stu-id="e55e5-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="e55e5-244">İmzalı İşaretçi `IntPtr`Türleri (kullanım)</span><span class="sxs-lookup"><span data-stu-id="e55e5-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="e55e5-245">İmzasız İşaretçi `UIntPtr`Türleri (kullanım)</span><span class="sxs-lookup"><span data-stu-id="e55e5-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="e55e5-246">`PVOID` C `void*` olan bir Windows ya da `IntPtr` `UIntPtr`, ancak `void*` mümkün olduğunca tercih olarak marshaled olabilir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="e55e5-247">Windows Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="e55e5-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="e55e5-248">Veri Türü Aralıkları</span><span class="sxs-lookup"><span data-stu-id="e55e5-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="e55e5-249">Yapılar</span><span class="sxs-lookup"><span data-stu-id="e55e5-249">Structs</span></span>

<span data-ttu-id="e55e5-250">Yönetilen structs yığın üzerinde oluşturulur ve yöntem döndürür kadar kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="e55e5-251">Tanım olarak o zaman, onlar "sabitlenmiş" (GC tarafından taşınmış almazsınız).</span><span class="sxs-lookup"><span data-stu-id="e55e5-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="e55e5-252">Yerel kod işaretçiyi geçerli yöntemin sonundan sonra kullanmıyorsa, adresi güvenli olmayan kod bloklarında da alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="e55e5-253">Blittable structs sadece doğrudan mareşal tabaka tarafından kullanılabilir gibi çok daha performant vardır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="e55e5-254">Structs blittable yapmaya çalışın (örneğin, kaçının). `bool`</span><span class="sxs-lookup"><span data-stu-id="e55e5-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="e55e5-255">Daha fazla bilgi için [Blittable Türleri](#blittable-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="e55e5-256">*If* Yapı blittable ise, daha `sizeof()` iyi `Marshal.SizeOf<MyStruct>()` performans yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="e55e5-257">Yukarıda belirtildiği gibi, sabitlenmiş `GCHandle`bir oluşturmak için deneyerek türünün blittable olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="e55e5-258">Tür bir dize değilse veya blittable olarak kabul edilirse, `GCHandle.Alloc` bir `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="e55e5-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="e55e5-259">Tanımlardaki yapı işaretçileri ya geçilmeli `ref` ya da `unsafe` `*`kullanılmalıdır ve .</span><span class="sxs-lookup"><span data-stu-id="e55e5-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="e55e5-260">✔️ DO, yönetilen yapıyla resmi platform belgelerinde veya üstbilgide kullanılan şekil ve adlarla mümkün olduğunca yakından eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="e55e5-261">✔️ DO, performansı `sizeof()` artırmak `Marshal.SizeOf<MyStruct>()` için blittable yapılar yerine C# kullanın.</span><span class="sxs-lookup"><span data-stu-id="e55e5-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="e55e5-262">❌Yapılardaki `System.Delegate` `System.MulticastDelegate` işlev işaretçisi alanlarını temsil etmek için kullanmaktan veya alanlardan kaçının.</span><span class="sxs-lookup"><span data-stu-id="e55e5-262">❌ AVOID using `System.Delegate` or `System.MulticastDelegate` fields to represent function pointer fields in structures.</span></span>

<span data-ttu-id="e55e5-263">Gerekli <xref:System.Delegate?displayProperty=fullName> <xref:System.MulticastDelegate?displayProperty=fullName> bir imzaya sahip olmadıklarından ve gerekli imzaya sahip olmadıklarından, geçen temsilcinin yerel kodun beklediği imzayla eşleşeceğini garanti etmezler.</span><span class="sxs-lookup"><span data-stu-id="e55e5-263">Since <xref:System.Delegate?displayProperty=fullName> and <xref:System.MulticastDelegate?displayProperty=fullName> don't have a required signature, they don't guarantee that the delegate passed in will match the signature the native code expects.</span></span> <span data-ttu-id="e55e5-264">Ayrıca, .NET Framework ve .NET Core'da, yerel `System.Delegate` gösterimini içeren bir yapıyı veya `System.MulticastDelegate` yerel temsilini içeren bir yapıyı yönetilen bir nesneye iliştirmek, yerel gösterimdeki alanın değeri yönetilen bir temsilciyi saran bir işlev işaretçisi değilse çalışma süresini bozabilir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-264">Additionally, in .NET Framework and .NET Core, marshaling a struct containing a `System.Delegate` or `System.MulticastDelegate` from its native representation to a managed object can destabilize the runtime if the value of the field in the native representation isn't a function pointer that wraps a managed delegate.</span></span> <span data-ttu-id="e55e5-265">.NET 5 ve sonraki sürümlerde, bir `System.Delegate` veya `System.MulticastDelegate` alan yerel gösterimden yönetilen bir nesneye marshaling desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e55e5-265">In .NET 5 and later versions, marshaling a `System.Delegate` or `System.MulticastDelegate` field from a native representation to a managed object is not supported.</span></span> <span data-ttu-id="e55e5-266">Veya `System.Delegate` `System.MulticastDelegate`' yerine belirli bir temsilci türü kullanın</span><span class="sxs-lookup"><span data-stu-id="e55e5-266">Use a specific delegate type instead of `System.Delegate` or `System.MulticastDelegate`.</span></span>

### <a name="fixed-buffers"></a><span data-ttu-id="e55e5-267">Sabit Arabellekler</span><span class="sxs-lookup"><span data-stu-id="e55e5-267">Fixed Buffers</span></span>

<span data-ttu-id="e55e5-268">Bunun gibi `INT_PTR Reserved1[2]` bir dizi iki `IntPtr` alana `Reserved1a` marshaled gerekir ve `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="e55e5-268">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="e55e5-269">Yerel dizi ilkel bir tür olduğunda, `fixed` anahtar kelimeyi biraz daha temiz yazmak için kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-269">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="e55e5-270">Örneğin, `SYSTEM_PROCESS_INFORMATION` yerel üstbilgide şu na benzer:</span><span class="sxs-lookup"><span data-stu-id="e55e5-270">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="e55e5-271">C#'da şöyle yazabiliriz:</span><span class="sxs-lookup"><span data-stu-id="e55e5-271">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="e55e5-272">Ancak, sabit arabellekleri ile bazı gotchas vardır.</span><span class="sxs-lookup"><span data-stu-id="e55e5-272">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="e55e5-273">Blittable olmayan türlerin sabit arabellekleri doğru şekilde marshaled olmaz, bu nedenle yerinde dizi birden çok ayrı alanlara genişletilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e55e5-273">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="e55e5-274">Ayrıca, .NET Framework ve .NET Core'da 3.0'dan önce, sabit arabellek alanı içeren bir yapı, blittable olmayan bir yapıiçinde iç içe geçikarsa, sabit arabellek alanı yerel koda doğru şekilde marshaled olmaz.</span><span class="sxs-lookup"><span data-stu-id="e55e5-274">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
