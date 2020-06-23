---
title: Peverify.exe (PEVerify Aracı)
description: Microsoft ara dili (MSIL) kodu & meta verilerin .NET 'teki tür güvenlik standartlarını karşılayıp karşılamadığını belirlemesine yardımcı olması için Peverify.exe (taşınabilir yürütülebilir dosya doğrulaması) kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
ms.openlocfilehash: d7962bc91d89d3bd183697011aed1afca0fb0fc1
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904214"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="65f26-103">Peverify.exe (PEVerify Aracı)</span><span class="sxs-lookup"><span data-stu-id="65f26-103">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="65f26-104">PEVerify aracı, Microsoft ara dili (MSIL) (derleyici yazıcıları, betik motor geliştiricileri vb.) oluşturan geliştiricilere, MSIL kodlarının ve ilişkili meta verilerinin güvenlik koşullarına uygun olup olmadığını belirlemede yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="65f26-104">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="65f26-105">Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir.</span><span class="sxs-lookup"><span data-stu-id="65f26-105">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="65f26-106">Bir geliştirici olarak, bilgisayar kullanıyorsanız, kodunuzun tür güvenliğini tehlikeye atmadığınızı doğrulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65f26-106">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="65f26-107">Bu durumda, MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65f26-107">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="65f26-108">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="65f26-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="65f26-109">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="65f26-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="65f26-110">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="65f26-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="65f26-111">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="65f26-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f26-112">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="65f26-112">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="65f26-113">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65f26-113">Parameters</span></span>  
  
|<span data-ttu-id="65f26-114">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="65f26-114">Argument</span></span>|<span data-ttu-id="65f26-115">Description</span><span class="sxs-lookup"><span data-stu-id="65f26-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="65f26-116">*filename*</span><span class="sxs-lookup"><span data-stu-id="65f26-116">*filename*</span></span>|<span data-ttu-id="65f26-117">MSIL ve meta verilerinin denetleneceği taşınabilir yürütülebilir (PE) dosyası.</span><span class="sxs-lookup"><span data-stu-id="65f26-117">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="65f26-118">Seçenek</span><span class="sxs-lookup"><span data-stu-id="65f26-118">Option</span></span>|<span data-ttu-id="65f26-119">Description</span><span class="sxs-lookup"><span data-stu-id="65f26-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="65f26-120">**/Break =** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="65f26-120">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="65f26-121">*MaxErrorCount* hatalarından sonra doğrulamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="65f26-121">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="65f26-122">Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="65f26-122">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="65f26-123">**/Saat**</span><span class="sxs-lookup"><span data-stu-id="65f26-123">**/clock**</span></span>|<span data-ttu-id="65f26-124">Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:</span><span class="sxs-lookup"><span data-stu-id="65f26-124">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="65f26-125">**MD Val. Cycle**</span><span class="sxs-lookup"><span data-stu-id="65f26-125">**MD Val. cycle**</span></span><br /> <span data-ttu-id="65f26-126">Meta veri doğrulama döngüsü</span><span class="sxs-lookup"><span data-stu-id="65f26-126">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="65f26-127">**MD Val. Pure**</span><span class="sxs-lookup"><span data-stu-id="65f26-127">**MD Val. pure**</span></span><br /> <span data-ttu-id="65f26-128">Meta veri doğrulama safı</span><span class="sxs-lookup"><span data-stu-id="65f26-128">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="65f26-129">**Il ver. Cycle**</span><span class="sxs-lookup"><span data-stu-id="65f26-129">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="65f26-130">Microsoft ara dili (MSIL) doğrulama döngüsü</span><span class="sxs-lookup"><span data-stu-id="65f26-130">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="65f26-131">**Il ver saf**</span><span class="sxs-lookup"><span data-stu-id="65f26-131">**IL Ver pure**</span></span><br /> <span data-ttu-id="65f26-132">MSIL doğrulaması saf</span><span class="sxs-lookup"><span data-stu-id="65f26-132">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="65f26-133">**Md Val. Cycle** ve **Il ver. Cycle** süreleri, gerekli başlatma ve kapatılma yordamlarını gerçekleştirmek için gereken süreyi içerir.</span><span class="sxs-lookup"><span data-stu-id="65f26-133">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="65f26-134">**Md Val. saf** ve **Il ver saf** süreleri yalnızca doğrulamayı veya doğrulamayı gerçekleştirmek için gereken süreyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="65f26-134">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="65f26-135">**/Help**</span><span class="sxs-lookup"><span data-stu-id="65f26-135">**/help**</span></span>|<span data-ttu-id="65f26-136">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65f26-136">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="65f26-137">**/HRESULT**</span><span class="sxs-lookup"><span data-stu-id="65f26-137">**/hresult**</span></span>|<span data-ttu-id="65f26-138">Onaltılık biçimde hata kodlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65f26-138">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="65f26-139">**/Ignore =** *Hex. Code* [, *Hex. Code*]</span><span class="sxs-lookup"><span data-stu-id="65f26-139">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="65f26-140">Belirtilen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="65f26-140">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="65f26-141">**/Ignore = @** *ResponseFile*</span><span class="sxs-lookup"><span data-stu-id="65f26-141">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="65f26-142">Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="65f26-142">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="65f26-143">**/İl**</span><span class="sxs-lookup"><span data-stu-id="65f26-143">**/il**</span></span>|<span data-ttu-id="65f26-144">*Dosya adı*tarafından belirtilen derlemede uygulanan metotlar için MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="65f26-144">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="65f26-145">Araç, **/quiet** seçeneğini belirtmediğiniz müddetçe bulunan her bir sorun için ayrıntılı açıklamalar döndürür.</span><span class="sxs-lookup"><span data-stu-id="65f26-145">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="65f26-146">**/MD**</span><span class="sxs-lookup"><span data-stu-id="65f26-146">**/md**</span></span>|<span data-ttu-id="65f26-147">*Dosya adı*tarafından belirtilen derlemede meta veri doğrulama denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="65f26-147">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="65f26-148">Bu, dosya içindeki tüm meta veri yapısını ölçer ve karşılaşılan tüm doğrulama sorunlarını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="65f26-148">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="65f26-149">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="65f26-149">**/nologo**</span></span>|<span data-ttu-id="65f26-150">Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="65f26-150">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="65f26-151">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="65f26-151">**/nosymbols**</span></span>|<span data-ttu-id="65f26-152">.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.</span><span class="sxs-lookup"><span data-stu-id="65f26-152">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="65f26-153">**/**</span><span class="sxs-lookup"><span data-stu-id="65f26-153">**/quiet**</span></span>|<span data-ttu-id="65f26-154">Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler.</span><span class="sxs-lookup"><span data-stu-id="65f26-154">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="65f26-155">Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.</span><span class="sxs-lookup"><span data-stu-id="65f26-155">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="65f26-156">Yalnızca saydam yöntemleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="65f26-156">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="65f26-157">**/Unique**</span><span class="sxs-lookup"><span data-stu-id="65f26-157">**/unique**</span></span>|<span data-ttu-id="65f26-158">Yinelenen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="65f26-158">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="65f26-159">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="65f26-159">**/verbose**</span></span>|<span data-ttu-id="65f26-160">.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65f26-160">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="65f26-161">**/?**</span><span class="sxs-lookup"><span data-stu-id="65f26-161">**/?**</span></span>|<span data-ttu-id="65f26-162">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65f26-162">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65f26-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65f26-163">Remarks</span></span>  
 <span data-ttu-id="65f26-164">Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="65f26-164">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="65f26-165">Normalde, güvenlik ilkesini güvenilir ancak doğrulanamayan kodun yürütülmesine izin verecek şekilde ayarlayabilseniz de, [doğruıolarak olmayan tür güvenli](../../standard/security/key-security-concepts.md#type-safety-and-security) olmayan kod çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="65f26-165">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="65f26-166">**/Md** veya **/Il** seçeneklerinin hiçbiri belirtilmediyse Peverify.exe her iki denetim türünü de gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="65f26-166">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="65f26-167">Peverify.exe önce **/md** denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="65f26-167">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="65f26-168">Hata yoksa, **/Il** denetimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="65f26-168">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="65f26-169">Hem **/md** hem de **/Il**belirtirseniz, meta verilerde hata olsa bile **/Il** denetimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="65f26-169">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="65f26-170">Bu nedenle, meta veri hatası yoksa, **PEVerify** *Dosya* adı **PEVerify** *dosya adı* **/md** **/Il**ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="65f26-170">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="65f26-171">Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar.</span><span class="sxs-lookup"><span data-stu-id="65f26-171">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="65f26-172">Peverify.exe denetimleri hakkında ayrıntılı bilgi için Windows SDK araçlar Geliştirici Kılavuzu klasöründe "meta veri doğrulama belirtimi" ve "MSIL yönerge kümesi belirtimi" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="65f26-172">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
 <span data-ttu-id="65f26-173">.NET Framework sürüm 2,0 veya sonraki bir sürümün `byref` aşağıdaki MSIL yönergeleri kullanılarak belirtilen doğrulanabilir dönüşler desteklediğini unutmayın: `dup` , `ldsflda` , `ldflda` , `ldelema` `call` ve `unbox` .</span><span class="sxs-lookup"><span data-stu-id="65f26-173">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="65f26-174">Örnekler</span><span class="sxs-lookup"><span data-stu-id="65f26-174">Examples</span></span>  
 <span data-ttu-id="65f26-175">Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="65f26-175">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="65f26-176">Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65f26-176">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="65f26-177">Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="65f26-177">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="65f26-178">Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65f26-178">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="65f26-179">Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65f26-179">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="65f26-180">Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="65f26-180">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="65f26-181">Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur.</span><span class="sxs-lookup"><span data-stu-id="65f26-181">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="65f26-182">Araç belirtilen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="65f26-182">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="65f26-183">Aşağıdaki komut, yukarıdaki önceki örnekle aynı sonucu üretir, ancak yanıt dosyasında yoksayılacak hata kodlarını belirtir `ignoreErrors.rsp` .</span><span class="sxs-lookup"><span data-stu-id="65f26-183">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="65f26-184">Yanıt dosyası hata kodlarının virgülle ayrılmış listesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="65f26-184">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="65f26-185">Alternatif olarak, yanıt dosyası her satırda bir hata kodu olacak şekilde de biçimlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="65f26-185">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="65f26-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65f26-186">See also</span></span>

- [<span data-ttu-id="65f26-187">Araçlar</span><span class="sxs-lookup"><span data-stu-id="65f26-187">Tools</span></span>](index.md)
- [<span data-ttu-id="65f26-188">Verifi, türü güvenli kod yazma</span><span class="sxs-lookup"><span data-stu-id="65f26-188">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="65f26-189">Tür güvenliği ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="65f26-189">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="65f26-190">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="65f26-190">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
