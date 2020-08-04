---
title: Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)
description: .NET Hizmetleri Yükleme Aracı Regsvcs.exe kullanın. Bir derlemeyi yükleyin ve kaydedin, bir sınıfa programlı olarak eklediğiniz hizmetleri yapılandırın ve daha fazlasını yapın.
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 6d0090eda764113407e35a3bcec139f1c7cfb050
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517249"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="e5fa0-104">Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="e5fa0-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="e5fa0-105">.NET Hizmetleri Yükleme aracı aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e5fa0-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="e5fa0-106">Bir derlemeyi yükler ve kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="e5fa0-107">Bir tür kitaplığı üretir, kaydeder ve belirtilen bir COM+ uygulamasına yükler.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="e5fa0-108">Sınıfınıza program aracılığıyla eklediğiniz hizmetleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="e5fa0-109">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="e5fa0-110">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e5fa0-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="e5fa0-111">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="e5fa0-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5fa0-112">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e5fa0-112">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="e5fa0-113">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5fa0-113">Parameters</span></span>  
  
|<span data-ttu-id="e5fa0-114">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="e5fa0-114">Argument</span></span>|<span data-ttu-id="e5fa0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5fa0-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e5fa0-116">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="e5fa0-116">*assemblyFile.dll*</span></span>|<span data-ttu-id="e5fa0-117">Kaynak derleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-117">The source assembly file.</span></span> <span data-ttu-id="e5fa0-118">Derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-118">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="e5fa0-119">Daha fazla bilgi için bkz. [bir derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="e5fa0-119">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="e5fa0-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="e5fa0-120">Option</span></span>|<span data-ttu-id="e5fa0-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5fa0-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e5fa0-122">**/Appdir:** *yol*</span><span class="sxs-lookup"><span data-stu-id="e5fa0-122">**/appdir:** *path*</span></span>|<span data-ttu-id="e5fa0-123">Uygulamanın kök dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-123">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="e5fa0-124">**/appname:** *ApplicationName*</span><span class="sxs-lookup"><span data-stu-id="e5fa0-124">**/appname:** *applicationName*</span></span>|<span data-ttu-id="e5fa0-125">Bulunacak veya oluşturulacak COM+ uygulamasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-125">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="e5fa0-126">**/c**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-126">**/c**</span></span>|<span data-ttu-id="e5fa0-127">Hedef uygulamayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-127">Creates the target application.</span></span>|  
|<span data-ttu-id="e5fa0-128">**/componly**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-128">**/componly**</span></span>|<span data-ttu-id="e5fa0-129">Yalnızca bileşenleri yapılandırır; yöntemleri ve arabirimleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-129">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="e5fa0-130">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-130">**/exapp**</span></span>|<span data-ttu-id="e5fa0-131">Varolan bir uygulamayı beklemek üzere aracı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-131">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="e5fa0-132">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-132">**/extlb**</span></span>|<span data-ttu-id="e5fa0-133">Varolan bir tür kitaplığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-133">Uses an existing type library.</span></span>|  
|<span data-ttu-id="e5fa0-134">**/FC**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-134">**/fc**</span></span>|<span data-ttu-id="e5fa0-135">Hedef uygulamayı bulur veya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-135">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="e5fa0-136">**/Help**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-136">**/help**</span></span>|<span data-ttu-id="e5fa0-137">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-137">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="e5fa0-138">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-138">**/noreconfig**</span></span>|<span data-ttu-id="e5fa0-139">Varolan bir hedef uygulamayı yeniden yapılandırmaz.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-139">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="e5fa0-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-140">**/nologo**</span></span>|<span data-ttu-id="e5fa0-141">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="e5fa0-142">**/parName:** *ad*</span><span class="sxs-lookup"><span data-stu-id="e5fa0-142">**/parname:** *name*</span></span>|<span data-ttu-id="e5fa0-143">Bulunacak veya oluşturulacak COM+ uygulamasının adını veya kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-143">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="e5fa0-144">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-144">**/reconfig**</span></span>|<span data-ttu-id="e5fa0-145">Varolan bir hedef uygulamayı yeniden yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-145">Reconfigures an existing target application.</span></span> <span data-ttu-id="e5fa0-146">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-146">This is the default.</span></span>|  
|<span data-ttu-id="e5fa0-147">**/tlb:** *TypeLibraryFile*</span><span class="sxs-lookup"><span data-stu-id="e5fa0-147">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="e5fa0-148">Yüklenecek tür kitaplığı dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-148">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="e5fa0-149">**p**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-149">**/u**</span></span>|<span data-ttu-id="e5fa0-150">Hedef uygulamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-150">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="e5fa0-151">**/**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-151">**/quiet**</span></span>|<span data-ttu-id="e5fa0-152">Sessiz modu belirtir; logo ve başarı iletisi görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-152">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="e5fa0-153">**/?**</span><span class="sxs-lookup"><span data-stu-id="e5fa0-153">**/?**</span></span>|<span data-ttu-id="e5fa0-154">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-154">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5fa0-155">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5fa0-155">Remarks</span></span>  
 <span data-ttu-id="e5fa0-156">Regsvcs.exe, *assemblyFile.dll*tarafından belirtilen bir kaynak derleme dosyası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-156">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="e5fa0-157">Bu derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-157">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="e5fa0-158">Tanımlayıcı ad imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi tanımlayıcı bir adla imzalama](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="e5fa0-158">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="e5fa0-159">Hedef uygulamanın ve tür kitaplığı dosyasının adları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-159">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="e5fa0-160">*ApplicationName* bağımsız değişkeni kaynak derleme dosyasından oluşturulabilir ve henüz yoksa Regsvcs.exe tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-160">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="e5fa0-161">*TypeLibraryFile* bağımsız değişkeni bir tür kitaplığı adı belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-161">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="e5fa0-162">Bir tür kitaplığı adı belirtmezseniz, Regsvcs.exe derleme adını varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-162">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="e5fa0-163">Regsvcs.exe bir bileşenin yöntemlerini kaydettiğinde, bu yöntemler için [talepler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) ve [bağlantı taleplerine](../misc/link-demands.md) tabidir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-163">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="e5fa0-164">Araç tam olarak güvenilen bir ortamda yürütüldüğünden, izin taleplerinin çoğu başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-164">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="e5fa0-165">Ancak Regsvcs.exe, veya için talep veya bağlantı talebi tarafından korunan yöntemlerle bileşenleri kaydedemez <xref:System.Security.Permissions.StrongNameIdentityPermission> <xref:System.Security.Permissions.PublisherIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="e5fa0-165">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="e5fa0-166">Regsvcs.exe'yi kullanmak için yerel bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-166">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="e5fa0-167">Bu eylemlerden herhangi birini gerçekleştirirken Regsvcs.exe başarısız olursa, ilgili hata iletilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-167">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e5fa0-168">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e5fa0-168">Examples</span></span>  
 <span data-ttu-id="e5fa0-169">Aşağıdaki komut ' de bulunan tüm ortak sınıfları `myTest.dll` `myTargetApp` (var olan bir com+ uygulaması) öğesine ekler ve `myTest.tlb` tür kitaplığını üretir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="e5fa0-170">Aşağıdaki komut ' de bulunan tüm ortak sınıfları `myTest.dll` `myTargetApp` (var olan bir com+ uygulaması) öğesine ekler ve `newTest.tlb` tür kitaplığını üretir.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-170">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5fa0-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-171">See also</span></span>

- [<span data-ttu-id="e5fa0-172">Araçlar</span><span class="sxs-lookup"><span data-stu-id="e5fa0-172">Tools</span></span>](index.md)
- [<span data-ttu-id="e5fa0-173">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="e5fa0-173">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="e5fa0-174">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="e5fa0-174">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
