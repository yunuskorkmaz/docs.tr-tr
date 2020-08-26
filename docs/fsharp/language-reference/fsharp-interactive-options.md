---
title: Etkileşimli Seçenekler
description: F# Etkileşimli, fsi.exe tarafından desteklenen komut satırı seçenekleri hakkında bilgi edinin.
ms.date: 08/15/2020
ms.openlocfilehash: adc8dc86f14366720e1acbf35115d4e318a76aef
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810539"
---
# <a name="f-interactive-options"></a><span data-ttu-id="76806-103">F# Etkileşimli seçenekleri</span><span class="sxs-lookup"><span data-stu-id="76806-103">F# Interactive options</span></span>

<span data-ttu-id="76806-104">Bu makalede, F# Etkileşimli tarafından desteklenen komut satırı seçenekleri açıklanmaktadır `fsi.exe` .</span><span class="sxs-lookup"><span data-stu-id="76806-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="76806-105">F# Etkileşimli, F # derleyicisi ile aynı komut satırı seçeneklerinin birçoğunu kabul eder, ancak aynı zamanda bazı ek seçenekleri de kabul eder.</span><span class="sxs-lookup"><span data-stu-id="76806-105">F# Interactive accepts many of the same command-line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="76806-106">Betik için F# Etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="76806-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="76806-107">F# Etkileşimli, `dotnet fsi` etkileşimli olarak başlatılabilir veya bir betiği çalıştırmak için komut satırından başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="76806-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="76806-108">Komut satırı söz dizimi</span><span class="sxs-lookup"><span data-stu-id="76806-108">The command-line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="76806-109">F # betik dosyaları için dosya uzantısı `.fsx` .</span><span class="sxs-lookup"><span data-stu-id="76806-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="76806-110">F# Etkileşimli seçenekleri tablosu</span><span class="sxs-lookup"><span data-stu-id="76806-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="76806-111">Aşağıdaki tablo F# Etkileşimli tarafından desteklenen seçenekleri özetler.</span><span class="sxs-lookup"><span data-stu-id="76806-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="76806-112">Bu seçenekleri komut satırında veya Visual Studio IDE aracılığıyla ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76806-112">You can set these options on the command line or through the Visual Studio IDE.</span></span> <span data-ttu-id="76806-113">Visual Studio IDE 'de bu seçenekleri ayarlamak için, **Araçlar** menüsünü açın, **Seçenekler**' i seçin, **F # araçlar** düğümünü genişletin ve ardından **F# Etkileşimli**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="76806-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options**, expand the **F# Tools** node, and then select **F# Interactive**.</span></span>

<span data-ttu-id="76806-114">Listelerin F# Etkileşimli seçenek bağımsız değişkenlerinde göründüğü, liste öğeleri noktalı virgülle ( `;` ) ayrılır.</span><span class="sxs-lookup"><span data-stu-id="76806-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="76806-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="76806-115">Option</span></span>|<span data-ttu-id="76806-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76806-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="76806-117">F# Etkileşimli, diğer bağımsız değişkenleri F # programı veya betiğine komut satırı bağımsız değişkenleri olarak değerlendirmek için kullanılır. Bu, **fsi. Commandbir**listesini kullanarak koda erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76806-117">Used to instruct F# Interactive to treat remaining arguments as command-line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="76806-118">**--Checked**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-119">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-120">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-121">**--CodePage: &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="76806-122">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-123">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-125">Uyarı ve hata iletilerini renkli olarak verir.</span><span class="sxs-lookup"><span data-stu-id="76806-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="76806-126">**--çapraz iyileştirme**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-127">Modüller arası iyileştirmeleri etkinleştirin veya devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="76806-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="76806-128">**--Debug**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="76806-129">**--Debug:**[**Full**&#124;**pdbonly**&#124;**Taşınabilir**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="76806-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="76806-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="76806-131">**-g:**[**Full**&#124;**pdbonly**&#124;**Taşınabilir**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="76806-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="76806-132">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-133">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-134">**--tanımla: &lt; dize&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="76806-135">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-136">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-137">**--belirleyici**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-138">Belirleyici derleme üretir (Modül sürümü GUID 'i ve zaman damgası dahil).</span><span class="sxs-lookup"><span data-stu-id="76806-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="76806-139">**--Exec**</span><span class="sxs-lookup"><span data-stu-id="76806-139">**--exec**</span></span>|<span data-ttu-id="76806-140">Dosyaları yükledikten veya komut satırında verilen betik dosyasını çalıştırdıktan sonra F # Interactive 'e yöneltir.</span><span class="sxs-lookup"><span data-stu-id="76806-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="76806-141">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="76806-141">**--fullpaths**</span></span>|<span data-ttu-id="76806-142">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-143">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-144">**--GUI**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-145">Windows Forms olay döngüsünü etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="76806-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="76806-146">Varsayılan değer etkindir.</span><span class="sxs-lookup"><span data-stu-id="76806-146">The default is enabled.</span></span>|
|<span data-ttu-id="76806-147">**--yardım**</span><span class="sxs-lookup"><span data-stu-id="76806-147">**--help**</span></span><br /><br /><span data-ttu-id="76806-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="76806-148">**-?**</span></span>|<span data-ttu-id="76806-149">Komut satırı söz dizimini ve her seçeneğin kısa bir açıklamasını göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76806-149">Used to display the command-line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="76806-150">**--lib: &lt; Klasör-Listele&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="76806-151">**-I: &lt; Klasör-liste&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="76806-152">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-153">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-154">**--Yükle: &lt; dosya adı&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="76806-155">Başlangıçta verilen kaynak kodu derler ve derlenmiş F # yapılarını oturuma yükler.</span><span class="sxs-lookup"><span data-stu-id="76806-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span>|
|<span data-ttu-id="76806-156">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="76806-156">**--mlcompatibility**</span></span>|<span data-ttu-id="76806-157">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-157">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-158">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-158">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-159">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="76806-159">**--noframework**</span></span>|<span data-ttu-id="76806-160">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-160">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-161">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="76806-161">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="76806-162">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="76806-162">**--nologo**</span></span>|<span data-ttu-id="76806-163">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-163">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-164">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-164">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-165">**--nowarn: &lt; uyarı-liste&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-165">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="76806-166">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-166">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-167">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-167">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-168">**--optimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-168">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-169">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-169">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-170">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-170">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-171">**--preferreduilang: &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-171">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="76806-172">Tercih edilen çıkış dili kültür adını belirtir (örneğin, ES-ES, ja-JP).</span><span class="sxs-lookup"><span data-stu-id="76806-172">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="76806-173">**--quiet**</span><span class="sxs-lookup"><span data-stu-id="76806-173">**--quiet**</span></span>|<span data-ttu-id="76806-174">F# Etkileşimli **stdout** akışına çıktıyı gizleyin.</span><span class="sxs-lookup"><span data-stu-id="76806-174">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="76806-175">**--alıntılar-hata ayıkla**</span><span class="sxs-lookup"><span data-stu-id="76806-175">**--quotations-debug**</span></span>|<span data-ttu-id="76806-176">F # teklif değişmez değerleri ve yansıtılan tanımlardan türetilmiş ifadeler için ek hata ayıklama bilgilerinin yayınlanmasının gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="76806-176">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="76806-177">Hata ayıklama bilgileri bir F # ifade ağacı düğümünün özel özniteliklerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="76806-177">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="76806-178">Bkz. [kod teklifleri](code-quotations.md) ve [Expr. CustomAttributes](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html#CustomAttributes).</span><span class="sxs-lookup"><span data-stu-id="76806-178">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html#CustomAttributes).</span></span>|
|<span data-ttu-id="76806-179">**--ReadLine**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-179">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-180">Etkileşimli modda sekme tamamlamayı etkinleştirin veya devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="76806-180">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="76806-181">**--Başvuru: &lt; dosya adı&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-181">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="76806-182">**-r: &lt; dosya adı&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-182">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="76806-183">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-183">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-184">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-184">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-185">**--edilecek çağrılar**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-185">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-186">Tail Özyinelemeli işlevler için yığın çerçevesinin yeniden kullanılmasını sağlayan tail Il yönergesinin kullanımını etkinleştirin veya devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="76806-186">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="76806-187">Bu seçenek varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="76806-187">This option is enabled by default.</span></span>|
|<span data-ttu-id="76806-188">**--targetprofile: &lt; dize&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-188">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="76806-189">Bu derlemenin hedef çerçeve profilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="76806-189">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="76806-190">Geçerli değerler `mscorlib` , `netcore` , veya `netstandard` .</span><span class="sxs-lookup"><span data-stu-id="76806-190">Valid values are `mscorlib`, `netcore`, or `netstandard`.</span></span> <span data-ttu-id="76806-191">Varsayılan değer: `mscorlib`.</span><span class="sxs-lookup"><span data-stu-id="76806-191">The default is `mscorlib`.</span></span>|
|<span data-ttu-id="76806-192">**--şunu kullanın: &lt; dosya adı&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-192">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="76806-193">Yorumlayıcıya ilk girdi olarak başlangıçta verilen dosyayı kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="76806-193">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="76806-194">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="76806-194">**--utf8output**</span></span>|<span data-ttu-id="76806-195">fsc.exe derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-195">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="76806-196">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-196">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-197">**--warn: &lt; Uyarı düzeyi&gt;**</span><span class="sxs-lookup"><span data-stu-id="76806-197">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="76806-198">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-198">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-199">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-199">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-200">**--warnaserror**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="76806-200">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="76806-201">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-201">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-202">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-202">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="76806-203">**--warnaserror**[ **+**&#124;**-** ]:\*\* &lt; int-List &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="76806-203">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="76806-204">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="76806-204">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="76806-205">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="76806-205">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="76806-206">Yapılandırılmış yazdırma F# Etkileşimli</span><span class="sxs-lookup"><span data-stu-id="76806-206">F# Interactive structured printing</span></span>

<span data-ttu-id="76806-207">F# Etkileşimli ( `dotnet fsi` ), değerleri raporlamak için [yapılandırılmış düz metin biçimlendirmesinin](plaintext-formatting.md) genişletilmiş bir sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="76806-207">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="76806-208">`%A`Düz metin biçimlendirmesinin tüm özellikleri desteklenir ve bazıları ek olarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="76806-208">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="76806-209">Renkler çıkış Konsolu tarafından destekleniyorsa, yazdırma işlemi renklendirilir.</span><span class="sxs-lookup"><span data-stu-id="76806-209">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="76806-210">Bu dizeyi açıkça değerlendirmediğiniz takdirde, gösterilen dizelerin uzunluğuna bir sınır konur.</span><span class="sxs-lookup"><span data-stu-id="76806-210">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="76806-211">Kullanıcı tanımlı bir ayarlar kümesi nesne aracılığıyla kullanılabilir `fsi` .</span><span class="sxs-lookup"><span data-stu-id="76806-211">A set of user-definable settings is available via the `fsi` object.</span></span>

<span data-ttu-id="76806-212">Bildirilen değerler için düz metin yazdırmayı özelleştirmek için kullanılabilir ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="76806-212">The available settings to customize plain text printing for reported values are:</span></span>

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="76806-213">Ve ile özelleştirin `AddPrinter``AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="76806-213">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="76806-214">F# Etkileşimli çıktılarında yazdırma, ve kullanılarak özelleştirilebilir `fsi.AddPrinter` `fsi.AddPrintTransformer` .</span><span class="sxs-lookup"><span data-stu-id="76806-214">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="76806-215">İlk işlev, bir nesnenin yazdırılmasını değiştirecek metin verir.</span><span class="sxs-lookup"><span data-stu-id="76806-215">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="76806-216">İkinci işlev bunun yerine görüntülenecek bir vekil nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="76806-216">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="76806-217">Örneğin, aşağıdaki F # kodunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="76806-217">For example, consider the following F# code:</span></span>

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

<span data-ttu-id="76806-218">Örneği F# Etkileşimli ' de çalıştırırsanız, biçimlendirme seçenek kümesine göre çıkış yapılır.</span><span class="sxs-lookup"><span data-stu-id="76806-218">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="76806-219">Bu durumda, tarih ve saat biçimlendirmesini etkiler:</span><span class="sxs-lookup"><span data-stu-id="76806-219">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="76806-220">`fsi.AddPrintTransformer` , yazdırma için bir yedek nesne vermek üzere kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="76806-220">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="76806-221">Bu çıktılar:</span><span class="sxs-lookup"><span data-stu-id="76806-221">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="76806-222">Transformatör işlevi geçirildiğinde `fsi.AddPrintTransformer` `null` , yazdırma transformatörü yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="76806-222">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="76806-223">Bu, tür ile başlayarak herhangi bir giriş değerini filtrelemek için kullanılabilir `obj` .</span><span class="sxs-lookup"><span data-stu-id="76806-223">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="76806-224">Örnek:</span><span class="sxs-lookup"><span data-stu-id="76806-224">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="76806-225">Bu çıktılar:</span><span class="sxs-lookup"><span data-stu-id="76806-225">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="76806-226">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="76806-226">Related topics</span></span>

|<span data-ttu-id="76806-227">Başlık</span><span class="sxs-lookup"><span data-stu-id="76806-227">Title</span></span>|<span data-ttu-id="76806-228">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76806-228">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="76806-229">Derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="76806-229">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="76806-230">F # derleyicisi için kullanılabilen komut satırı seçeneklerini açıklar, **fsc.exe**.</span><span class="sxs-lookup"><span data-stu-id="76806-230">Describes command-line options available for the F# compiler, **fsc.exe**.</span></span>|
