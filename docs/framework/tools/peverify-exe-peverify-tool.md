---
title: Peverify.exe (PEVerify Aracı)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd1f7679a3c2ecc234724e6417c5b12a78ff7ddc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598297"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="693dc-102">Peverify.exe (PEVerify Aracı)</span><span class="sxs-lookup"><span data-stu-id="693dc-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="693dc-103">PEVerify aracı, Microsoft ara dili (MSIL) (derleyici yazıcıları, betik motor geliştiricileri vb.) oluşturan geliştiricilere, MSIL kodlarının ve ilişkili meta verilerinin güvenlik koşullarına uygun olup olmadığını belirlemede yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="693dc-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="693dc-104">Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir.</span><span class="sxs-lookup"><span data-stu-id="693dc-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="693dc-105">Bir geliştirici olarak, bilgisayar kullanıyorsanız, kodunuzun tür güvenliğini tehlikeye atmadığınızı doğrulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="693dc-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="693dc-106">Bu durumda, MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="693dc-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="693dc-107">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="693dc-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="693dc-108">Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="693dc-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="693dc-109">Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="693dc-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="693dc-110">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="693dc-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="693dc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="693dc-111">Syntax</span></span>  
  
```  
peverify filename [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="693dc-112">Parametreler</span><span class="sxs-lookup"><span data-stu-id="693dc-112">Parameters</span></span>  
  
|<span data-ttu-id="693dc-113">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="693dc-113">Argument</span></span>|<span data-ttu-id="693dc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="693dc-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="693dc-115">*Dosya adı*</span><span class="sxs-lookup"><span data-stu-id="693dc-115">*filename*</span></span>|<span data-ttu-id="693dc-116">MSIL ve meta verilerinin denetleneceği taşınabilir yürütülebilir (PE) dosyası.</span><span class="sxs-lookup"><span data-stu-id="693dc-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="693dc-117">Seçenek</span><span class="sxs-lookup"><span data-stu-id="693dc-117">Option</span></span>|<span data-ttu-id="693dc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="693dc-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="693dc-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="693dc-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="693dc-120">Doğrulamadan sonra iptal *maxErrorCount* hataları.</span><span class="sxs-lookup"><span data-stu-id="693dc-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="693dc-121">Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="693dc-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="693dc-122">**/Clock**</span><span class="sxs-lookup"><span data-stu-id="693dc-122">**/clock**</span></span>|<span data-ttu-id="693dc-123">Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:</span><span class="sxs-lookup"><span data-stu-id="693dc-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="693dc-124">**MD Val. döngüsü**</span><span class="sxs-lookup"><span data-stu-id="693dc-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="693dc-125">Meta veri doğrulama döngüsü</span><span class="sxs-lookup"><span data-stu-id="693dc-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="693dc-126">**MD Val. saf**</span><span class="sxs-lookup"><span data-stu-id="693dc-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="693dc-127">Meta veri doğrulama safı</span><span class="sxs-lookup"><span data-stu-id="693dc-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="693dc-128">**IL Ver. döngüsü**</span><span class="sxs-lookup"><span data-stu-id="693dc-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="693dc-129">Microsoft ara dili (MSIL) doğrulama döngüsü</span><span class="sxs-lookup"><span data-stu-id="693dc-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="693dc-130">**IL Ver saf**</span><span class="sxs-lookup"><span data-stu-id="693dc-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="693dc-131">MSIL doğrulaması saf</span><span class="sxs-lookup"><span data-stu-id="693dc-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="693dc-132">**MD Val. döngüsü** ve **IL Ver. döngüsü** süreleri, gerekli başlatma ve kapatma yordamları gerçekleştirmek için gereken süreyi içerir.</span><span class="sxs-lookup"><span data-stu-id="693dc-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="693dc-133">**MD Val. saf** ve **IL Ver saf** kez ve yalnızca doğrulamayı gerçekleştirmek için gereken süreyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="693dc-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="693dc-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="693dc-134">**/help**</span></span>|<span data-ttu-id="693dc-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="693dc-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="693dc-136">**/HRESULT**</span><span class="sxs-lookup"><span data-stu-id="693dc-136">**/hresult**</span></span>|<span data-ttu-id="693dc-137">Onaltılık biçimde hata kodlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="693dc-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="693dc-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="693dc-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="693dc-139">Belirtilen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="693dc-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="693dc-140">**Yoksay = @** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="693dc-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="693dc-141">Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="693dc-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="693dc-142">**/İl**</span><span class="sxs-lookup"><span data-stu-id="693dc-142">**/il**</span></span>|<span data-ttu-id="693dc-143">Tarafından belirtilen derlemede uygulanmış yöntemler için MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir *filename*.</span><span class="sxs-lookup"><span data-stu-id="693dc-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="693dc-144">Araç, belirtmediğiniz sürece bulunan her sorun için ayrıntılı açıklamalar döndürür **/quiet** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="693dc-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="693dc-145">**/ MD**</span><span class="sxs-lookup"><span data-stu-id="693dc-145">**/md**</span></span>|<span data-ttu-id="693dc-146">Tarafından belirtilen derleme meta veri doğrulama denetimleri gerçekleştirir *filename*.</span><span class="sxs-lookup"><span data-stu-id="693dc-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="693dc-147">Bu, dosya içindeki tüm meta veri yapısını ölçer ve karşılaşılan tüm doğrulama sorunlarını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="693dc-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="693dc-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="693dc-148">**/nologo**</span></span>|<span data-ttu-id="693dc-149">Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="693dc-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="693dc-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="693dc-150">**/nosymbols**</span></span>|<span data-ttu-id="693dc-151">.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.</span><span class="sxs-lookup"><span data-stu-id="693dc-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="693dc-152">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="693dc-152">**/quiet**</span></span>|<span data-ttu-id="693dc-153">Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler.</span><span class="sxs-lookup"><span data-stu-id="693dc-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="693dc-154">Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.</span><span class="sxs-lookup"><span data-stu-id="693dc-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="693dc-155">Yalnızca saydam yöntemleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="693dc-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="693dc-156">**/ unique**</span><span class="sxs-lookup"><span data-stu-id="693dc-156">**/unique**</span></span>|<span data-ttu-id="693dc-157">Yinelenen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="693dc-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="693dc-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="693dc-158">**/verbose**</span></span>|<span data-ttu-id="693dc-159">.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="693dc-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="693dc-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="693dc-160">**/?**</span></span>|<span data-ttu-id="693dc-161">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="693dc-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="693dc-162">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="693dc-162">Remarks</span></span>  
 <span data-ttu-id="693dc-163">Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="693dc-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="693dc-164">Normalde olmayan kodu [doğrulanabilir şekilde tür güvenli](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) çalıştıramazsınız karşın, güvenilir, ancak doğrulanamaz kod yürütülmesine izin veren güvenlik ilkesini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="693dc-164">Normally, code that is not [verifiably type safe](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="693dc-165">Kullanılmazsa **/md** ya da **/il** seçenekler belirtilir, Peverify.exe her iki tür denetimi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="693dc-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="693dc-166">Peverify.exe gerçekleştirir **/md** ilk denetler.</span><span class="sxs-lookup"><span data-stu-id="693dc-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="693dc-167">Herhangi bir hata varsa **/il** denetimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="693dc-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="693dc-168">Her ikisini de belirtirseniz **/md** ve **/il**, **/il** meta verilerde hatalar olsa denetimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="693dc-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="693dc-169">Bu nedenle, herhangi bir meta veri hatası yoksa **peverify** *filename* eşdeğerdir **peverify** *filename* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="693dc-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="693dc-170">Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar.</span><span class="sxs-lookup"><span data-stu-id="693dc-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="693dc-171">Peverify.exe gerçekleştirdiği denetimler hakkında ayrıntılı bilgi için bkz. "Meta veri doğrulama belirtimi" ve "MSIL yönergesi belirtimi" araçları Kılavuzu klasöründe [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="693dc-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="693dc-172">.NET Framework sürüm 2.0 veya sonraki doğrulanabilir desteklediğini unutmayın `byref` şu MSIL yönergeleri kullanılarak belirtilen döndürür: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` ve `unbox`.</span><span class="sxs-lookup"><span data-stu-id="693dc-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="693dc-173">Örnekler</span><span class="sxs-lookup"><span data-stu-id="693dc-173">Examples</span></span>  
 <span data-ttu-id="693dc-174">Aşağıdaki komutu derlemesinde uygulanmış yöntemler için meta veri doğrulama denetimlerini ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="693dc-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="693dc-175">Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="693dc-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="693dc-176">Aşağıdaki komutu derlemesinde uygulanmış yöntemler için meta veri doğrulama denetimlerini ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="693dc-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="693dc-177">Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="693dc-177">The tool displays the time required to perform these checks.</span></span>  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="693dc-178">Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="693dc-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="693dc-179">Aşağıdaki komutu derlemesinde uygulanmış yöntemler için meta veri doğrulama denetimlerini ve MSIL tür güvenliği doğrulama denetimlerini gerçekleştirir `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="693dc-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="693dc-180">Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur.</span><span class="sxs-lookup"><span data-stu-id="693dc-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="693dc-181">Araç belirtilen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="693dc-181">The tool also ignores the specified error codes.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="693dc-182">Aşağıdaki komut Yukarıdaki örnekteki aynı sonucu üretir, ancak yanıt dosyasında yok sayılacak hata kodlarını belirtir `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="693dc-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="693dc-183">Yanıt dosyası hata kodlarının virgülle ayrılmış listesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="693dc-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```  
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="693dc-184">Alternatif olarak, yanıt dosyası her satırda bir hata kodu olacak şekilde de biçimlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="693dc-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="693dc-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="693dc-185">See also</span></span>
- [<span data-ttu-id="693dc-186">Araçlar</span><span class="sxs-lookup"><span data-stu-id="693dc-186">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="693dc-187">Doğrulanabilir şekilde tür kullanımı uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="693dc-187">Writing Verifiably Type-Safe Code</span></span>](../../../docs/framework/misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="693dc-188">Tür güvenliği ve Emniyeti</span><span class="sxs-lookup"><span data-stu-id="693dc-188">Type Safety and Security</span></span>](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="693dc-189">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="693dc-189">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
