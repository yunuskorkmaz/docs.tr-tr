---
title: Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d221c10a0ded848cb24f256ce8afc080e6de44a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614640"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="6a098-102">Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="6a098-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="6a098-103">.NET Hizmetleri Yükleme aracı aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="6a098-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
-   <span data-ttu-id="6a098-104">Bir derlemeyi yükler ve kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6a098-104">Loads and registers an assembly.</span></span>  
  
-   <span data-ttu-id="6a098-105">Bir tür kitaplığı üretir, kaydeder ve belirtilen bir COM+ uygulamasına yükler.</span><span class="sxs-lookup"><span data-stu-id="6a098-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
-   <span data-ttu-id="6a098-106">Sınıfınıza program aracılığıyla eklediğiniz hizmetleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6a098-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="6a098-107">Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a098-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6a098-108">Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6a098-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="6a098-109">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="6a098-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a098-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a098-110">Syntax</span></span>  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a098-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a098-111">Parameters</span></span>  
  
|<span data-ttu-id="6a098-112">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="6a098-112">Argument</span></span>|<span data-ttu-id="6a098-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a098-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6a098-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="6a098-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="6a098-115">Kaynak derleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="6a098-115">The source assembly file.</span></span> <span data-ttu-id="6a098-116">Derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a098-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="6a098-117">Daha fazla bilgi için [bir derlemeyi tanımlayıcı adla imzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="6a098-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="6a098-118">Seçenek</span><span class="sxs-lookup"><span data-stu-id="6a098-118">Option</span></span>|<span data-ttu-id="6a098-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a098-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6a098-120">**/appdir:** *yolu*</span><span class="sxs-lookup"><span data-stu-id="6a098-120">**/appdir:** *path*</span></span>|<span data-ttu-id="6a098-121">Uygulamanın kök dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a098-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="6a098-122">**yüklemede:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="6a098-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="6a098-123">Bulunacak veya oluşturulacak COM+ uygulamasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a098-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="6a098-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="6a098-124">**/c**</span></span>|<span data-ttu-id="6a098-125">Hedef uygulamayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a098-125">Creates the target application.</span></span>|  
|<span data-ttu-id="6a098-126">**/ componly**</span><span class="sxs-lookup"><span data-stu-id="6a098-126">**/componly**</span></span>|<span data-ttu-id="6a098-127">Yalnızca bileşenleri yapılandırır; yöntemleri ve arabirimleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="6a098-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="6a098-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="6a098-128">**/exapp**</span></span>|<span data-ttu-id="6a098-129">Varolan bir uygulamayı beklemek üzere aracı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a098-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="6a098-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="6a098-130">**/extlb**</span></span>|<span data-ttu-id="6a098-131">Varolan bir tür kitaplığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a098-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="6a098-132">**/FC**</span><span class="sxs-lookup"><span data-stu-id="6a098-132">**/fc**</span></span>|<span data-ttu-id="6a098-133">Hedef uygulamayı bulur veya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a098-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="6a098-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="6a098-134">**/help**</span></span>|<span data-ttu-id="6a098-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6a098-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="6a098-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="6a098-136">**/noreconfig**</span></span>|<span data-ttu-id="6a098-137">Varolan bir hedef uygulamayı yeniden yapılandırmaz.</span><span class="sxs-lookup"><span data-stu-id="6a098-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="6a098-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="6a098-138">**/nologo**</span></span>|<span data-ttu-id="6a098-139">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="6a098-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="6a098-140">**/parname:** *adı*</span><span class="sxs-lookup"><span data-stu-id="6a098-140">**/parname:** *name*</span></span>|<span data-ttu-id="6a098-141">Bulunacak veya oluşturulacak COM+ uygulamasının adını veya kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a098-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="6a098-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="6a098-142">**/reconfig**</span></span>|<span data-ttu-id="6a098-143">Varolan bir hedef uygulamayı yeniden yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6a098-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="6a098-144">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="6a098-144">This is the default.</span></span>|  
|<span data-ttu-id="6a098-145">**/ TLB:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="6a098-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="6a098-146">Yüklenecek tür kitaplığı dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a098-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="6a098-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="6a098-147">**/u**</span></span>|<span data-ttu-id="6a098-148">Hedef uygulamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6a098-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="6a098-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="6a098-149">**/quiet**</span></span>|<span data-ttu-id="6a098-150">Sessiz modu belirtir; logo ve başarı iletisi görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="6a098-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="6a098-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="6a098-151">**/?**</span></span>|<span data-ttu-id="6a098-152">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6a098-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a098-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a098-153">Remarks</span></span>  
 <span data-ttu-id="6a098-154">Regsvcs.exe tarafından belirtilen kaynak derleme dosyası gerektirir *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="6a098-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="6a098-155">Bu derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a098-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="6a098-156">Tanımlayıcı ad imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi tanımlayıcı adla imzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="6a098-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="6a098-157">Hedef uygulamanın ve tür kitaplığı dosyasının adları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6a098-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="6a098-158">*ApplicationName* bağımsız değişkeni, kaynak derleme dosyasından üretilebilir ve Regsvcs.exe tarafından zaten yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6a098-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="6a098-159">*Typelibraryfile* bağımsız değişkeni bir tür kitaplığı adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a098-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="6a098-160">Bir tür kitaplığı adı belirtmezseniz, Regsvcs.exe derleme adını varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a098-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="6a098-161">Regsvcs.exe bir bileşenin yöntemlerini kaydettiğinde, tabi olan [taleplerini](https://msdn.microsoft.com/library/e5283e28-2366-4519-b27d-ef5c1ddc1f48) ve [bağlantı talepleri](../../../docs/framework/misc/link-demands.md) o yöntemlerdeki.</span><span class="sxs-lookup"><span data-stu-id="6a098-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://msdn.microsoft.com/library/e5283e28-2366-4519-b27d-ef5c1ddc1f48) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="6a098-162">Araç tam olarak güvenilen bir ortamda yürütüldüğünden, izin taleplerinin çoğu başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="6a098-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="6a098-163">Ancak, Regsvcs.exe bileşenleri için bir talep veya bağlantı talebiyle korunan yöntemlerle kaydını yapamıyorum <xref:System.Security.Permissions.StrongNameIdentityPermission> veya <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="6a098-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="6a098-164">Regsvcs.exe'yi kullanmak için yerel bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a098-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="6a098-165">Bu eylemlerden herhangi birini gerçekleştirirken Regsvcs.exe başarısız olursa, ilgili hata iletilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6a098-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6a098-166">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6a098-166">Examples</span></span>  
 <span data-ttu-id="6a098-167">Aşağıdaki komut içinde bulunan tüm ortak sınıfları ekler `myTest.dll` için `myTargetApp` (bir mevcut COM + uygulaması) ve üretir `myTest.tlb` tür kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="6a098-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="6a098-168">Aşağıdaki komut içinde bulunan tüm ortak sınıfları ekler `myTest.dll` için `myTargetApp` (bir mevcut COM + uygulaması) ve üretir `newTest.tlb` tür kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="6a098-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a098-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a098-169">See also</span></span>
- [<span data-ttu-id="6a098-170">Araçlar</span><span class="sxs-lookup"><span data-stu-id="6a098-170">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="6a098-171">Nasıl yapılır: Derlemeyi tanımlayıcı bir adla imzalama</span><span class="sxs-lookup"><span data-stu-id="6a098-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [<span data-ttu-id="6a098-172">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="6a098-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
