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
ms.openlocfilehash: aecd2f6894558b45898c7f22dd333617d9e2e327
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180355"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="e2247-102">Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="e2247-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="e2247-103">.NET Hizmetleri Yükleme aracı aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e2247-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="e2247-104">Bir derlemeyi yükler ve kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e2247-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="e2247-105">Bir tür kitaplığı üretir, kaydeder ve belirtilen bir COM+ uygulamasına yükler.</span><span class="sxs-lookup"><span data-stu-id="e2247-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="e2247-106">Sınıfınıza program aracılığıyla eklediğiniz hizmetleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e2247-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="e2247-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span><span class="sxs-lookup"><span data-stu-id="e2247-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="e2247-108">Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e2247-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="e2247-109">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="e2247-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2247-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2247-110">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="e2247-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2247-111">Parameters</span></span>  
  
|<span data-ttu-id="e2247-112">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="e2247-112">Argument</span></span>|<span data-ttu-id="e2247-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2247-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e2247-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="e2247-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="e2247-115">Kaynak derleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="e2247-115">The source assembly file.</span></span> <span data-ttu-id="e2247-116">Derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2247-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="e2247-117">Daha fazla bilgi için [bkz.](../../standard/assembly/sign-strong-name.md)</span><span class="sxs-lookup"><span data-stu-id="e2247-117">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="e2247-118">Seçenek</span><span class="sxs-lookup"><span data-stu-id="e2247-118">Option</span></span>|<span data-ttu-id="e2247-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2247-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e2247-120">**/appdir:** *yol*</span><span class="sxs-lookup"><span data-stu-id="e2247-120">**/appdir:** *path*</span></span>|<span data-ttu-id="e2247-121">Uygulamanın kök dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2247-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="e2247-122">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="e2247-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="e2247-123">Bulunacak veya oluşturulacak COM+ uygulamasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2247-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="e2247-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="e2247-124">**/c**</span></span>|<span data-ttu-id="e2247-125">Hedef uygulamayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2247-125">Creates the target application.</span></span>|  
|<span data-ttu-id="e2247-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="e2247-126">**/componly**</span></span>|<span data-ttu-id="e2247-127">Yalnızca bileşenleri yapılandırır; yöntemleri ve arabirimleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e2247-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="e2247-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="e2247-128">**/exapp**</span></span>|<span data-ttu-id="e2247-129">Varolan bir uygulamayı beklemek üzere aracı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2247-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="e2247-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="e2247-130">**/extlb**</span></span>|<span data-ttu-id="e2247-131">Varolan bir tür kitaplığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2247-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="e2247-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="e2247-132">**/fc**</span></span>|<span data-ttu-id="e2247-133">Hedef uygulamayı bulur veya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2247-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="e2247-134">**/yardım**</span><span class="sxs-lookup"><span data-stu-id="e2247-134">**/help**</span></span>|<span data-ttu-id="e2247-135">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e2247-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="e2247-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="e2247-136">**/noreconfig**</span></span>|<span data-ttu-id="e2247-137">Varolan bir hedef uygulamayı yeniden yapılandırmaz.</span><span class="sxs-lookup"><span data-stu-id="e2247-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="e2247-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="e2247-138">**/nologo**</span></span>|<span data-ttu-id="e2247-139">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="e2247-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="e2247-140">**/parname:** *isim*</span><span class="sxs-lookup"><span data-stu-id="e2247-140">**/parname:** *name*</span></span>|<span data-ttu-id="e2247-141">Bulunacak veya oluşturulacak COM+ uygulamasının adını veya kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2247-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="e2247-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="e2247-142">**/reconfig**</span></span>|<span data-ttu-id="e2247-143">Varolan bir hedef uygulamayı yeniden yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e2247-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="e2247-144">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e2247-144">This is the default.</span></span>|  
|<span data-ttu-id="e2247-145">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="e2247-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="e2247-146">Yüklenecek tür kitaplığı dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2247-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="e2247-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="e2247-147">**/u**</span></span>|<span data-ttu-id="e2247-148">Hedef uygulamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e2247-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="e2247-149">**/sessiz**</span><span class="sxs-lookup"><span data-stu-id="e2247-149">**/quiet**</span></span>|<span data-ttu-id="e2247-150">Sessiz modu belirtir; logo ve başarı iletisi görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="e2247-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="e2247-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="e2247-151">**/?**</span></span>|<span data-ttu-id="e2247-152">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e2247-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2247-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2247-153">Remarks</span></span>  
 <span data-ttu-id="e2247-154">Regsvcs.exe *assemblyFile.dll*tarafından belirtilen bir kaynak derleme dosyası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e2247-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="e2247-155">Bu derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2247-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="e2247-156">Güçlü ad imzalama hakkında daha fazla bilgi için [bkz.](../../standard/assembly/sign-strong-name.md)</span><span class="sxs-lookup"><span data-stu-id="e2247-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="e2247-157">Hedef uygulamanın ve tür kitaplığı dosyasının adları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e2247-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="e2247-158">*ApplicationName* bağımsız değişkeni kaynak derleme dosyasından oluşturulabilir ve zaten yoksa Regsvcs.exe tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e2247-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="e2247-159">*Typelibraryfile* bağımsız değişkeni bir tür kitaplığı adı belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="e2247-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="e2247-160">Bir tür kitaplığı adı belirtmezseniz, Regsvcs.exe derleme adını varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2247-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="e2247-161">Regsvcs.exe bir bileşenin yöntemlerini kaydettiğinde, bu yöntemlerle ilgili [taleplere](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) ve [bağlantı taleplerine](../misc/link-demands.md) tabidir.</span><span class="sxs-lookup"><span data-stu-id="e2247-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="e2247-162">Araç tam olarak güvenilen bir ortamda yürütüldüğünden, izin taleplerinin çoğu başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="e2247-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="e2247-163">Ancak, Regsvcs.exe bileşenleri bir talep veya bağlantı talebi <xref:System.Security.Permissions.StrongNameIdentityPermission> tarafından <xref:System.Security.Permissions.PublisherIdentityPermission>korunan yöntemlerle kaydedemez.</span><span class="sxs-lookup"><span data-stu-id="e2247-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="e2247-164">Regsvcs.exe'yi kullanmak için yerel bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2247-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="e2247-165">Bu eylemlerden herhangi birini gerçekleştirirken Regsvcs.exe başarısız olursa, ilgili hata iletilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e2247-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e2247-166">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e2247-166">Examples</span></span>  
 <span data-ttu-id="e2247-167">Aşağıdaki komut, içerdiği `myTest.dll` tüm ortak `myTargetApp` sınıfları (varolan bir `myTest.tlb` COM+ uygulamasına) ekler ve tür kitaplığını üretir.</span><span class="sxs-lookup"><span data-stu-id="e2247-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="e2247-168">Aşağıdaki komut, içerdiği `myTest.dll` tüm ortak `myTargetApp` sınıfları (varolan bir `newTest.tlb` COM+ uygulamasına) ekler ve tür kitaplığını üretir.</span><span class="sxs-lookup"><span data-stu-id="e2247-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2247-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2247-169">See also</span></span>

- [<span data-ttu-id="e2247-170">Araçlar</span><span class="sxs-lookup"><span data-stu-id="e2247-170">Tools</span></span>](index.md)
- [<span data-ttu-id="e2247-171">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="e2247-171">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="e2247-172">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="e2247-172">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
