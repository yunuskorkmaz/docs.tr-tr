---
title: "Peverify.exe (PEVerify Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5acb6da7c68f899daa4144e897e9ec31fcfa868a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="0e5b5-102">Peverify.exe (PEVerify Aracı)</span><span class="sxs-lookup"><span data-stu-id="0e5b5-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="0e5b5-103">PEVerify aracı, Microsoft ara dili (MSIL) (derleyici yazıcıları, betik motor geliştiricileri vb.) oluşturan geliştiricilere, MSIL kodlarının ve ilişkili meta verilerinin güvenlik koşullarına uygun olup olmadığını belirlemede yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="0e5b5-104">Bazı derleyiciler yalnızca belirli dil yapılarını kullanmaktan kaçındığınızda doğrulanabilir şekilde tür kullanımı uyumlu kod üretir.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="0e5b5-105">Bir geliştirici olarak, bilgisayar kullanıyorsanız, kodunuzun tür güvenliğini tehlikeye atmadığınızı doğrulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="0e5b5-106">Bu durumda, MSIL ve meta verileri denetlemek için dosyalarınızda PEVerify aracını çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="0e5b5-107">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="0e5b5-108">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="0e5b5-109">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0e5b5-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="0e5b5-110">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="0e5b5-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e5b5-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e5b5-111">Syntax</span></span>  
  
```  
peverify filename [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e5b5-112">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e5b5-112">Parameters</span></span>  
  
|<span data-ttu-id="0e5b5-113">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="0e5b5-113">Argument</span></span>|<span data-ttu-id="0e5b5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e5b5-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="0e5b5-115">*Dosya adı*</span><span class="sxs-lookup"><span data-stu-id="0e5b5-115">*filename*</span></span>|<span data-ttu-id="0e5b5-116">MSIL ve meta verilerinin denetleneceği taşınabilir yürütülebilir (PE) dosyası.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="0e5b5-117">Seçenek</span><span class="sxs-lookup"><span data-stu-id="0e5b5-117">Option</span></span>|<span data-ttu-id="0e5b5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e5b5-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0e5b5-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="0e5b5-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="0e5b5-120">İptalleri doğrulamadan sonra *maxErrorCount* hataları.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="0e5b5-121">Bu parametre .NET Framework sürüm 2.0 ve sonrasında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="0e5b5-122">**/Clock**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-122">**/clock**</span></span>|<span data-ttu-id="0e5b5-123">Milisaniye olarak aşağıdaki doğrulama zamanlarını ölçer ve bildirir:</span><span class="sxs-lookup"><span data-stu-id="0e5b5-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="0e5b5-124">**MD elden döngüsü**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="0e5b5-125">Meta veri doğrulama döngüsü</span><span class="sxs-lookup"><span data-stu-id="0e5b5-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="0e5b5-126">**MD elden saf**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="0e5b5-127">Meta veri doğrulama safı</span><span class="sxs-lookup"><span data-stu-id="0e5b5-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="0e5b5-128">**IL sürüm döngüsü**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="0e5b5-129">Microsoft ara dili (MSIL) doğrulama döngüsü</span><span class="sxs-lookup"><span data-stu-id="0e5b5-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="0e5b5-130">**Saf IL Ver**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="0e5b5-131">MSIL doğrulaması saf</span><span class="sxs-lookup"><span data-stu-id="0e5b5-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="0e5b5-132">**MD elden döngüsü** ve **IL sürüm döngüsü** kez dahil etmeniz gereken başlatma ve kapatma işlemleri gerçekleştirmek için gereken süre.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="0e5b5-133">**MD elden saf** ve **IL Ver saf** saatler doğrulama veya yalnızca doğrulama gerçekleştirmek için gereken süreyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="0e5b5-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-134">**/help**</span></span>|<span data-ttu-id="0e5b5-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="0e5b5-136">**/HRESULT**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-136">**/hresult**</span></span>|<span data-ttu-id="0e5b5-137">Onaltılık biçimde hata kodlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="0e5b5-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="0e5b5-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="0e5b5-139">Belirtilen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="0e5b5-140">**Yoksay = @** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="0e5b5-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="0e5b5-141">Belirtilen yanıt dosyasında listelenen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="0e5b5-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-142">**/il**</span></span>|<span data-ttu-id="0e5b5-143">Belirtilen derleme uygulanan yöntemleri için MSIL tür güvenlik doğrulama denetimleri gerçekleştirir *filename*.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="0e5b5-144">Belirtmediğiniz sürece bulunan her sorun için ayrıntılı açıklamalar aracı döndürür **/quiet** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="0e5b5-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-145">**/md**</span></span>|<span data-ttu-id="0e5b5-146">Tarafından belirtilen derlemedeki meta veri doğrulama denetimlerini gerçekleştiren *filename*.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="0e5b5-147">Bu, dosya içindeki tüm meta veri yapısını ölçer ve karşılaşılan tüm doğrulama sorunlarını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="0e5b5-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-148">**/nologo**</span></span>|<span data-ttu-id="0e5b5-149">Ürün sürümü ve telif hakkı bilgilerinin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="0e5b5-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-150">**/nosymbols**</span></span>|<span data-ttu-id="0e5b5-151">.NET Framework sürüm 2.0'da, geriye doğru uyumluluk için satır numaralarını gizler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="0e5b5-152">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-152">**/quiet**</span></span>|<span data-ttu-id="0e5b5-153">Sessiz mod kullanılacağını belirtir; doğrulama sorunu raporlarının çıkışını önler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="0e5b5-154">Peverify.exe dosyanın tür kullanımı uyumlu olup olmadığını bildirmeye devam eder, ancak tür güvenliği doğrulamasını önleyen sorunlar hakkında bilgi vermez.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="0e5b5-155">Yalnızca saydam yöntemleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="0e5b5-156">**/ benzersiz**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-156">**/unique**</span></span>|<span data-ttu-id="0e5b5-157">Yinelenen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="0e5b5-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-158">**/verbose**</span></span>|<span data-ttu-id="0e5b5-159">.NET Framework sürüm 2. 0'da, MSIL doğrulama iletilerinde ek bilgiler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="0e5b5-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="0e5b5-160">**/?**</span></span>|<span data-ttu-id="0e5b5-161">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e5b5-162">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e5b5-162">Remarks</span></span>  
 <span data-ttu-id="0e5b5-163">Ortak dil çalışma zamanı, güvenlik ve yalıtım mekanizmalarını zorlamaya yardımcı olmak için uygulama kodunun tür kullanımı uyumlu yürütülmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="0e5b5-164">Normalde, kodları [doğrulanabilir şekilde tür uyumlu](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) çalışamaz, güvenilen ancak doğrulanamaz kod yürütmeyi izin veren güvenlik ilkesini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-164">Normally, code that is not [verifiably type safe](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="0e5b5-165">Ne **/md** ya da **/il** seçenekleri belirtilirse, Peverify.exe her iki tür denetimler gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="0e5b5-166">Peverify.exe gerçekleştirir **/md** ilk denetler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="0e5b5-167">Hiçbir hatalar varsa **/il** denetimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="0e5b5-168">Her ikisini de belirtirseniz, **/md** ve **/il**, **/il** meta verilerde hatalar olsa denetimleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="0e5b5-169">Bu nedenle, hiçbir meta veri hatası yoksa **peverify** *filename* eşdeğerdir **peverify** *filename* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="0e5b5-170">Peverify.exe, veri akışı analizine ve geçerli meta veriye ilişkin birkaç yüz kuralı içeren bir listeye göre kapsamlı MSIL doğrulama denetimleri yapar.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="0e5b5-171">"Meta veri doğrulama belirtimi" ve "MSIL yönerge kümesi belirtimi" araçları Geliştirici Kılavuzu klasöründe Peverify.exe gerçekleştirir denetimleri ayrıntılı bilgi için bkz: [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e5b5-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="0e5b5-172">.NET Framework sürüm 2.0 veya üstü doğrulanabilen desteklediğini unutmayın `byref` aşağıdaki MSIL yönergeleri kullanarak belirtilen döndürür: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` ve `unbox`.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0e5b5-173">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0e5b5-173">Examples</span></span>  
 <span data-ttu-id="0e5b5-174">Aşağıdaki komutu derlemede uygulanan yöntemleri için meta veri doğrulama denetimlerini ve MSIL tür güvenlik doğrulama denetimleri gerçekleştirir `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="0e5b5-175">Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="0e5b5-176">Aşağıdaki komutu derlemede uygulanan yöntemleri için meta veri doğrulama denetimlerini ve MSIL tür güvenlik doğrulama denetimleri gerçekleştirir `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="0e5b5-177">Araç bu denetimleri gerçekleştirmek için gereken süreyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-177">The tool displays the time required to perform these checks.</span></span>  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="0e5b5-178">Yukarıdaki isteğin başarıyla tamamlanmasından sonra Peverify.exe aşağıdaki iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="0e5b5-179">Aşağıdaki komutu derlemede uygulanan yöntemleri için meta veri doğrulama denetimlerini ve MSIL tür güvenlik doğrulama denetimleri gerçekleştirir `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="0e5b5-180">Ancak en fazla hata sayısı olan 100'e ulaştığında Peverify.exe durur.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="0e5b5-181">Araç belirtilen hata kodlarını dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-181">The tool also ignores the specified error codes.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="0e5b5-182">Aşağıdaki komut yukarıdaki önceki örnekteki gibi aynı sonucu verir, ancak yanıt dosyasında yoksaymak için hata kodlarını belirtir `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="0e5b5-183">Yanıt dosyası hata kodlarının virgülle ayrılmış listesini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```  
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="0e5b5-184">Alternatif olarak, yanıt dosyası her satırda bir hata kodu olacak şekilde de biçimlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e5b5-185">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e5b5-185">See Also</span></span>  
 [<span data-ttu-id="0e5b5-186">Araçlar</span><span class="sxs-lookup"><span data-stu-id="0e5b5-186">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="0e5b5-187">NIB: Doğrulanabilir şekilde tür kullanımı uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="0e5b5-187">NIB: Writing Verifiably Type-Safe Code</span></span>](http://msdn.microsoft.com/library/d18f10ef-3b48-4f47-8726-96714021547b)  
 [<span data-ttu-id="0e5b5-188">Tür güvenliği ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="0e5b5-188">Type Safety and Security</span></span>](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [<span data-ttu-id="0e5b5-189">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="0e5b5-189">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
