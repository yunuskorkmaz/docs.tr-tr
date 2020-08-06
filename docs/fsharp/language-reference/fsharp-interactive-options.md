---
title: Etkileşimli Seçenekler
description: F# Etkileşimli, fsi.exe tarafından desteklenen komut satırı seçenekleri hakkında bilgi edinin.
ms.date: 07/22/2020
ms.openlocfilehash: f9932cac24fad187c332306968fb13981912e80a
ms.sourcegitcommit: 09bad6ec0cbf18be7cd7f62e77286d305a18b607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87795469"
---
# <a name="f-interactive-options"></a><span data-ttu-id="d3348-103">F# Etkileşimli seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d3348-103">F# Interactive options</span></span>

<span data-ttu-id="d3348-104">Bu makalede, F# Etkileşimli tarafından desteklenen komut satırı seçenekleri açıklanmaktadır `fsi.exe` .</span><span class="sxs-lookup"><span data-stu-id="d3348-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="d3348-105">F# Etkileşimli, F # derleyicisi ile aynı komut satırı seçeneklerinin çoğunu kabul eder, ancak Ayrıca bazı ek seçenekleri de kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d3348-105">F# Interactive accepts many of the same command line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="d3348-106">Betik için F# Etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="d3348-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="d3348-107">F# Etkileşimli, `dotnet fsi` etkileşimli olarak başlatılabilir veya bir betiği çalıştırmak için komut satırından başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3348-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="d3348-108">Komut satırı söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d3348-108">The command line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="d3348-109">F # betik dosyaları için dosya uzantısı `.fsx` .</span><span class="sxs-lookup"><span data-stu-id="d3348-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="d3348-110">F# Etkileşimli seçenekleri tablosu</span><span class="sxs-lookup"><span data-stu-id="d3348-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="d3348-111">Aşağıdaki tablo F# Etkileşimli tarafından desteklenen seçenekleri özetler.</span><span class="sxs-lookup"><span data-stu-id="d3348-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="d3348-112">Bu seçenekleri komut satırında veya Visual Studio IDE aracılığıyla ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3348-112">You can set these options on the command-line or through the Visual Studio IDE.</span></span> <span data-ttu-id="d3348-113">Bu seçenekleri Visual Studio IDE 'de ayarlamak için, **Araçlar** menüsünü açın, **Seçenekler...**' i seçin, ardından **F # araçları** düğümünü genişletin ve **F# Etkileşimli**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d3348-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options...**, then expand the **F# Tools** node and select **F# Interactive**.</span></span>

<span data-ttu-id="d3348-114">Listelerin F# Etkileşimli seçenek bağımsız değişkenlerinde göründüğü, liste öğeleri noktalı virgülle ( `;` ) ayrılır.</span><span class="sxs-lookup"><span data-stu-id="d3348-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="d3348-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="d3348-115">Option</span></span>|<span data-ttu-id="d3348-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3348-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="d3348-117">F# Etkileşimli, diğer bağımsız değişkenleri F # programı veya betiğine komut satırı bağımsız değişkeni olarak değerlendirmek için kullanılır. Bu, **fsi. Commandbir**listesini kullanarak koda erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3348-117">Used to instruct F# Interactive to treat remaining arguments as command line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="d3348-118">**--Checked**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-119">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-120">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-121">**--CodePage: &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="d3348-122">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-123">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-125">Uyarı ve hata iletilerini renkli olarak verir.</span><span class="sxs-lookup"><span data-stu-id="d3348-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="d3348-126">**--çapraz iyileştirme**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-127">Modüller arası iyileştirmeleri etkinleştirin veya devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="d3348-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="d3348-128">**--Debug**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="d3348-129">**--Debug:**[**Full**&#124;**pdbonly**&#124;**Taşınabilir**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="d3348-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="d3348-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="d3348-131">**-g:**[**Full**&#124;**pdbonly**&#124;**Taşınabilir**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="d3348-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="d3348-132">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-133">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-134">**--tanımla: &lt; dize&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="d3348-135">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-136">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-137">**--belirleyici**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-138">Belirleyici derleme üretir (Modül sürümü GUID 'i ve zaman damgası dahil).</span><span class="sxs-lookup"><span data-stu-id="d3348-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="d3348-139">**--Exec**</span><span class="sxs-lookup"><span data-stu-id="d3348-139">**--exec**</span></span>|<span data-ttu-id="d3348-140">Dosyaları yükledikten veya komut satırında verilen betik dosyasını çalıştırdıktan sonra F # Interactive 'e yöneltir.</span><span class="sxs-lookup"><span data-stu-id="d3348-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="d3348-141">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="d3348-141">**--fullpaths**</span></span>|<span data-ttu-id="d3348-142">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-143">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-144">**--GUI**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-145">Windows Forms olay döngüsünü etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d3348-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="d3348-146">Varsayılan değer etkindir.</span><span class="sxs-lookup"><span data-stu-id="d3348-146">The default is enabled.</span></span>|
|<span data-ttu-id="d3348-147">**--yardım**</span><span class="sxs-lookup"><span data-stu-id="d3348-147">**--help**</span></span><br /><br /><span data-ttu-id="d3348-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="d3348-148">**-?**</span></span>|<span data-ttu-id="d3348-149">Komut satırı söz dizimini ve her seçeneğin kısa bir açıklamasını göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3348-149">Used to display the command line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="d3348-150">**--lib: &lt; Klasör-Listele&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="d3348-151">**-I: &lt; Klasör-liste&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="d3348-152">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-153">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-154">**--Yükle: &lt; dosya adı&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="d3348-155">Başlangıçta verilen kaynak kodu derler ve derlenmiş F # yapılarını oturuma yükler.</span><span class="sxs-lookup"><span data-stu-id="d3348-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span> <span data-ttu-id="d3348-156">Hedef kaynak **#use** veya **#load**gibi komut dosyası yönergeleri içeriyorsa,-- **Load** veya **#load**yerine **--Use** veya **#use** kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3348-156">If the target source contains scripting directives such as **#use** or **#load**, then you must use **--use** or **#use** instead of **--load** or **#load**.</span></span>|
|<span data-ttu-id="d3348-157">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="d3348-157">**--mlcompatibility**</span></span>|<span data-ttu-id="d3348-158">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-158">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-159">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-159">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-160">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="d3348-160">**--noframework**</span></span>|<span data-ttu-id="d3348-161">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-161">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-162">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="d3348-162">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="d3348-163">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="d3348-163">**--nologo**</span></span>|<span data-ttu-id="d3348-164">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-164">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-165">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-165">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-166">**--nowarn: &lt; uyarı-liste&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-166">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="d3348-167">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-167">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-168">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-168">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-169">**--optimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-169">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-170">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-170">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-171">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-171">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-172">**--preferreduilang: &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-172">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="d3348-173">Tercih edilen çıkış dili kültür adını belirtir (örneğin, ES-ES, ja-JP).</span><span class="sxs-lookup"><span data-stu-id="d3348-173">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="d3348-174">**--quiet**</span><span class="sxs-lookup"><span data-stu-id="d3348-174">**--quiet**</span></span>|<span data-ttu-id="d3348-175">F# Etkileşimli **stdout** akışına çıktıyı gizleyin.</span><span class="sxs-lookup"><span data-stu-id="d3348-175">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="d3348-176">**--alıntılar-hata ayıkla**</span><span class="sxs-lookup"><span data-stu-id="d3348-176">**--quotations-debug**</span></span>|<span data-ttu-id="d3348-177">F # teklif değişmez değerleri ve yansıtılan tanımlardan türetilmiş ifadeler için ek hata ayıklama bilgilerinin yayınlanmasının gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3348-177">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="d3348-178">Hata ayıklama bilgileri bir F # ifade ağacı düğümünün özel özniteliklerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="d3348-178">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="d3348-179">Bkz. [kod teklifleri](code-quotations.md) ve [Expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span><span class="sxs-lookup"><span data-stu-id="d3348-179">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span></span>|
|<span data-ttu-id="d3348-180">**--ReadLine**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-180">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-181">Etkileşimli modda sekme tamamlamayı etkinleştirin veya devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="d3348-181">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="d3348-182">**--Başvuru: &lt; dosya adı&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-182">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="d3348-183">**-r: &lt; dosya adı&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-183">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="d3348-184">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-184">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-185">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-185">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-186">**--edilecek çağrılar**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-186">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-187">Tail Özyinelemeli işlevler için yığın çerçevesinin yeniden kullanılmasını sağlayan tail Il yönergesinin kullanımını etkinleştirin veya devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="d3348-187">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="d3348-188">Bu seçenek varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="d3348-188">This option is enabled by default.</span></span>|
|<span data-ttu-id="d3348-189">**--targetprofile: &lt; dize&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-189">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="d3348-190">Bu derlemenin hedef çerçeve profilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3348-190">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="d3348-191">Geçerli değerler mscorlib, netcore veya Netstandard ' dır.</span><span class="sxs-lookup"><span data-stu-id="d3348-191">Valid values are mscorlib, netcore or netstandard.</span></span>  <span data-ttu-id="d3348-192">Varsayılan olarak mscorlib 'dir.</span><span class="sxs-lookup"><span data-stu-id="d3348-192">The default is mscorlib.</span></span>|
|<span data-ttu-id="d3348-193">**--şunu kullanın: &lt; dosya adı&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-193">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="d3348-194">Yorumlayıcıya ilk girdi olarak başlangıçta verilen dosyayı kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="d3348-194">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="d3348-195">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="d3348-195">**--utf8output**</span></span>|<span data-ttu-id="d3348-196">fsc.exe derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-196">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="d3348-197">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-197">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-198">**--warn: &lt; Uyarı düzeyi&gt;**</span><span class="sxs-lookup"><span data-stu-id="d3348-198">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="d3348-199">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-199">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-200">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-200">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-201">**--warnaserror**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="d3348-201">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="d3348-202">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-202">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-203">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-203">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="d3348-204">**--warnaserror**[ **+**&#124;**-** ]:\*\* &lt; int-List &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="d3348-204">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="d3348-205">**fsc.exe** derleyici seçeneği ile aynı.</span><span class="sxs-lookup"><span data-stu-id="d3348-205">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="d3348-206">Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="d3348-206">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="d3348-207">Yapılandırılmış yazdırma F# Etkileşimli</span><span class="sxs-lookup"><span data-stu-id="d3348-207">F# Interactive structured printing</span></span>

<span data-ttu-id="d3348-208">F# Etkileşimli ( `dotnet fsi` ), değerleri raporlamak için [yapılandırılmış düz metin biçimlendirmesinin](plaintext-formatting.md) genişletilmiş bir sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3348-208">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="d3348-209">`%A`Düz metin biçimlendirmesinin tüm özellikleri desteklenir ve bazıları ek olarak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d3348-209">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="d3348-210">Renkler çıkış Konsolu tarafından destekleniyorsa, yazdırma işlemi renklendirilir.</span><span class="sxs-lookup"><span data-stu-id="d3348-210">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="d3348-211">Bu dizeyi açıkça değerlendirmediğiniz takdirde, gösterilen dizelerin uzunluğuna bir sınır konur.</span><span class="sxs-lookup"><span data-stu-id="d3348-211">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="d3348-212">Kullanıcı tanımlı bir ayarlar kümesi nesne aracılığıyla kullanılabilir `fsi` .</span><span class="sxs-lookup"><span data-stu-id="d3348-212">A set of user-definable settings are available via the `fsi` object.</span></span>

<span data-ttu-id="d3348-213">Bildirilen değerler için düz metin yazdırmayı özelleştirmek için kullanılabilir ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d3348-213">The available settings to customize plain text printing for reported values are:</span></span>

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

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="d3348-214">Ve ile özelleştirin `AddPrinter``AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="d3348-214">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="d3348-215">F# Etkileşimli çıktılarında yazdırma, ve kullanılarak özelleştirilebilir `fsi.AddPrinter` `fsi.AddPrintTransformer` .</span><span class="sxs-lookup"><span data-stu-id="d3348-215">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="d3348-216">İlk işlev, bir nesnenin yazdırılmasını değiştirecek metin verir.</span><span class="sxs-lookup"><span data-stu-id="d3348-216">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="d3348-217">İkinci işlev bunun yerine görüntülenecek bir vekil nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3348-217">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="d3348-218">Örneğin, aşağıdaki F # kodunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d3348-218">For example, consider the following F# code:</span></span>

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

<span data-ttu-id="d3348-219">Örneği F# Etkileşimli ' de çalıştırırsanız, biçimlendirme seçenek kümesine göre çıkış yapılır.</span><span class="sxs-lookup"><span data-stu-id="d3348-219">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="d3348-220">Bu durumda, tarih ve saat biçimlendirmesini etkiler:</span><span class="sxs-lookup"><span data-stu-id="d3348-220">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="d3348-221">`fsi.AddPrintTransformer`, yazdırma için bir yedek nesne vermek üzere kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d3348-221">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="d3348-222">Bu çıktılar:</span><span class="sxs-lookup"><span data-stu-id="d3348-222">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="d3348-223">Transformatör işlevi geçirildiğinde `fsi.AddPrintTransformer` `null` , yazdırma transformatörü yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d3348-223">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="d3348-224">Bu, tür ile başlayarak herhangi bir giriş değerini filtrelemek için kullanılabilir `obj` .</span><span class="sxs-lookup"><span data-stu-id="d3348-224">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="d3348-225">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d3348-225">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="d3348-226">Bu çıktılar:</span><span class="sxs-lookup"><span data-stu-id="d3348-226">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="d3348-227">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="d3348-227">Related topics</span></span>

|<span data-ttu-id="d3348-228">Başlık</span><span class="sxs-lookup"><span data-stu-id="d3348-228">Title</span></span>|<span data-ttu-id="d3348-229">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3348-229">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="d3348-230">Derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d3348-230">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="d3348-231">F # derleyicisi için kullanılabilen komut satırı seçeneklerini açıklar, **fsc.exe**.</span><span class="sxs-lookup"><span data-stu-id="d3348-231">Describes command line options available for the F# compiler, **fsc.exe**.</span></span>|
