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
ms.openlocfilehash: ba8b4cd7f398eee9129d24d25d8fdb754c89a3ee
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653303"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="93d25-103">Peverify.exe (PEVerify aracı)</span><span class="sxs-lookup"><span data-stu-id="93d25-103">Peverify.exe (PEVerify tool)</span></span>

<span data-ttu-id="93d25-104">PEVerify Aracı, Microsoft ara dili (MSIL) oluşturan geliştiricilere (derleyici yazarları ve betik motoru geliştiricileri gibi), MSIL kodunun ve ilişkili meta verilerin tür güvenliği gereksinimlerini karşılayıp karşılamadığını belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="93d25-104">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers and script engine developers) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="93d25-105">Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir.</span><span class="sxs-lookup"><span data-stu-id="93d25-105">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="93d25-106">Böyle bir derleyici kullanıyorsanız, kodunuzun tür güvenliğinin tehlikeye çalışmadığını doğrulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93d25-106">If you're using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="93d25-107">MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93d25-107">You can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="93d25-108">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="93d25-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="93d25-109">Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="93d25-109">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>
  
## <a name="syntax"></a><span data-ttu-id="93d25-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93d25-110">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="93d25-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93d25-111">Parameters</span></span>  
  
|<span data-ttu-id="93d25-112">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="93d25-112">Argument</span></span>|<span data-ttu-id="93d25-113">Description</span><span class="sxs-lookup"><span data-stu-id="93d25-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="93d25-114">*filename*</span><span class="sxs-lookup"><span data-stu-id="93d25-114">*filename*</span></span>|<span data-ttu-id="93d25-115">MSIL ve meta verilerinin denetleneceği taşınabilir yürütülebilir (PE) dosyası.</span><span class="sxs-lookup"><span data-stu-id="93d25-115">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="93d25-116">Seçenek</span><span class="sxs-lookup"><span data-stu-id="93d25-116">Option</span></span>|<span data-ttu-id="93d25-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93d25-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="93d25-118">**/Break =** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="93d25-118">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="93d25-119">*MaxErrorCount* hatalarından sonra doğrulamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="93d25-119">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="93d25-120">Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="93d25-120">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="93d25-121">**/Saat**</span><span class="sxs-lookup"><span data-stu-id="93d25-121">**/clock**</span></span>|<span data-ttu-id="93d25-122">Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:</span><span class="sxs-lookup"><span data-stu-id="93d25-122">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="93d25-123">**MD Val. Cycle**</span><span class="sxs-lookup"><span data-stu-id="93d25-123">**MD Val. cycle**</span></span><br /> <span data-ttu-id="93d25-124">Meta veri doğrulama döngüsü</span><span class="sxs-lookup"><span data-stu-id="93d25-124">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="93d25-125">**MD Val. Pure**</span><span class="sxs-lookup"><span data-stu-id="93d25-125">**MD Val. pure**</span></span><br /> <span data-ttu-id="93d25-126">Meta veri doğrulama safı</span><span class="sxs-lookup"><span data-stu-id="93d25-126">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="93d25-127">**Il ver. Cycle**</span><span class="sxs-lookup"><span data-stu-id="93d25-127">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="93d25-128">Microsoft ara dili (MSIL) doğrulama döngüsü</span><span class="sxs-lookup"><span data-stu-id="93d25-128">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="93d25-129">**Il ver saf**</span><span class="sxs-lookup"><span data-stu-id="93d25-129">**IL Ver pure**</span></span><br /> <span data-ttu-id="93d25-130">MSIL doğrulaması saf</span><span class="sxs-lookup"><span data-stu-id="93d25-130">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="93d25-131">**Md Val. Cycle** ve **Il ver. Cycle** süreleri, gerekli başlatma ve kapatılma yordamlarını gerçekleştirmek için gereken süreyi içerir.</span><span class="sxs-lookup"><span data-stu-id="93d25-131">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="93d25-132">**Md Val. saf** ve **Il ver saf** süreleri yalnızca doğrulamayı veya doğrulamayı gerçekleştirmek için gereken süreyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="93d25-132">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="93d25-133">**/Help**</span><span class="sxs-lookup"><span data-stu-id="93d25-133">**/help**</span></span>|<span data-ttu-id="93d25-134">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93d25-134">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="93d25-135">**/HRESULT**</span><span class="sxs-lookup"><span data-stu-id="93d25-135">**/hresult**</span></span>|<span data-ttu-id="93d25-136">Onaltılık biçimde hata kodlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93d25-136">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="93d25-137">**/Ignore =** *Hex. Code* [, *Hex. Code*]</span><span class="sxs-lookup"><span data-stu-id="93d25-137">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="93d25-138">Belirtilen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="93d25-138">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="93d25-139">**/Ignore = @** *ResponseFile*</span><span class="sxs-lookup"><span data-stu-id="93d25-139">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="93d25-140">Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="93d25-140">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="93d25-141">**/İl**</span><span class="sxs-lookup"><span data-stu-id="93d25-141">**/il**</span></span>|<span data-ttu-id="93d25-142">*Dosya adı* tarafından belirtilen derlemede uygulanan metotlar için MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="93d25-142">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="93d25-143">Araç, **/quiet** seçeneğini belirtmediğiniz müddetçe bulunan her bir sorun için ayrıntılı açıklamalar döndürür.</span><span class="sxs-lookup"><span data-stu-id="93d25-143">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="93d25-144">**/MD**</span><span class="sxs-lookup"><span data-stu-id="93d25-144">**/md**</span></span>|<span data-ttu-id="93d25-145">*Dosya adı* tarafından belirtilen derlemede meta veri doğrulama denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="93d25-145">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="93d25-146">Bu seçenek, dosyanın içindeki tam meta veri yapısını gösterir ve karşılaşılan tüm doğrulama sorunlarını raporlar.</span><span class="sxs-lookup"><span data-stu-id="93d25-146">This option walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="93d25-147">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="93d25-147">**/nologo**</span></span>|<span data-ttu-id="93d25-148">Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="93d25-148">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="93d25-149">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="93d25-149">**/nosymbols**</span></span>|<span data-ttu-id="93d25-150">.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.</span><span class="sxs-lookup"><span data-stu-id="93d25-150">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="93d25-151">**/**</span><span class="sxs-lookup"><span data-stu-id="93d25-151">**/quiet**</span></span>|<span data-ttu-id="93d25-152">Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler.</span><span class="sxs-lookup"><span data-stu-id="93d25-152">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="93d25-153">Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.</span><span class="sxs-lookup"><span data-stu-id="93d25-153">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="93d25-154">Yalnızca saydam yöntemleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="93d25-154">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="93d25-155">**/Unique**</span><span class="sxs-lookup"><span data-stu-id="93d25-155">**/unique**</span></span>|<span data-ttu-id="93d25-156">Yinelenen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="93d25-156">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="93d25-157">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="93d25-157">**/verbose**</span></span>|<span data-ttu-id="93d25-158">.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93d25-158">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="93d25-159">**/?**</span><span class="sxs-lookup"><span data-stu-id="93d25-159">**/?**</span></span>|<span data-ttu-id="93d25-160">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93d25-160">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93d25-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93d25-161">Remarks</span></span>  

 <span data-ttu-id="93d25-162">Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93d25-162">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="93d25-163">Normalde, güvenlik ilkesini güvenilir ancak doğrulanamayan kodun yürütülmesine izin verecek şekilde ayarlayabilseniz de, [doğruıolarak olmayan tür güvenli](../../standard/security/key-security-concepts.md#type-safety-and-security) olmayan kod çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="93d25-163">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="93d25-164">**/Md** veya **/Il** seçeneklerinin hiçbiri belirtilmediyse Peverify.exe her iki denetim türünü de gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="93d25-164">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="93d25-165">Peverify.exe önce **/md** denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="93d25-165">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="93d25-166">Hata yoksa, **/Il** denetimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="93d25-166">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="93d25-167">Hem **/md** hem de **/Il** belirtirseniz, meta verilerde hata olsa bile **/Il** denetimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="93d25-167">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="93d25-168">Bu nedenle, meta veri hatası yoksa, **PEVerify** *Dosya* adı **PEVerify** *dosya adı* **/md** **/Il** ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="93d25-168">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="93d25-169">Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar.</span><span class="sxs-lookup"><span data-stu-id="93d25-169">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="93d25-170">Peverify.exe denetimleri hakkında ayrıntılı bilgi için Windows SDK araçlar Geliştirici Kılavuzu klasöründe "meta veri doğrulama belirtimi" ve "MSIL yönerge kümesi belirtimi" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="93d25-170">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
<span data-ttu-id="93d25-171">.NET Framework sürüm 2,0 veya üzeri `byref` , aşağıdaki MSIL yönergeleri kullanılarak belirtilen doğrulanabilir dönüşler destekler: `dup` , `ldsflda` , `ldflda` , `ldelema` , `call` ve `unbox` .</span><span class="sxs-lookup"><span data-stu-id="93d25-171">.NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call`, and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="93d25-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="93d25-172">Examples</span></span>  

 <span data-ttu-id="93d25-173">Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="93d25-173">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="93d25-174">Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93d25-174">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="93d25-175">Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="93d25-175">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="93d25-176">Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93d25-176">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="93d25-177">Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93d25-177">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="93d25-178">Aşağıdaki komut, derlemede uygulanan yöntemler için meta veri doğrulama denetimleri ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="93d25-178">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="93d25-179">Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur.</span><span class="sxs-lookup"><span data-stu-id="93d25-179">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="93d25-180">Araç belirtilen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="93d25-180">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="93d25-181">Aşağıdaki komut, yukarıdaki önceki örnekle aynı sonucu üretir, ancak yanıt dosyasında yoksayılacak hata kodlarını belirtir `ignoreErrors.rsp` .</span><span class="sxs-lookup"><span data-stu-id="93d25-181">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="93d25-182">Yanıt dosyası hata kodlarının virgülle ayrılmış listesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="93d25-182">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="93d25-183">Alternatif olarak, yanıt dosyası her satırda bir hata kodu olacak şekilde de biçimlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="93d25-183">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="93d25-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93d25-184">See also</span></span>

- [<span data-ttu-id="93d25-185">Araçlar</span><span class="sxs-lookup"><span data-stu-id="93d25-185">Tools</span></span>](index.md)
- [<span data-ttu-id="93d25-186">Verifili Type-Safe kodu yazma</span><span class="sxs-lookup"><span data-stu-id="93d25-186">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="93d25-187">Tür güvenliği ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="93d25-187">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="93d25-188">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="93d25-188">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
