---
title: "Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd7f50d591232feda0259ecefdb5b9e39514ccb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="794f2-102">Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="794f2-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="794f2-103">.NET Hizmetleri Yükleme aracı aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="794f2-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
-   <span data-ttu-id="794f2-104">Bir derlemeyi yükler ve kaydeder.</span><span class="sxs-lookup"><span data-stu-id="794f2-104">Loads and registers an assembly.</span></span>  
  
-   <span data-ttu-id="794f2-105">Bir tür kitaplığı üretir, kaydeder ve belirtilen bir COM+ uygulamasına yükler.</span><span class="sxs-lookup"><span data-stu-id="794f2-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
-   <span data-ttu-id="794f2-106">Sınıfınıza program aracılığıyla eklediğiniz hizmetleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="794f2-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="794f2-107">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="794f2-107">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="794f2-108">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="794f2-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="794f2-109">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="794f2-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="794f2-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="794f2-110">Syntax</span></span>  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
#### <a name="parameters"></a><span data-ttu-id="794f2-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="794f2-111">Parameters</span></span>  
  
|<span data-ttu-id="794f2-112">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="794f2-112">Argument</span></span>|<span data-ttu-id="794f2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="794f2-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="794f2-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="794f2-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="794f2-115">Kaynak derleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="794f2-115">The source assembly file.</span></span> <span data-ttu-id="794f2-116">Derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="794f2-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="794f2-117">Daha fazla bilgi için bkz: [bir derlemeyi tanımlayıcı adla imzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="794f2-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="794f2-118">Seçenek</span><span class="sxs-lookup"><span data-stu-id="794f2-118">Option</span></span>|<span data-ttu-id="794f2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="794f2-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="794f2-120">**/appdir:** *yolu*</span><span class="sxs-lookup"><span data-stu-id="794f2-120">**/appdir:** *path*</span></span>|<span data-ttu-id="794f2-121">Uygulamanın kök dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="794f2-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="794f2-122">**Appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="794f2-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="794f2-123">Bulunacak veya oluşturulacak COM+ uygulamasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="794f2-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="794f2-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="794f2-124">**/c**</span></span>|<span data-ttu-id="794f2-125">Hedef uygulamayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="794f2-125">Creates the target application.</span></span>|  
|<span data-ttu-id="794f2-126">**/ componly**</span><span class="sxs-lookup"><span data-stu-id="794f2-126">**/componly**</span></span>|<span data-ttu-id="794f2-127">Yalnızca bileşenleri yapılandırır; yöntemleri ve arabirimleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="794f2-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="794f2-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="794f2-128">**/exapp**</span></span>|<span data-ttu-id="794f2-129">Varolan bir uygulamayı beklemek üzere aracı belirtir.</span><span class="sxs-lookup"><span data-stu-id="794f2-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="794f2-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="794f2-130">**/extlb**</span></span>|<span data-ttu-id="794f2-131">Varolan bir tür kitaplığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="794f2-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="794f2-132">**/FC**</span><span class="sxs-lookup"><span data-stu-id="794f2-132">**/fc**</span></span>|<span data-ttu-id="794f2-133">Hedef uygulamayı bulur veya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="794f2-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="794f2-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="794f2-134">**/help**</span></span>|<span data-ttu-id="794f2-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="794f2-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="794f2-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="794f2-136">**/noreconfig**</span></span>|<span data-ttu-id="794f2-137">Varolan bir hedef uygulamayı yeniden yapılandırmaz.</span><span class="sxs-lookup"><span data-stu-id="794f2-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="794f2-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="794f2-138">**/nologo**</span></span>|<span data-ttu-id="794f2-139">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="794f2-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="794f2-140">**/parname:** *adı*</span><span class="sxs-lookup"><span data-stu-id="794f2-140">**/parname:** *name*</span></span>|<span data-ttu-id="794f2-141">Bulunacak veya oluşturulacak COM+ uygulamasının adını veya kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="794f2-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="794f2-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="794f2-142">**/reconfig**</span></span>|<span data-ttu-id="794f2-143">Varolan bir hedef uygulamayı yeniden yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="794f2-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="794f2-144">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="794f2-144">This is the default.</span></span>|  
|<span data-ttu-id="794f2-145">**TLB:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="794f2-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="794f2-146">Yüklenecek tür kitaplığı dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="794f2-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="794f2-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="794f2-147">**/u**</span></span>|<span data-ttu-id="794f2-148">Hedef uygulamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="794f2-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="794f2-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="794f2-149">**/quiet**</span></span>|<span data-ttu-id="794f2-150">Sessiz modu belirtir; logo ve başarı iletisi görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="794f2-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="794f2-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="794f2-151">**/?**</span></span>|<span data-ttu-id="794f2-152">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="794f2-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="794f2-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="794f2-153">Remarks</span></span>  
 <span data-ttu-id="794f2-154">Regsvcs.exe tarafından belirtilen kaynak derleme dosyası gerektirir *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="794f2-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="794f2-155">Bu derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="794f2-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="794f2-156">Güçlü ad imzalama hakkında daha fazla bilgi için bkz: [bir derlemeyi tanımlayıcı adla imzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="794f2-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="794f2-157">Hedef uygulamanın ve tür kitaplığı dosyasının adları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="794f2-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="794f2-158">*ApplicationName* bağımsız değişkeni kaynak derleme dosyasından oluşturulabilir ve Regsvcs.exe tarafından zaten yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="794f2-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="794f2-159">*Typelibraryfile* bağımsız değişkeni bir tür kitaplığı adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="794f2-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="794f2-160">Bir tür kitaplığı adı belirtmezseniz, Regsvcs.exe derleme adını varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="794f2-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="794f2-161">Regsvcs.exe bir bileşenin yöntemleri kaydettiğinde tabi olan [taleplerini](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) ve [bağlantı talepleri](../../../docs/framework/misc/link-demands.md) bu yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="794f2-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="794f2-162">Araç tam olarak güvenilen bir ortamda yürütüldüğünden, izin taleplerinin çoğu başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="794f2-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="794f2-163">Ancak, Regsvcs.exe bileşenleri için isteğe bağlı veya bağlantı bir istek tarafından korunan yöntemleriyle kaydı yapılamıyor <xref:System.Security.Permissions.StrongNameIdentityPermission> veya <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="794f2-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="794f2-164">Regsvcs.exe'yi kullanmak için yerel bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="794f2-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="794f2-165">Bu eylemlerden herhangi birini gerçekleştirirken Regsvcs.exe başarısız olursa, ilgili hata iletilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="794f2-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="794f2-166">Örnekler</span><span class="sxs-lookup"><span data-stu-id="794f2-166">Examples</span></span>  
 <span data-ttu-id="794f2-167">Aşağıdaki komut içinde yer alan tüm ortak sınıflar ekler `myTest.dll` için `myTargetApp` (bir var olan COM + uygulaması) ve üretir `myTest.tlb` tür kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="794f2-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="794f2-168">Aşağıdaki komut içinde yer alan tüm ortak sınıflar ekler `myTest.dll` için `myTargetApp` (bir var olan COM + uygulaması) ve üretir `newTest.tlb` tür kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="794f2-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="794f2-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="794f2-169">See Also</span></span>  
 [<span data-ttu-id="794f2-170">Araçlar</span><span class="sxs-lookup"><span data-stu-id="794f2-170">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="794f2-171">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="794f2-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="794f2-172">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="794f2-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
