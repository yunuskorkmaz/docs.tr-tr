---
title: Ilasm.exe (IL Derleyici)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b95f3d70c7329efd1affcb333ac6eee08cc29d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="4c2fe-102">Ilasm.exe (IL Derleyici)</span><span class="sxs-lookup"><span data-stu-id="4c2fe-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="4c2fe-103">IL Derleyicisi ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="4c2fe-104">(IL hakkında daha fazla bilgi için bkz: [yönetilen yürütme işlemi](../../../docs/standard/managed-execution-process.md).) IL ve gereken meta veriyi içeren elde edilen çalıştırılabilir dosyayı çalıştırarak IL'in beklendiği gibi çalışıp çalışmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-104">(For more information on IL, see [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="4c2fe-105">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4c2fe-106">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-106">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4c2fe-107">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="4c2fe-108">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="4c2fe-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="4c2fe-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c2fe-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

#### <a name="parameters"></a><span data-ttu-id="4c2fe-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c2fe-110">Parameters</span></span>

| <span data-ttu-id="4c2fe-111">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="4c2fe-111">Argument</span></span> | <span data-ttu-id="4c2fe-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c2fe-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="4c2fe-113">.il kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-113">The name of the .il source file.</span></span> <span data-ttu-id="4c2fe-114">Bu dosya meta veri bildirim yönergeleri ve simgesel IL yönergelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="4c2fe-115">Birden çok kaynak dosya bağımsız değişkenleri ile tek bir PE dosyası üretmek için sağlanan *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="4c2fe-116">**Not:** kodunu .il kaynak dosyasında son satırının sonunda boşluk veya satır sonu karakteri sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="4c2fe-117">Seçenek</span><span class="sxs-lookup"><span data-stu-id="4c2fe-117">Option</span></span> | <span data-ttu-id="4c2fe-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c2fe-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="4c2fe-119">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-119">**/32bitpreferred**</span></span>|<span data-ttu-id="4c2fe-120">32 bit tercih edilen bir görüntü (PE32) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="4c2fe-121">**/ alignment:**`integer`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="4c2fe-122">FileAlignment tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="4c2fe-123">Eğer .alignment IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="4c2fe-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-124">**/appcontainer**</span></span>|<span data-ttu-id="4c2fe-125">Üreten bir *.dll* veya *.exe* Windows uygulama kapsayıcısında çıktı olarak çalışan dosya.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="4c2fe-126">**/ARM**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-126">**/arm**</span></span>|<span data-ttu-id="4c2fe-127">Hedef işlemci olarak Gelişmiş RISC Makinesi (ARM) belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="4c2fe-128">Hiçbir görüntü verileri belirtilmezse, varsayılan değer **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="4c2fe-129">**/ temel:**`integer`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-129">**/base:** `integer`</span></span>|<span data-ttu-id="4c2fe-130">ImageBase tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="4c2fe-131">Eğer .imagebase IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="4c2fe-132">**/Clock**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-132">**/clock**</span></span>|<span data-ttu-id="4c2fe-133">Belirtilen .il kaynak dosyası için aşağıdaki derleme sürelerini milisaniye cinsinden ölçer ve raporlar:</span><span class="sxs-lookup"><span data-stu-id="4c2fe-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="4c2fe-134">**Toplam çalışma**: harcanan toplam zamanı izleyin belirli işlemlerini gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="4c2fe-135">**Başlangıç**: yükleme ve dosyayı açma.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="4c2fe-136">**MD yayma**: meta veri yayma.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="4c2fe-137">**Ref Def çözümleme**: dosya tanımlarında başvuruları çözümleme.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="4c2fe-138">**CEE dosyası oluşturma**: bellekte dosya görüntüsü oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="4c2fe-139">**PE dosya yazma**: görüntünün PE dosyaya yazma.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="4c2fe-140">**/ debug**[:**IMPL**&#124; **OPT**]</span><span class="sxs-lookup"><span data-stu-id="4c2fe-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="4c2fe-141">Hata ayıklama bilgisi içerir (yerel değişken ve bağımsız değişken adları ve satır numaraları).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="4c2fe-142">Bir PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="4c2fe-143">**/ debug** JIT iyileştirmesi hiçbir ek değerle devre dışı bırakır ve sıralama noktaları PDB dosyasından kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="4c2fe-144">**IMPL** JIT iyileştirmesi devre dışı bırakır ve örtük sıralama noktaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="4c2fe-145">**OPT** JIT iyileştirmesi sağlar ve örtük sıralama noktaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="4c2fe-146">**/ dll**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-146">**/dll**</span></span>|<span data-ttu-id="4c2fe-147">Üreten bir *.dll* çıktı olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="4c2fe-148">**/ENC:**`file`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-148">**/enc:** `file`</span></span>|<span data-ttu-id="4c2fe-149">Belirtilen kaynak dosyasından Düzenle ve Devam Et deltaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="4c2fe-150">Bu bağımsız değişken yalnızca akademik amaçlıdır ve ticari kullanım için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="4c2fe-151">**/ exe**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-151">**/exe**</span></span>|<span data-ttu-id="4c2fe-152">Çıktı olarak bir yürütülebilir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-152">Produces an executable file as output.</span></span> <span data-ttu-id="4c2fe-153">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-153">This is the default.</span></span>|
|<span data-ttu-id="4c2fe-154">**/ bayraklar:**`integer`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-154">**/flags:** `integer`</span></span>|<span data-ttu-id="4c2fe-155">ImageFlags tarafından belirtilen değere ayarlar `integer` ortak dil çalışma zamanı üst bilgisindeki.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="4c2fe-156">Eğer .corflags IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="4c2fe-157">CorHdr.h, COMIMAGE_FLAGS için geçerli değerler listesi için bkz: *tamsayı*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="4c2fe-158">**/fold**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-158">**/fold**</span></span>|<span data-ttu-id="4c2fe-159">Eşdeğer metot gövdelerini tek bir gövde olarak katlar.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="4c2fe-160">/**hıghentropyva**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-160">/**highentropyva**</span></span>|<span data-ttu-id="4c2fe-161">Yüksek entropili adres alanı düzenini (ASLR) destekleyen bir çıktı çalıştırılabilir dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="4c2fe-162">(İçin varsayılan **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="4c2fe-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="4c2fe-163">**/ içerir:**`includePath`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-163">**/include:** `includePath`</span></span>|<span data-ttu-id="4c2fe-164">Bulunan dosyalar aramak için bir yol ayarlar `#include`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="4c2fe-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-165">**/itanium**</span></span>|<span data-ttu-id="4c2fe-166">Hedef işlemci olarak Intel Itanium belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="4c2fe-167">Hiçbir görüntü verileri belirtilmezse, varsayılan değer **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="4c2fe-168">**/ Anahtar:**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="4c2fe-169">Derlenen `filename` bulunan özel anahtar kullanarak güçlü bir imza ile `keyFile`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="4c2fe-170">**/Key:** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="4c2fe-171">Derlenen `filename` üretilen en güçlü bir imza ile özel anahtarını kullanarak `keySource`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="4c2fe-172">**/ listeleme**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-172">**/listing**</span></span>|<span data-ttu-id="4c2fe-173">Standart çıktıda bir listeleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="4c2fe-174">Eğer bu seçeneği koymazsanız, listeleme dosyası oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="4c2fe-175">Bu parametre .NET Framework 2.0 ve sonrasında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="4c2fe-176">**/MDV:**`versionString`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="4c2fe-177">Meta veri sürümü dizesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="4c2fe-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="4c2fe-179">Meta veri akışı sürümü ayarlar nerede `major` ve `minor` tamsayı olduğunu.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="4c2fe-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-180">**/noautoinherit**</span></span>|<span data-ttu-id="4c2fe-181">Devre dışı bırakır varsayılan devralmadan <xref:System.Object> hiçbir temel sınıf belirtildiğinde.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="4c2fe-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-182">**/nocorstub**</span></span>|<span data-ttu-id="4c2fe-183">CORExeMain taslağının oluşturulmasını bastırır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="4c2fe-184">**/ nologo**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-184">**/nologo**</span></span>|<span data-ttu-id="4c2fe-185">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="4c2fe-186">**/ Çıktı:**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="4c2fe-187">Çıktı dosyası adını ve uzantısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="4c2fe-188">Varsayılan olarak, çıktı dosyası adı ilk kaynak dosyasının adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="4c2fe-189">Varsayılan uzantısı *.exe*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-189">The default extension is *.exe*.</span></span> <span data-ttu-id="4c2fe-190">Belirtirseniz **/dll** seçeneği, varsayılan uzantısıdır *.dll*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="4c2fe-191">**Not:** belirtme **/çıkış**: dosyam.dll ayarlı değil **/dll** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="4c2fe-192">Belirtmezseniz, **/dll**, sonucu adlı bir yürütülebilir dosya olacaktır *dosyam.dll*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="4c2fe-193">**/ optimize**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-193">**/optimize**</span></span>|<span data-ttu-id="4c2fe-194">Uzun yönergeleri kısa olarak iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="4c2fe-195">Örneğin, `br` için `br.s`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="4c2fe-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-196">**/pe64**</span></span>|<span data-ttu-id="4c2fe-197">64 bitlik bir görüntü oluşturur (PE32+).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="4c2fe-198">Hiçbir hedef işlemci belirtilmezse, varsayılan değer `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="4c2fe-199">**/ pdb**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-199">**/pdb**</span></span>|<span data-ttu-id="4c2fe-200">Hata ayıklama bilgisi izlemeyi etkinleştirmeden bir PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="4c2fe-201">**istemci bilgisayarlara**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-201">**/quiet**</span></span>|<span data-ttu-id="4c2fe-202">Sessiz modu belirtir; hiçbir derleme ilerlemesini bildirmez.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="4c2fe-203">**/ Resource:**`file.res`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="4c2fe-204">Belirtilen kaynak dosyası içeren \*elde edilen içinde .res biçimi *.exe* veya *.dll* dosya.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="4c2fe-205">Yalnızca bir .res dosyası ile belirtilebilir **/Resource** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="4c2fe-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="4c2fe-207">NT isteğe bağlı üst bilgisinde alt sistem sürümünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="4c2fe-208">İçin **/appcontainer** ve **/arm** 6.02 en düşük sürüm numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="4c2fe-209">**/ stack:**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="4c2fe-210">NT isteğe bağlı üstbilgi SizeOfStackReserve değeri ayarlar `stackSize`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="4c2fe-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-211">**/stripreloc**</span></span>|<span data-ttu-id="4c2fe-212">Temel yeniden konumlandırmanın gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="4c2fe-213">**/Subsystem:**`integer`</span><span class="sxs-lookup"><span data-stu-id="4c2fe-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="4c2fe-214">Alt sistemi tarafından belirtilen değere ayarlar `integer` NT isteğe bağlı üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="4c2fe-215">Eğer .subsystem IL yönergesi dosyada belirtiliyorsa, bu komut onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="4c2fe-216">Winnt.h, IMAGE_SUBSYSTEM için geçerli değerler listesi için bkz: `integer`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="4c2fe-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-217">**/x64**</span></span>|<span data-ttu-id="4c2fe-218">Hedef işlemci olarak bir 64 bitlik AMD işlemci belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="4c2fe-219">Hiçbir görüntü verileri belirtilmezse, varsayılan değer **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="4c2fe-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="4c2fe-220">**/?**</span></span>|<span data-ttu-id="4c2fe-221">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="4c2fe-222">Tüm seçenekler için *Ilasm.exe* büyük küçük harf duyarsız ve ilk üç harf tarafından tanınan.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="4c2fe-223">Örneğin, **/lis** eşdeğerdir **/listeleme** ve **/res**: myresfile.res eşdeğerdir **/Resource**: myresfile.res. Bağımsız değişkenler belirten seçenekler, seçenek ve bağımsız değişken arasında ayıraç olarak ya iki nokta üst üste (:) ya da eşittir işaretini (=) kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="4c2fe-224">Örneğin, **/çıkış**:*file.ext* eşdeğerdir **/çıkış**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c2fe-225">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c2fe-225">Remarks</span></span>

<span data-ttu-id="4c2fe-226">IL Derleyicisi araç satıcılarına IL oluşturucuları tasarlamaları ve uygulamaları için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="4c2fe-227">Kullanarak *Ilasm.exe*, aracı ve derleyici geliştiricileri yoğunlaşabilirsiniz üzerinde IL ve meta veri oluşturma IL PE dosya biçimi'nde yayma ile ilgili olmadan.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="4c2fe-228">C# ve Visual Basic gibi çalışma zamanı hedef diğer derleyiciler benzer *Ilasm.exe* Ara nesne dosyaları üretmez ve bir PE dosyası oluşturmak için bir bağlama aşama gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="4c2fe-229">IL Derleyicisi, çalışma zamanını hedef alan programlama dillerinin tüm varolan meta veri ve IL özelliklerini ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="4c2fe-230">Böylece, herhangi bir IL derleyici yeterli ifade bu programlama dillerini yazılır ve ile derlenmiş yönetilen kod *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="4c2fe-231">Eğer .il kaynak dosyasının son kod satırında bir boşluk veya satır sonu karakteri yoksa derleme başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="4c2fe-232">Kullanabileceğiniz *Ilasm.exe* kendi yardımcı aracı ile birlikte [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="4c2fe-233">*Ildasm.exe* alır giriş IL kodu içerir ve bir metin dosyası olarak uygun oluşturan bir PE dosyası *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="4c2fe-234">Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="4c2fe-235">Kod derleme ve çıktı çalıştıran sonra *Ildasm.exe*, el ile düzenleyebilirsiniz eksik öznitelikler eklemek için sonuçta elde edilen IL metin dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="4c2fe-236">Sonra bu metin dosyasını çalıştırabilirsiniz *Ilasm.exe* son bir yürütülebilir dosya oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="4c2fe-237">Bu tekniği kullanarak ayrı derleyiciler tarafından üretilen çeşitli PE dosyalarından tek bir PE dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="4c2fe-238">Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="4c2fe-239">Bunu yapmak için kullanımını birleştirilmiş *Ildasm.exe* ve *Ilasm.exe* varsayılan olarak, mümkün olduğunca doğru assembler yazdığınız IL kaynaklarınızı uzun olanlar için kısa Kodlamalar yerine değil (veya başka bir derleyici tarafından yayınlaması).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="4c2fe-240">Kullanım **/ optimize** mümkün olduğunda kısa Kodlamalar yerine seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="4c2fe-241">*Ildasm.exe* yalnızca disk dosyaları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="4c2fe-242">Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="4c2fe-243">IL dilbilgisi hakkında daha fazla bilgi için bkz: asmparse.grammar dosyasında [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c2fe-243">For more information about the grammar of IL, see the asmparse.grammar file in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>

## <a name="version-information"></a><span data-ttu-id="4c2fe-244">Sürüm Bilgileri</span><span class="sxs-lookup"><span data-stu-id="4c2fe-244">Version Information</span></span>

<span data-ttu-id="4c2fe-245">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], aşağıdakine benzer bir kod kullanarak bir arabirim uygulaması için özel bir öznitelik ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c2fe-245">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```
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

<span data-ttu-id="4c2fe-246">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], size rastgele bir sıralama BLOB (ikili büyük nesne) kendi ham ikili gösterim kullanarak aşağıdaki kodda gösterildiği gibi belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c2fe-246">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="4c2fe-247">IL dilbilgisi hakkında daha fazla bilgi için bkz: asmparse.grammar dosyasında [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c2fe-247">For more information about the grammar of IL, see the asmparse.grammar file in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>

## <a name="examples"></a><span data-ttu-id="4c2fe-248">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4c2fe-248">Examples</span></span>

<span data-ttu-id="4c2fe-249">Aşağıdaki komutu IL dosyasını derler *myTestFile.il* ve yürütülebilir üretir *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="4c2fe-250">Aşağıdaki komutu IL dosyasını derler *myTestFile.il* ve üretir *.dll* dosya *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="4c2fe-251">Aşağıdaki komutu IL dosyasını derler *myTestFile.il* ve üretir *.dll* dosya *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="4c2fe-252">Aşağıdaki kod örneğinde "Hello World!" görüntüler oldukça basit bir uygulama gösterir</span><span class="sxs-lookup"><span data-stu-id="4c2fe-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="4c2fe-253">konsola.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-253">to the console.</span></span> <span data-ttu-id="4c2fe-254">Bu kodu derleyin ve ardından [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) aracı bir IL dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-254">You can compile this code and then use the [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

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

<span data-ttu-id="4c2fe-255">Aşağıdaki IL kod örneği önceki C# kod örneğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="4c2fe-256">Bu kod IL derleyici aracını kullanarak bir derlemeye derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="4c2fe-257">"Hello World!" IL hem C# kod örnekleri görüntüle</span><span class="sxs-lookup"><span data-stu-id="4c2fe-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="4c2fe-258">konsola.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-258">to the console.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="4c2fe-259">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-259">See also</span></span>

[<span data-ttu-id="4c2fe-260">Araçları</span><span class="sxs-lookup"><span data-stu-id="4c2fe-260">Tools</span></span>](../../../docs/framework/tools/index.md)  
[<span data-ttu-id="4c2fe-261">*Ildasm.exe* (IL ayrıştırıcı)</span><span class="sxs-lookup"><span data-stu-id="4c2fe-261">*Ildasm.exe* (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
[<span data-ttu-id="4c2fe-262">Yönetilen yürütme işlemi</span><span class="sxs-lookup"><span data-stu-id="4c2fe-262">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)  
[<span data-ttu-id="4c2fe-263">Komut istemleri</span><span class="sxs-lookup"><span data-stu-id="4c2fe-263">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
