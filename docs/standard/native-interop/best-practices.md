---
title: Yerel birlikte çalışabilirlik en iyi uygulamaları-.NET
description: .NET 'teki yerel bileşenlerle arabirimlendirme için en iyi uygulamaları öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 7730241ba834d9fcafaaf13055da1a03d359aa1b
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479590"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="f0d0e-103">Yerel birlikte çalışabilirlik en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="f0d0e-103">Native interoperability best practices</span></span>

<span data-ttu-id="f0d0e-104">.NET, yerel birlikte çalışabilirlik kodunuzu özelleştirmek için kullanabileceğiniz çeşitli yollar sunar.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="f0d0e-105">Bu makale, Microsoft 'un .NET ekiplerinin yerel birlikte çalışabilirlik için izlediği yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="f0d0e-106">Genel kılavuz</span><span class="sxs-lookup"><span data-stu-id="f0d0e-106">General guidance</span></span>

<span data-ttu-id="f0d0e-107">Bu bölümdeki kılavuz tüm birlikte çalışma senaryoları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="f0d0e-108">✔️, yöntemlerinizi ve parametreleriniz için, çağırmak istediğiniz yerel yöntem olarak aynı adlandırma ve büyük harfleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="f0d0e-109">✔️ sabit değerler için aynı adlandırma ve büyük harfleri kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="f0d0e-110">✔️, yerel türe en yakın eşleme olan .NET türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="f0d0e-111">Örneğin, C# ' de, `uint` Yerel tür olduğunda kullanın `unsigned int` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="f0d0e-112">✔️ yalnızca, `[In]` `[Out]` istediğiniz davranış varsayılan davranıştan farklı olduğunda ve özniteliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="f0d0e-113">✔️, <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> yerel dizi arabelleklerinizi havuza almak için KULLANMAYı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="f0d0e-114">✔️, P/Invoke bildirimlerinizi yerel kitaplığınız ile aynı ada ve büyük harfe sahip bir sınıfta sarmalamanızı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="f0d0e-115">Bu, `[DllImport]` özniteliklerinizin `nameof` Yerel kitaplığın adını geçirmek için C# dil özelliğini kullanmasını sağlar ve yerel kitaplığın adını yanlış yazmadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="f0d0e-116">DllImport öznitelik ayarları</span><span class="sxs-lookup"><span data-stu-id="f0d0e-116">DllImport attribute settings</span></span>

| <span data-ttu-id="f0d0e-117">Ayar</span><span class="sxs-lookup"><span data-stu-id="f0d0e-117">Setting</span></span> | <span data-ttu-id="f0d0e-118">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="f0d0e-118">Default</span></span> | <span data-ttu-id="f0d0e-119">Öneri</span><span class="sxs-lookup"><span data-stu-id="f0d0e-119">Recommendation</span></span> | <span data-ttu-id="f0d0e-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f0d0e-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="f0d0e-121">Varsayılanı tut</span><span class="sxs-lookup"><span data-stu-id="f0d0e-121">keep default</span></span>  | <span data-ttu-id="f0d0e-122">Bu açık olarak yanlış olarak ayarlandığında, başarısız HRESULT dönüş değerleri özel durumlara açılır (ve tanımdaki dönüş değeri sonuç olarak null olur).</span><span class="sxs-lookup"><span data-stu-id="f0d0e-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="f0d0e-123">API 'ye bağlıdır</span><span class="sxs-lookup"><span data-stu-id="f0d0e-123">depends on the API</span></span>  | <span data-ttu-id="f0d0e-124">API GetLastError kullanıyorsa bunu true olarak ayarlayın ve değeri almak için Marshal. GetLastWin32Error kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="f0d0e-125">API bir hata olduğunu bildiren bir koşul ayarlarsa, yanlışlıkla üzerine yazılmasını önlemek için başka çağrılar yapmadan önce hatayı alın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="f0d0e-126">`CharSet.None`, davranışa geri döner `CharSet.Ansi`</span><span class="sxs-lookup"><span data-stu-id="f0d0e-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="f0d0e-127">`CharSet.Unicode` `CharSet.Ansi` Tanımda dizeler veya karakterler varsa, açıkça kullanın</span><span class="sxs-lookup"><span data-stu-id="f0d0e-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="f0d0e-128">Bu, dizelerin sıralama davranışını ve ne `ExactSpelling` zaman yapılacağını belirtir `false` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="f0d0e-129">Bunun `CharSet.Ansi` aslında UNIX ÜZERINDE UTF8 olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="f0d0e-130">_Çoğu_ zaman Windows Unicode kullanır, ancak UNIX UTF8 kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="f0d0e-131">[Değiştirmeye belgeleri](./charset.md)hakkında daha fazla bilgi için bkz..</span><span class="sxs-lookup"><span data-stu-id="f0d0e-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="f0d0e-132">Bunu true olarak ayarlayın ve çalışma zamanı, ayarın değerine bağlı olarak bir "A" veya "W" sonekiyle `CharSet` (için "a" `CharSet.Ansi` ve "w") farklı işlev adlarını araymaz `CharSet.Unicode` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="f0d0e-133">Dize parametreleri</span><span class="sxs-lookup"><span data-stu-id="f0d0e-133">String parameters</span></span>

<span data-ttu-id="f0d0e-134">Karakter kümesi Unicode olduğunda veya bağımsız değişken açıkça olarak işaretlenmişse `[MarshalAs(UnmanagedType.LPWSTR)]` _ve_ dize değer ile geçirildiğinde (değil `ref` `out` ), dize sabitlenir ve doğrudan yerel kod tarafından kullanılır (kopyalanmaktansa).</span><span class="sxs-lookup"><span data-stu-id="f0d0e-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="f0d0e-135">`[DllImport]` `Charset.Unicode` DIZELERINIZIN ANSI düzeltmesini açıkça istemediğiniz sürece, işaretini işaretlemeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="f0d0e-136">❌`[Out] string`Parametreleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="f0d0e-137">Değer tarafından özniteliği ile geçirilen dize parametreleri, `[Out]` dize bir dizilmiş dize ise çalışma zamanının kararlılığını bozabilir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="f0d0e-138">İçin belgelerde dize oluşturma hakkında daha fazla bilgi görüntüleyin <xref:System.String.Intern%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f0d0e-139">❌`StringBuilder`PARAMETRELERDEN kaçının.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="f0d0e-140">`StringBuilder` hazırlama *her zaman* yerel bir arabellek kopyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="f0d0e-141">Bu nedenle, son derece verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="f0d0e-142">Bir dize alan bir Windows API 'SI çağırmanın tipik senaryosunu gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="f0d0e-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="f0d0e-143">İstenen kapasiteyi (yönetilen kapasiteyi ayırır) bir SB oluşturun **{1}**</span><span class="sxs-lookup"><span data-stu-id="f0d0e-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="f0d0e-144">Çağır</span><span class="sxs-lookup"><span data-stu-id="f0d0e-144">Invoke</span></span>
   1. <span data-ttu-id="f0d0e-145">Yerel bir arabellek ayırır **{2}**</span><span class="sxs-lookup"><span data-stu-id="f0d0e-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="f0d0e-146">`[In]` _(Bir `StringBuilder` parametre için varsayılan)_ içeriğini kopyalar</span><span class="sxs-lookup"><span data-stu-id="f0d0e-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="f0d0e-147">Yerel arabelleği yeni ayrılmış bir yönetilen diziye `[Out]` **{3}** _(Ayrıca için varsayılan `StringBuilder` )_ kopyalar</span><span class="sxs-lookup"><span data-stu-id="f0d0e-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="f0d0e-148">`ToString()` henüz başka bir yönetilen diziyi ayırır **{4}**</span><span class="sxs-lookup"><span data-stu-id="f0d0e-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="f0d0e-149">Bu, *{4}* yerel koddan bir dizeyi almak için ayırmaların bir dizesidir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="f0d0e-150">Bunu sınırlamak için en iyi yöntem, başka bir çağrıda öğesini yeniden kullanmak olacaktır `StringBuilder` ancak yalnızca *1* ayırmayı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="f0d0e-151">' Den bir karakter arabelleğini kullanmak ve önbelleğe almak çok daha iyidir `ArrayPool` . daha sonra, sonraki çağrılar için yalnızca ayırmaya erişebilirsiniz `ToString()` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="f0d0e-152">İle ilgili diğer sorun, `StringBuilder` geri dönüş arabelleğini her zaman ilk null değere kopyasın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="f0d0e-153">Geçilen geri dize sonlandırılmazsa veya çift null ile sonlandırılmış bir dize ise, P/Invoke uygulamanız en iyi şekilde yanlış olur.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="f0d0e-154">*Kullanıyorsanız* `StringBuilder` , bir adet son Gotcha, kapasitenin birlikte çalışma içinde her zaman hesaba katılmış bir gizli null değer **içermemelidir** .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="f0d0e-155">Çoğu API 'nin, null değeri *de dahil olmak üzere* arabellek boyutunu istediği için bu, insanların bu yanlış alması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="f0d0e-156">Bu, harcanan/gereksiz ayırmalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="f0d0e-157">Ayrıca, bu Gotcha, çalışma zamanının `StringBuilder` kopyaları en aza indirmek için sıralama iyileştirmesine engel olur.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="f0d0e-158">✔️ içinden ' i kullanmayı düşünün `char[]` `ArrayPool` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="f0d0e-159">Dize sıralaması hakkında daha fazla bilgi için bkz. [dizeler Için varsayılan sıralama](../../framework/interop/default-marshaling-for-strings.md) ve [dize sıralamasını özelleştirme](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="f0d0e-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="f0d0e-160">__Windows 'A özgü__ `[Out]` Clr 'nin `CoTaskMemFree` Varsayılan olarak boş dizeler veya `SysStringFree` olarak işaretlenen dizeler için kullanacağı dizeler `UnmanagedType.BSTR` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="f0d0e-161">**Çıkış dizesi arabelleğine sahip çoğu API için:** Geçirilen karakter sayısı null içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="f0d0e-162">Döndürülen değer geçilen karakter sayısından küçükse, çağrı başarılı olur ve değer sondaki null *olmayan* karakter sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="f0d0e-163">Aksi takdirde, sayı null karakter *dahil olmak üzere* arabelleğin gerekli boyutudur.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="f0d0e-164">5 ' te geçiş yapın, 4 ' ü alın: dize sonunda null olan 4 karakter uzunluğundadır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="f0d0e-165">5 ' te geçiş yapın, 6: dize 5 karakter uzunluğundadır, null tutmak için 6 karakterlik bir arabellek gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="f0d0e-166">Dizeler için Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="f0d0e-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="f0d0e-167">Boole parametreleri ve alanları</span><span class="sxs-lookup"><span data-stu-id="f0d0e-167">Boolean parameters and fields</span></span>

<span data-ttu-id="f0d0e-168">Boole değerleri daha kolay.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="f0d0e-169">Varsayılan olarak, .NET, `bool` `BOOL` 4 baytlık bir değer olan bir Windows için sıralanır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="f0d0e-170">Ancak, `_Bool` ve `bool` C ve C++ içindeki türler *tek* bir bayttır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="f0d0e-171">Bu, dönüş değerinin atıldığı ve yalnızca *büyük olasılıkla* sonucu değiştirecek olan hataları takip etmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="f0d0e-172">.NET `bool` değerlerini C veya C++ türlerine hazırlama hakkında daha fazla bilgi için `bool` , [Boole alanı sıralamasını özelleştirme](customize-struct-marshaling.md#customizing-boolean-field-marshaling)hakkındaki belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="f0d0e-173">Yapılamıyor</span><span class="sxs-lookup"><span data-stu-id="f0d0e-173">GUIDs</span></span>

<span data-ttu-id="f0d0e-174">GUID 'Ler doğrudan imzalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="f0d0e-175">Birçok Windows API 'si, `GUID&` gibi tür diğer adlarını alır `REFIID` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="f0d0e-176">Ref tarafından geçirildiğinde, `ref` ya da `[MarshalAs(UnmanagedType.LPStruct)]` özniteliğiyle geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="f0d0e-177">GUID</span><span class="sxs-lookup"><span data-stu-id="f0d0e-177">GUID</span></span> | <span data-ttu-id="f0d0e-178">-Başvuru GUID 'SI</span><span class="sxs-lookup"><span data-stu-id="f0d0e-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="f0d0e-179">❌`[MarshalAs(UnmanagedType.LPStruct)]`GUID parametrelerinden başka bir şey Için kullanmayın `ref` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="f0d0e-180">Blittable türleri</span><span class="sxs-lookup"><span data-stu-id="f0d0e-180">Blittable types</span></span>

<span data-ttu-id="f0d0e-181">Blittable türleri, yönetilen ve yerel kodda aynı bit düzeyi gösterimine sahip olan türlerdir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="f0d0e-182">Bu şekilde, yerel koda ve yerel koddan sıralanmaları için başka bir biçime dönüştürülmesi gerekmez ve bu da performansı artırdığı için tercih edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span> <span data-ttu-id="f0d0e-183">Bazı türler blittable değildir ancak blittable içeriğini içerecek şekilde bilinir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-183">Some types are not blittable but are known to contain blittable contents.</span></span> <span data-ttu-id="f0d0e-184">Bu türler, blittable türleri gibi benzer iyileştirmelere sahiptir, ancak yapı alanları veya amaçları için blittable olarak değerlendirilmez [`UnmanagedCallersOnlyAttribute`](xref:System.Runtime.InteropServices.UnmanagedCallersOnlyAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-184">These types have similar optimizations as blittable types when they are not contained in another type, but are not considered blittable when in fields of structs or for the purposes of [`UnmanagedCallersOnlyAttribute`](xref:System.Runtime.InteropServices.UnmanagedCallersOnlyAttribute).</span></span>

<span data-ttu-id="f0d0e-185">**Blittable türleri:**</span><span class="sxs-lookup"><span data-stu-id="f0d0e-185">**Blittable types:**</span></span>

- <span data-ttu-id="f0d0e-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="f0d0e-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="f0d0e-187">örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzene sahip yapılar</span><span class="sxs-lookup"><span data-stu-id="f0d0e-187">structs with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="f0d0e-188">Sabit düzen için `[StructLayout(LayoutKind.Sequential)]` veya `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="f0d0e-188">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="f0d0e-189">yapılar `LayoutKind.Sequential` Varsayılan olarak</span><span class="sxs-lookup"><span data-stu-id="f0d0e-189">structs are `LayoutKind.Sequential` by default</span></span>

<span data-ttu-id="f0d0e-190">**Blittable içeriği olan türler:**</span><span class="sxs-lookup"><span data-stu-id="f0d0e-190">**Types with blittable contents:**</span></span>

- <span data-ttu-id="f0d0e-191">blittable ilkel türlerin iç içe olmayan, tek boyutlu dizileri (örneğin, `int[]` )</span><span class="sxs-lookup"><span data-stu-id="f0d0e-191">non-nested, one-dimensional arrays of blittable primitive types (for example, `int[]`)</span></span>
- <span data-ttu-id="f0d0e-192">örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzene sahip sınıflar</span><span class="sxs-lookup"><span data-stu-id="f0d0e-192">classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="f0d0e-193">Sabit düzen için `[StructLayout(LayoutKind.Sequential)]` veya `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="f0d0e-193">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="f0d0e-194">sınıflar `LayoutKind.Auto` Varsayılan olarak</span><span class="sxs-lookup"><span data-stu-id="f0d0e-194">classes are `LayoutKind.Auto` by default</span></span>

<span data-ttu-id="f0d0e-195">**Blittable DEĞIL:**</span><span class="sxs-lookup"><span data-stu-id="f0d0e-195">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="f0d0e-196">**Bazen blittable:**</span><span class="sxs-lookup"><span data-stu-id="f0d0e-196">**SOMETIMES blittable:**</span></span>

- `char`

<span data-ttu-id="f0d0e-197">**Bazen blittable içeriğe sahip türler:**</span><span class="sxs-lookup"><span data-stu-id="f0d0e-197">**Types with SOMETIMES blittable contents:**</span></span>

- `string`

<span data-ttu-id="f0d0e-198">Blittable türler,, veya ile başvuru ile `in` geçirildiğinde `ref` `out` veya blittable içeriði olan türler değere göre geçirildiğinde, bir ara belleğe kopyalamak yerine yalnızca hazırlayıcısı tarafından sabitlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-198">When blittable types are passed by reference with `in`, `ref`, or `out`, or when types with blittable contents are passed by value, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span>

<span data-ttu-id="f0d0e-199">`char` tek boyutlu bir dizide **veya** ile birlikte açık olarak işaretlenen bir türün parçasıysa blittable `[StructLayout]` `CharSet = CharSet.Unicode` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-199">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="f0d0e-200">`string` , başka bir türde yoksa ve ile işaretlenmiş bir bağımsız değişken olarak geçiriliyorsa, blittable içeriğini içerir `[MarshalAs(UnmanagedType.LPWStr)]` `[DllImport]` `CharSet = CharSet.Unicode` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-200">`string` contains blittable contents if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="f0d0e-201">Bir türün blittable olup olmadığını veya bir sabitlenmiş bir oluşturma girişiminde blittable içeriği içerip içerdiğini görebilirsiniz `GCHandle` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-201">You can see if a type is blittable or contains blittable contents by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="f0d0e-202">Tür bir dize değilse veya blittable olarak kabul edilir `GCHandle.Alloc` `ArgumentException` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-202">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="f0d0e-203">✔️ yapılarınızı mümkün olduğunca blittable yapın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-203">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="f0d0e-204">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-204">For more information, see:</span></span>

- [<span data-ttu-id="f0d0e-205">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="f0d0e-205">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="f0d0e-206">Tür sıralaması</span><span class="sxs-lookup"><span data-stu-id="f0d0e-206">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="f0d0e-207">Yönetilen nesneleri canlı tutma</span><span class="sxs-lookup"><span data-stu-id="f0d0e-207">Keeping managed objects alive</span></span>

<span data-ttu-id="f0d0e-208">`GC.KeepAlive()` bir nesnenin, KeepAlive yöntemi vurana kadar kapsamda kalmasını güvence altına alınır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-208">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="f0d0e-209">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) hazırlayıcısı 'in bir P/Invoke süresince bir nesneyi canlı tutmaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-209">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="f0d0e-210">Yöntemi, yöntem imzaları yerine kullanılabilir `IntPtr` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-210">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="f0d0e-211">`SafeHandle` Bu sınıfın yerini etkin bir şekilde değiştirir ve bunun yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-211">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="f0d0e-212">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) yönetilen bir nesnenin sabitlenmesini ve yerel işaretçisine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-212">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="f0d0e-213">Temel model:</span><span class="sxs-lookup"><span data-stu-id="f0d0e-213">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="f0d0e-214">Sabitleme için varsayılan değer değildir `GCHandle` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-214">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="f0d0e-215">Diğer büyük model, yerel kod aracılığıyla yönetilen bir nesneye başvuru geçirmek ve genellikle bir geri çağırma ile yönetilen koda geri dönmek içindir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-215">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="f0d0e-216">Bu, şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f0d0e-216">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="f0d0e-217">`GCHandle`Bellek sızıntılarını önlemek için açıkça serbest bırakılmış olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-217">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="f0d0e-218">Ortak Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="f0d0e-218">Common Windows data types</span></span>

<span data-ttu-id="f0d0e-219">Aşağıda, Windows API 'Lerinde yaygın olarak kullanılan ve Windows koduna çağrılırken hangi C# türlerinin kullanılacağı veri türlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-219">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="f0d0e-220">Aşağıdaki türler, adlarına rağmen 32-bit ve 64-bit Windows üzerinde aynı boyutlardır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-220">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="f0d0e-221">Width</span><span class="sxs-lookup"><span data-stu-id="f0d0e-221">Width</span></span> | <span data-ttu-id="f0d0e-222">Windows</span><span class="sxs-lookup"><span data-stu-id="f0d0e-222">Windows</span></span>          | <span data-ttu-id="f0d0e-223">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="f0d0e-223">C (Windows)</span></span>          | <span data-ttu-id="f0d0e-224">C#</span><span class="sxs-lookup"><span data-stu-id="f0d0e-224">C#</span></span>       | <span data-ttu-id="f0d0e-225">Yapıyı</span><span class="sxs-lookup"><span data-stu-id="f0d0e-225">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="f0d0e-226">32</span><span class="sxs-lookup"><span data-stu-id="f0d0e-226">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="f0d0e-227">8</span><span class="sxs-lookup"><span data-stu-id="f0d0e-227">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="f0d0e-228">8</span><span class="sxs-lookup"><span data-stu-id="f0d0e-228">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="f0d0e-229">8</span><span class="sxs-lookup"><span data-stu-id="f0d0e-229">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="f0d0e-230">8</span><span class="sxs-lookup"><span data-stu-id="f0d0e-230">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="f0d0e-231">16</span><span class="sxs-lookup"><span data-stu-id="f0d0e-231">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="f0d0e-232">16</span><span class="sxs-lookup"><span data-stu-id="f0d0e-232">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="f0d0e-233">16</span><span class="sxs-lookup"><span data-stu-id="f0d0e-233">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="f0d0e-234">16</span><span class="sxs-lookup"><span data-stu-id="f0d0e-234">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="f0d0e-235">16</span><span class="sxs-lookup"><span data-stu-id="f0d0e-235">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="f0d0e-236">32</span><span class="sxs-lookup"><span data-stu-id="f0d0e-236">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="f0d0e-237">32</span><span class="sxs-lookup"><span data-stu-id="f0d0e-237">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="f0d0e-238">32</span><span class="sxs-lookup"><span data-stu-id="f0d0e-238">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="f0d0e-239">32</span><span class="sxs-lookup"><span data-stu-id="f0d0e-239">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="f0d0e-240">64</span><span class="sxs-lookup"><span data-stu-id="f0d0e-240">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="f0d0e-241">64</span><span class="sxs-lookup"><span data-stu-id="f0d0e-241">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="f0d0e-242">64</span><span class="sxs-lookup"><span data-stu-id="f0d0e-242">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="f0d0e-243">64</span><span class="sxs-lookup"><span data-stu-id="f0d0e-243">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="f0d0e-244">64</span><span class="sxs-lookup"><span data-stu-id="f0d0e-244">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="f0d0e-245">32</span><span class="sxs-lookup"><span data-stu-id="f0d0e-245">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="f0d0e-246">32</span><span class="sxs-lookup"><span data-stu-id="f0d0e-246">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="f0d0e-247">Aşağıdaki türler, işaretçiler olması, platformun genişliğini izler.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-247">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="f0d0e-248">`IntPtr` / `UIntPtr` Bunlar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-248">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="f0d0e-249">İmzalı Işaretçi türleri (kullanım `IntPtr` )</span><span class="sxs-lookup"><span data-stu-id="f0d0e-249">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="f0d0e-250">İşaretsiz Işaretçi türleri (kullanım `UIntPtr` )</span><span class="sxs-lookup"><span data-stu-id="f0d0e-250">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="f0d0e-251">`PVOID`C olan bir Windows `void*` ya da olarak sıralanabilir `IntPtr` `UIntPtr` , ancak `void*` mümkün olduğunda tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-251">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="f0d0e-252">Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="f0d0e-252">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="f0d0e-253">Veri türü aralıkları</span><span class="sxs-lookup"><span data-stu-id="f0d0e-253">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

### <a name="formerly-built-in-supported-types"></a><span data-ttu-id="f0d0e-254">Önceden oluşturulmuş desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="f0d0e-254">Formerly built-in supported types</span></span>

<span data-ttu-id="f0d0e-255">Bir tür için yerleşik desteğin kaldırıldığı nadir örnekler vardır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-255">There are rare instances when built-in support for a type is removed.</span></span>

<span data-ttu-id="f0d0e-256">[`UnmanagedType.HString`](xref:System.Runtime.InteropServices.UnmanagedType)Yerleşik sıralama desteği .NET 5 sürümünde kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-256">The [`UnmanagedType.HString`](xref:System.Runtime.InteropServices.UnmanagedType) built-in marshal support was removed in the .NET 5 release.</span></span> <span data-ttu-id="f0d0e-257">Bu sıralama türünü kullanan ve önceki bir çerçeveyi hedefleyen ikili dosyaları yeniden derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-257">You must recompile binaries that use this marshalling type and that target a previous framework.</span></span> <span data-ttu-id="f0d0e-258">Bu tür sıralaması devam edebilir, ancak aşağıdaki kod örneğinde gösterildiği gibi bunu el ile sıralamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-258">It's still possible to marshal this type, but you must marshal it manually, as the following code example shows.</span></span> <span data-ttu-id="f0d0e-259">Bu kod, ileriye dönük ve önceki çerçevelerle de uyumlu olacak şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-259">This code will work moving forward and is also compatible with previous frameworks.</span></span>

```csharp
static class HSTRING
{
    public static IntPtr FromString(string s)
    {
        Marshal.ThrowExceptionForHR(WindowsCreateString(s, s.Length, out IntPtr h));
        return h;
    }

    public static void Delete(IntPtr s)
    {
        Marshal.ThrowExceptionForHR(WindowsDeleteString(s));
    }

    [DllImport("api-ms-win-core-winrt-string-l1-1-0.dll", CallingConvention = CallingConvention.StdCall, ExactSpelling = true)]
    private static extern int WindowsCreateString(
        [MarshalAs(UnmanagedType.LPWStr)] string sourceString, int length, out IntPtr hstring);

    [DllImport("api-ms-win-core-winrt-string-l1-1-0.dll", CallingConvention = CallingConvention.StdCall, ExactSpelling = true)]
    private static extern int WindowsDeleteString(IntPtr hstring);
}

// Usage example
IntPtr hstring = HSTRING.FromString("HSTRING from .NET to WinRT API");
try
{
    // Pass hstring to WinRT or Win32 API.
}
finally
{
    HSTRING.Delete(hstring);
}
```

## <a name="structs"></a><span data-ttu-id="f0d0e-260">Yapılar</span><span class="sxs-lookup"><span data-stu-id="f0d0e-260">Structs</span></span>

<span data-ttu-id="f0d0e-261">Yönetilen yapılar yığında oluşturulur ve Yöntem dönene kadar kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-261">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="f0d0e-262">Daha sonra, tanım olarak "sabitlenmiş" olur (GC tarafından taşınmaz).</span><span class="sxs-lookup"><span data-stu-id="f0d0e-262">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="f0d0e-263">Ayrıca, yerel kod geçerli yöntemin sonundan sonra işaretçiyi kullanmayacaksa, güvenli olmayan kod bloklarıyla adresi de alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-263">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="f0d0e-264">Blittable yapılar, doğrudan hazırlama katmanı tarafından yalnızca kullanılabilecek şekilde daha fazla performanızdır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-264">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="f0d0e-265">Yapıları blittable yapmayı deneyin (örneğin, kullanmaktan kaçının `bool` ).</span><span class="sxs-lookup"><span data-stu-id="f0d0e-265">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="f0d0e-266">Daha fazla bilgi için [blittable Types](#blittable-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-266">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="f0d0e-267">Yapı *blittable ise,* `sizeof()` `Marshal.SizeOf<MyStruct>()` daha iyi performans için yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-267">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="f0d0e-268">Yukarıda da belirtildiği gibi, sabitlenmiş bir sabitlenmiş oluşturma girişiminde, türün blittable olduğunu doğrulayabilirsiniz `GCHandle` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-268">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="f0d0e-269">Tür bir dize değilse veya blittable olarak kabul edilir, `GCHandle.Alloc` bir oluşturur `ArgumentException` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-269">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="f0d0e-270">Tanımlarda yapıların işaretçilerine ya da ile geçirilmesi gerekir `ref` `unsafe` `*` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-270">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="f0d0e-271">✔️, resmi platform belgelerinde veya üstbilgisinde kullanılan şekle ve adlara göre, yönetilen yapı ile mümkün olduğunca yakından eşleşir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-271">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="f0d0e-272">✔️ `sizeof()` `Marshal.SizeOf<MyStruct>()` performansı artırmak için blittable yapıları yerine C# kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-272">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="f0d0e-273">❌`System.Delegate` `System.MulticastDelegate` Yapılardaki işlev işaretçisi alanlarını temsil etmek için veya alanlarını kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-273">❌ AVOID using `System.Delegate` or `System.MulticastDelegate` fields to represent function pointer fields in structures.</span></span>

<span data-ttu-id="f0d0e-274"><xref:System.Delegate?displayProperty=fullName> <xref:System.MulticastDelegate?displayProperty=fullName> Gerekli bir imzaya sahip olmadığından, geçirilen temsilcinin yerel kodun beklediği imzayla eşleşeceğini garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-274">Since <xref:System.Delegate?displayProperty=fullName> and <xref:System.MulticastDelegate?displayProperty=fullName> don't have a required signature, they don't guarantee that the delegate passed in will match the signature the native code expects.</span></span> <span data-ttu-id="f0d0e-275">Ayrıca, .NET Framework ve .NET Core ' da, yerel `System.Delegate` `System.MulticastDelegate` temsilindeki alanın değeri yönetilen bir temsilciyi sarmalayan bir işlev işaretçisi değilse, bir veya yerel gösteriminden yönetilen bir nesne içeren bir yapının sıralaması çalışma zamanının kararlılığını bozabilir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-275">Additionally, in .NET Framework and .NET Core, marshaling a struct containing a `System.Delegate` or `System.MulticastDelegate` from its native representation to a managed object can destabilize the runtime if the value of the field in the native representation isn't a function pointer that wraps a managed delegate.</span></span> <span data-ttu-id="f0d0e-276">.NET 5 ve sonraki sürümlerde, bir `System.Delegate` veya `System.MulticastDelegate` alanını yerel gösterimden yönetilen bir nesneye sıralama desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-276">In .NET 5 and later versions, marshaling a `System.Delegate` or `System.MulticastDelegate` field from a native representation to a managed object is not supported.</span></span> <span data-ttu-id="f0d0e-277">Veya yerine belirli bir temsilci türü kullanın `System.Delegate` `System.MulticastDelegate` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-277">Use a specific delegate type instead of `System.Delegate` or `System.MulticastDelegate`.</span></span>

### <a name="fixed-buffers"></a><span data-ttu-id="f0d0e-278">Sabit arabellekler</span><span class="sxs-lookup"><span data-stu-id="f0d0e-278">Fixed Buffers</span></span>

<span data-ttu-id="f0d0e-279">Benzer bir dizi `INT_PTR Reserved1[2]` iki alan için sıralanmalıdır `IntPtr` `Reserved1a` ve `Reserved1b` .</span><span class="sxs-lookup"><span data-stu-id="f0d0e-279">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="f0d0e-280">Yerel dizi basit bir tür olduğunda, `fixed` anahtar sözcüğünü kullanarak biraz daha düzgün bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-280">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="f0d0e-281">Örneğin, `SYSTEM_PROCESS_INFORMATION` Yerel üst bilgisinde şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="f0d0e-281">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="f0d0e-282">C# ' de, bunu şöyle yazalım:</span><span class="sxs-lookup"><span data-stu-id="f0d0e-282">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="f0d0e-283">Ancak, sabit arabelleklerle bazı tuzakları vardır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-283">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="f0d0e-284">Blittable olmayan türlerin sabit arabellekleri doğru sıralanmayacak, bu nedenle yerinde dizinin birden çok ayrı alana genişletilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-284">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="f0d0e-285">Ayrıca, .NET Framework ve .NET Core 'da 3,0 öncesinde, sabit bir arabellek alanı içeren bir struct, blittable olmayan bir yapı içinde iç içe geçmişse, sabit arabellek alanı yerel koda doğru şekilde sıralanmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f0d0e-285">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
