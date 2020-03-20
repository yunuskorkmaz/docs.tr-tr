---
title: Ilasm.exe (IL Derleyici)
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: cb995e78e534048043886070536ef0dd0a45c057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105099"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="684a5-102">Ilasm.exe (IL Derleyici)</span><span class="sxs-lookup"><span data-stu-id="684a5-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="684a5-103">IL Derleyicisi ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="684a5-104">(IL hakkında daha fazla bilgi için yönetilen [yürütme işlemi](../../standard/managed-execution-process.md)ne bakın.) IL'nin beklendiği gibi çalışıp çalışmadığını belirlemek için IL ve gerekli meta verileri içeren ortaya çıkan yürütülebilir çalıştırılabilir çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="684a5-104">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="684a5-105">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="684a5-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="684a5-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span><span class="sxs-lookup"><span data-stu-id="684a5-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="684a5-107">Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="684a5-107">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="684a5-108">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="684a5-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="684a5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="684a5-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="684a5-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="684a5-110">Parameters</span></span>

| <span data-ttu-id="684a5-111">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="684a5-111">Argument</span></span> | <span data-ttu-id="684a5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="684a5-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="684a5-113">.il kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="684a5-113">The name of the .il source file.</span></span> <span data-ttu-id="684a5-114">Bu dosya meta veri bildirim yönergeleri ve simgesel IL yönergelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="684a5-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="684a5-115">Birden çok kaynak dosya bağımsız değişkenleri *Ilasm.exe*ile tek bir PE dosyası üretmek için sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="684a5-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="684a5-116">**Not:** .il kaynak dosyasındaki son kod satırının beyaz boşluk veya satır sonu karakterinin gerisinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="684a5-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="684a5-117">Seçenek</span><span class="sxs-lookup"><span data-stu-id="684a5-117">Option</span></span> | <span data-ttu-id="684a5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="684a5-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="684a5-119">**/32bittercih**</span><span class="sxs-lookup"><span data-stu-id="684a5-119">**/32bitpreferred**</span></span>|<span data-ttu-id="684a5-120">32 bit tercih edilen bir görüntü (PE32) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="684a5-121">**/hizalama:**`integer`</span><span class="sxs-lookup"><span data-stu-id="684a5-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="684a5-122">FileAlignment'ı NT `integer` İsteğe Bağlı üstbilgide belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="684a5-123">Eğer .alignment IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="684a5-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="684a5-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="684a5-124">**/appcontainer**</span></span>|<span data-ttu-id="684a5-125">Çıktı olarak Windows uygulama kapsayıcısında çalışan bir *.dll* veya *.exe* dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="684a5-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="684a5-126">**/kol**</span><span class="sxs-lookup"><span data-stu-id="684a5-126">**/arm**</span></span>|<span data-ttu-id="684a5-127">Hedef işlemci olarak Gelişmiş RISC Makinesi (ARM) belirtir.</span><span class="sxs-lookup"><span data-stu-id="684a5-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="684a5-128">Görüntü bitliği belirtilmemişse, varsayılan **değer /32bitpreferred.**</span><span class="sxs-lookup"><span data-stu-id="684a5-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="684a5-129">**/taban:**`integer`</span><span class="sxs-lookup"><span data-stu-id="684a5-129">**/base:** `integer`</span></span>|<span data-ttu-id="684a5-130">ImageBase'i NT `integer` İsteğe Bağlı üstbilgide belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="684a5-131">Eğer .imagebase IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="684a5-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="684a5-132">**/saat**</span><span class="sxs-lookup"><span data-stu-id="684a5-132">**/clock**</span></span>|<span data-ttu-id="684a5-133">Belirtilen .il kaynak dosyası için aşağıdaki derleme sürelerini milisaniye cinsinden ölçer ve raporlar:</span><span class="sxs-lookup"><span data-stu-id="684a5-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="684a5-134">**Toplam Çalıştırma**: Takip eden tüm belirli işlemleri gerçekleştirmek için harcanan toplam süre.</span><span class="sxs-lookup"><span data-stu-id="684a5-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="684a5-135">**Başlangıç**: Dosyayı yükleme ve açma.</span><span class="sxs-lookup"><span data-stu-id="684a5-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="684a5-136">**Yayan MD**: Meta veri yayan.</span><span class="sxs-lookup"><span data-stu-id="684a5-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="684a5-137">**Ref to Def Resolution**: Dosyadaki tanımlara yapılan başvuruların çözülmesi.</span><span class="sxs-lookup"><span data-stu-id="684a5-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="684a5-138">**CEE Dosya Oluşturma**: Bellekte dosya görüntüsü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="684a5-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="684a5-139">**PE Dosya Yazma**: Resmin PE dosyasına yazılması.</span><span class="sxs-lookup"><span data-stu-id="684a5-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="684a5-140">**/hata ayıklama**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="684a5-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="684a5-141">Hata ayıklama bilgisi içerir (yerel değişken ve bağımsız değişken adları ve satır numaraları).</span><span class="sxs-lookup"><span data-stu-id="684a5-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="684a5-142">Bir PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="684a5-143">**/debug** hiçbir ek değeri ile JIT optimizasyonu devre dışı ve PDB dosyasından sıra noktaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="684a5-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="684a5-144">**IMPL,** JIT optimizasyonunu devre dışı kılabilir ve örtük sıra noktalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="684a5-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="684a5-145">**OPT,** JIT optimizasyonunu sağlar ve örtük sıra noktalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="684a5-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="684a5-146">**/dll**</span><span class="sxs-lookup"><span data-stu-id="684a5-146">**/dll**</span></span>|<span data-ttu-id="684a5-147">Çıktı olarak *bir .dll* dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="684a5-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="684a5-148">**/enc:**`file`</span><span class="sxs-lookup"><span data-stu-id="684a5-148">**/enc:** `file`</span></span>|<span data-ttu-id="684a5-149">Belirtilen kaynak dosyasından Düzenle ve Devam Et deltaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="684a5-150">Bu bağımsız değişken yalnızca akademik amaçlıdır ve ticari kullanım için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="684a5-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="684a5-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="684a5-151">**/exe**</span></span>|<span data-ttu-id="684a5-152">Çıktı olarak bir yürütülebilir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-152">Produces an executable file as output.</span></span> <span data-ttu-id="684a5-153">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="684a5-153">This is the default.</span></span>|
|<span data-ttu-id="684a5-154">**/bayraklar:**`integer`</span><span class="sxs-lookup"><span data-stu-id="684a5-154">**/flags:** `integer`</span></span>|<span data-ttu-id="684a5-155">ImageFlags'i ortak dil `integer` çalışma zamanı üstbilgisinde belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="684a5-156">Eğer .corflags IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="684a5-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="684a5-157">Tamsayı için geçerli değerlerin listesi için COMIMAGE_FLAGS *integer*CorHdr.h'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="684a5-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="684a5-158">**/kat**</span><span class="sxs-lookup"><span data-stu-id="684a5-158">**/fold**</span></span>|<span data-ttu-id="684a5-159">Eşdeğer metot gövdelerini tek bir gövde olarak katlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="684a5-160">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="684a5-160">/**highentropyva**</span></span>|<span data-ttu-id="684a5-161">Yüksek entropili adres alanı düzenini (ASLR) destekleyen bir çıktı çalıştırılabilir dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="684a5-162">(Varsayılan **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="684a5-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="684a5-163">**/dahil:**`includePath`</span><span class="sxs-lookup"><span data-stu-id="684a5-163">**/include:** `includePath`</span></span>|<span data-ttu-id="684a5-164">'ye `#include`dahil olan dosyaları aramak için bir yol ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="684a5-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="684a5-165">**/itanium**</span></span>|<span data-ttu-id="684a5-166">Hedef işlemci olarak Intel Itanium belirtir.</span><span class="sxs-lookup"><span data-stu-id="684a5-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="684a5-167">Görüntü bitliği belirtilmemişse, varsayılan değer **/pe64'dür.**</span><span class="sxs-lookup"><span data-stu-id="684a5-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="684a5-168">**/tuşu:**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="684a5-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="684a5-169">'de `filename` `keyFile`bulunan özel anahtarı kullanarak güçlü bir imza ile derler.</span><span class="sxs-lookup"><span data-stu-id="684a5-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="684a5-170">**/tuşu:** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="684a5-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="684a5-171">Üretilen `filename` özel anahtarı kullanarak güçlü bir `keySource`imza ile derler.</span><span class="sxs-lookup"><span data-stu-id="684a5-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="684a5-172">**/listeleme**</span><span class="sxs-lookup"><span data-stu-id="684a5-172">**/listing**</span></span>|<span data-ttu-id="684a5-173">Standart çıktıda bir listeleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="684a5-174">Eğer bu seçeneği koymazsanız, listeleme dosyası oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="684a5-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="684a5-175">Bu parametre .NET Framework 2.0 ve sonrasında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="684a5-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="684a5-176">**/mdv:**`versionString`</span><span class="sxs-lookup"><span data-stu-id="684a5-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="684a5-177">Meta veri sürümü dizesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="684a5-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="684a5-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="684a5-179">Meta veri akışı sürümünü, `major` `minor` nerede ve tamsayılar olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="684a5-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="684a5-180">**/noautoinherit**</span></span>|<span data-ttu-id="684a5-181">Temel sınıf belirtilmediğinde varsayılan <xref:System.Object> kalıtım devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="684a5-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="684a5-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="684a5-182">**/nocorstub**</span></span>|<span data-ttu-id="684a5-183">CORExeMain taslağının oluşturulmasını bastırır.</span><span class="sxs-lookup"><span data-stu-id="684a5-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="684a5-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="684a5-184">**/nologo**</span></span>|<span data-ttu-id="684a5-185">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="684a5-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="684a5-186">**/çıkış:**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="684a5-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="684a5-187">Çıktı dosyası adını ve uzantısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="684a5-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="684a5-188">Varsayılan olarak, çıktı dosyası adı ilk kaynak dosyasının adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="684a5-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="684a5-189">Varsayılan uzantı *.exe'dir.*</span><span class="sxs-lookup"><span data-stu-id="684a5-189">The default extension is *.exe*.</span></span> <span data-ttu-id="684a5-190">**/dll** seçeneğini belirtirseniz, varsayılan uzantı *.dll'dir.*</span><span class="sxs-lookup"><span data-stu-id="684a5-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="684a5-191">**Not:** Belirtilmesi **/output**:myfile.dll **/dll** seçeneğini ayarlamaz.</span><span class="sxs-lookup"><span data-stu-id="684a5-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="684a5-192">**/dll**belirtmezseniz, sonuç *myfile.dll*adlı yürütülebilir bir dosya olacaktır.</span><span class="sxs-lookup"><span data-stu-id="684a5-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="684a5-193">**/optimize etmek**</span><span class="sxs-lookup"><span data-stu-id="684a5-193">**/optimize**</span></span>|<span data-ttu-id="684a5-194">Uzun yönergeleri kısa olarak iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="684a5-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="684a5-195">Örneğin, `br` `br.s`.</span><span class="sxs-lookup"><span data-stu-id="684a5-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="684a5-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="684a5-196">**/pe64**</span></span>|<span data-ttu-id="684a5-197">64 bitlik bir görüntü oluşturur (PE32+).</span><span class="sxs-lookup"><span data-stu-id="684a5-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="684a5-198">Hedef işlemci belirtilmemişse, `/itanium`varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="684a5-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="684a5-199">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="684a5-199">**/pdb**</span></span>|<span data-ttu-id="684a5-200">Hata ayıklama bilgisi izlemeyi etkinleştirmeden bir PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="684a5-201">**/sessiz**</span><span class="sxs-lookup"><span data-stu-id="684a5-201">**/quiet**</span></span>|<span data-ttu-id="684a5-202">Sessiz modu belirtir; hiçbir derleme ilerlemesini bildirmez.</span><span class="sxs-lookup"><span data-stu-id="684a5-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="684a5-203">**/kaynak:**`file.res`</span><span class="sxs-lookup"><span data-stu-id="684a5-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="684a5-204">Belirtilen kaynak dosyasını \*.res biçiminde ortaya çıkan *.exe* veya *.dll* dosyasında içerir.</span><span class="sxs-lookup"><span data-stu-id="684a5-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="684a5-205">Sadece bir .res dosyası **/kaynak** seçeneği ile belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="684a5-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="684a5-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="684a5-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="684a5-207">NT isteğe bağlı üst bilgisinde alt sistem sürümünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="684a5-208">**/appcontainer** ve **/arm** için minimum sürüm numarası 6.02'dir.</span><span class="sxs-lookup"><span data-stu-id="684a5-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="684a5-209">**/yığın:**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="684a5-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="684a5-210">NT İsteğe Bağlı üstbilgideki SizeOfStackReserve değerini `stackSize`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="684a5-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="684a5-211">**/stripreloc**</span></span>|<span data-ttu-id="684a5-212">Temel yeniden konumlandırmanın gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="684a5-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="684a5-213">**/alt sistem:**`integer`</span><span class="sxs-lookup"><span data-stu-id="684a5-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="684a5-214">Alt sistemi NT İsteğe Bağlı `integer` üstbilgide belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="684a5-215">Eğer .subsystem IL yönergesi dosyada belirtiliyorsa, bu komut onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="684a5-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="684a5-216">Winnt.h için geçerli değerlerin listesi için `integer`IMAGE_SUBSYSTEM bakın.</span><span class="sxs-lookup"><span data-stu-id="684a5-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="684a5-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="684a5-217">**/x64**</span></span>|<span data-ttu-id="684a5-218">Hedef işlemci olarak bir 64 bitlik AMD işlemci belirtir.</span><span class="sxs-lookup"><span data-stu-id="684a5-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="684a5-219">Görüntü bitliği belirtilmemişse, varsayılan değer **/pe64'dür.**</span><span class="sxs-lookup"><span data-stu-id="684a5-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="684a5-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="684a5-220">**/?**</span></span>|<span data-ttu-id="684a5-221">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="684a5-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="684a5-222">*Ilasm.exe* için tüm seçenekler büyük/küçük harf duyarsız ve ilk üç harf tarafından tanınan.</span><span class="sxs-lookup"><span data-stu-id="684a5-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="684a5-223">Örneğin, **/lis** **/listing** ve **/res**:myresfile.res eşdeğerdir **/kaynak**:myresfile.res. Bağımsız değişkenleri belirten seçenekler iki nokta üst üste kabul eder (:) veya seçenek ve bağımsız değişken arasındaki ayırıcı olarak eşit bir işaret (=) olur.</span><span class="sxs-lookup"><span data-stu-id="684a5-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="684a5-224">Örneğin, **/output**:*file.ext* **/output**=*file.ext'e*eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="684a5-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="684a5-225">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="684a5-225">Remarks</span></span>

<span data-ttu-id="684a5-226">IL Derleyicisi araç satıcılarına IL oluşturucuları tasarlamaları ve uygulamaları için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="684a5-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="684a5-227">*Ilasm.exe*kullanarak, araç ve derleyici geliştiriciler IL ve meta veri üretimi pe dosya biçiminde IL yayan ile ilgili olmadan konsantre olabilir.</span><span class="sxs-lookup"><span data-stu-id="684a5-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="684a5-228">C# ve Visual Basic gibi çalışma süresini hedefleyen diğer derleyicilere benzer şekilde, *Ilasm.exe* ara nesne dosyaları üretmez ve PE dosyası oluşturmak için bağlama aşaması gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="684a5-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="684a5-229">IL Derleyicisi, çalışma zamanını hedef alan programlama dillerinin tüm varolan meta veri ve IL özelliklerini ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="684a5-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="684a5-230">Bu, bu programlama dillerinden herhangi birinde yazılmış yönetilen kodun IL Assembler'da yeterince ifade edilmesine ve *Ilasm.exe*ile derlenmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="684a5-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="684a5-231">Eğer .il kaynak dosyasının son kod satırında bir boşluk veya satır sonu karakteri yoksa derleme başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="684a5-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="684a5-232">Onun arkadaşı aracı, [*Ildasm.exe*](ildasm-exe-il-disassembler.md)ile birlikte *Ilasm.exe* kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="684a5-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="684a5-233">*Ildasm.exe* IL kodu içeren bir PE dosyası alır ve *Ilasm.exe*girişi olarak uygun bir metin dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="684a5-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="684a5-234">Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="684a5-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="684a5-235">Kodu derleyip çıktıyı *Ildasm.exe*üzerinden çalıştırdıktan sonra, ortaya çıkan IL metin dosyası eksik öznitelikleri eklemek için elle düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="684a5-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="684a5-236">Daha sonra son yürütülebilir dosyayı oluşturmak için bu metin dosyasını *Ilasm.exe* üzerinden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="684a5-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="684a5-237">Bu tekniği kullanarak ayrı derleyiciler tarafından üretilen çeşitli PE dosyalarından tek bir PE dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="684a5-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="684a5-238">Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="684a5-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="684a5-239">*Ildasm.exe* ve *Ilasm.exe'nin* bu birleşik kullanımını mümkün olduğunca doğru hale getirmek için, varsayılan olarak assembler IL kaynaklarınızda yazmış olabileceğiniz (veya başka bir derleyici tarafından yayılmış olabilecek) uzun kodlamaları yerine almaz.</span><span class="sxs-lookup"><span data-stu-id="684a5-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="684a5-240">Mümkün olan her yerde kısa kodlamaların yerine **/optimize** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="684a5-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="684a5-241">*Ildasm.exe* sadece diskteki dosyalarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="684a5-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="684a5-242">Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="684a5-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="684a5-243">IL dilbilgisi hakkında daha fazla bilgi için Windows SDK'daki asmparse.grammar dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="684a5-243">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="684a5-244">Sürüm Bilgileri</span><span class="sxs-lookup"><span data-stu-id="684a5-244">Version Information</span></span>

<span data-ttu-id="684a5-245">.NET Framework 4.5 ile başlayarak, aşağıdakilere benzer bir kod kullanarak arabirim uygulamasına özel bir öznitelik ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="684a5-245">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="684a5-246">.NET Framework 4.5 ile başlayarak, aşağıdaki kodda gösterildiği gibi ham ikili gösterimini kullanarak rasgele bir mareşal BLOB (ikili büyük nesne) belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="684a5-246">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="684a5-247">IL dilbilgisi hakkında daha fazla bilgi için Windows SDK'daki asmparse.grammar dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="684a5-247">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="684a5-248">Örnekler</span><span class="sxs-lookup"><span data-stu-id="684a5-248">Examples</span></span>

<span data-ttu-id="684a5-249">Aşağıdaki komut IL dosyasını *myTestFile.il* toplar ve çalıştırılabilir *myTestFile.exe'yi*üretir.</span><span class="sxs-lookup"><span data-stu-id="684a5-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="684a5-250">Aşağıdaki komut IL dosyasını *myTestFile.il* toplar ve *.dll* dosya *myTestFile.dll*üretir.</span><span class="sxs-lookup"><span data-stu-id="684a5-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="684a5-251">Aşağıdaki komut IL dosyasını *myTestFile.il* toplar ve *.dll* dosya *myNewTestFile.dll*üretir.</span><span class="sxs-lookup"><span data-stu-id="684a5-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="684a5-252">Aşağıdaki kod örneği "Merhaba Dünya!" gösteren son derece basit bir uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="684a5-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="684a5-253">metnini görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="684a5-253">to the console.</span></span> <span data-ttu-id="684a5-254">Bu kodu derleyebilir ve il dosyası oluşturmak için [*Ildasm.exe*](ildasm-exe-il-disassembler.md) aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="684a5-254">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="684a5-255">Aşağıdaki IL kod örneği önceki C# kod örneğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="684a5-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="684a5-256">Bu kodu IL Assembler aracını kullanarak bir derlemeye ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="684a5-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="684a5-257">Hem IL hem de C# kod örnekleri "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="684a5-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="684a5-258">metnini görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="684a5-258">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="684a5-259">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="684a5-259">See also</span></span>

- [<span data-ttu-id="684a5-260">Araçlar</span><span class="sxs-lookup"><span data-stu-id="684a5-260">Tools</span></span>](index.md)
- [<span data-ttu-id="684a5-261">*Ildasm.exe* (IL Desassembler)</span><span class="sxs-lookup"><span data-stu-id="684a5-261">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="684a5-262">Yönetilen Yürütme İşlemi</span><span class="sxs-lookup"><span data-stu-id="684a5-262">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="684a5-263">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="684a5-263">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
