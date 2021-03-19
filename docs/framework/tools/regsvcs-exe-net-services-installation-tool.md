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
ms.openlocfilehash: 03787ecacc00c35f31f1fa5101fff5882e5314f6
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653315"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="5ae13-104">Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)</span><span class="sxs-lookup"><span data-stu-id="5ae13-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>

<span data-ttu-id="5ae13-105">.NET Hizmetleri Yükleme aracı aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="5ae13-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="5ae13-106">Bir derlemeyi yükler ve kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5ae13-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="5ae13-107">Bir tür kitaplığı üretir, kaydeder ve belirtilen bir COM+ uygulamasına yükler.</span><span class="sxs-lookup"><span data-stu-id="5ae13-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="5ae13-108">Sınıfınıza program aracılığıyla eklediğiniz hizmetleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5ae13-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="5ae13-109">Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="5ae13-109">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="5ae13-110">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="5ae13-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ae13-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ae13-111">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="5ae13-112">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ae13-112">Parameters</span></span>  
  
|<span data-ttu-id="5ae13-113">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="5ae13-113">Argument</span></span>|<span data-ttu-id="5ae13-114">Description</span><span class="sxs-lookup"><span data-stu-id="5ae13-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5ae13-115">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="5ae13-115">*assemblyFile.dll*</span></span>|<span data-ttu-id="5ae13-116">Kaynak derleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="5ae13-116">The source assembly file.</span></span> <span data-ttu-id="5ae13-117">Derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-117">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="5ae13-118">Daha fazla bilgi için bkz. [bir derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="5ae13-118">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="5ae13-119">Seçenek</span><span class="sxs-lookup"><span data-stu-id="5ae13-119">Option</span></span>|<span data-ttu-id="5ae13-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ae13-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5ae13-121">**/Appdir:** *yol*</span><span class="sxs-lookup"><span data-stu-id="5ae13-121">**/appdir:** *path*</span></span>|<span data-ttu-id="5ae13-122">Uygulamanın kök dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-122">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="5ae13-123">**/appname:** *ApplicationName*</span><span class="sxs-lookup"><span data-stu-id="5ae13-123">**/appname:** *applicationName*</span></span>|<span data-ttu-id="5ae13-124">Bulunacak veya oluşturulacak COM+ uygulamasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-124">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="5ae13-125">**/c**</span><span class="sxs-lookup"><span data-stu-id="5ae13-125">**/c**</span></span>|<span data-ttu-id="5ae13-126">Hedef uygulamayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ae13-126">Creates the target application.</span></span>|  
|<span data-ttu-id="5ae13-127">**/componly**</span><span class="sxs-lookup"><span data-stu-id="5ae13-127">**/componly**</span></span>|<span data-ttu-id="5ae13-128">Yalnızca bileşenleri yapılandırır; yöntemleri ve arabirimleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="5ae13-128">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="5ae13-129">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="5ae13-129">**/exapp**</span></span>|<span data-ttu-id="5ae13-130">Varolan bir uygulamayı beklemek üzere aracı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-130">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="5ae13-131">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="5ae13-131">**/extlb**</span></span>|<span data-ttu-id="5ae13-132">Varolan bir tür kitaplığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ae13-132">Uses an existing type library.</span></span>|  
|<span data-ttu-id="5ae13-133">**/FC**</span><span class="sxs-lookup"><span data-stu-id="5ae13-133">**/fc**</span></span>|<span data-ttu-id="5ae13-134">Hedef uygulamayı bulur veya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ae13-134">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="5ae13-135">**/Help**</span><span class="sxs-lookup"><span data-stu-id="5ae13-135">**/help**</span></span>|<span data-ttu-id="5ae13-136">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5ae13-136">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="5ae13-137">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="5ae13-137">**/noreconfig**</span></span>|<span data-ttu-id="5ae13-138">Varolan bir hedef uygulamayı yeniden yapılandırmaz.</span><span class="sxs-lookup"><span data-stu-id="5ae13-138">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="5ae13-139">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="5ae13-139">**/nologo**</span></span>|<span data-ttu-id="5ae13-140">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="5ae13-140">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="5ae13-141">**/parName:** *ad*</span><span class="sxs-lookup"><span data-stu-id="5ae13-141">**/parname:** *name*</span></span>|<span data-ttu-id="5ae13-142">Bulunacak veya oluşturulacak COM+ uygulamasının adını veya kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-142">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="5ae13-143">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="5ae13-143">**/reconfig**</span></span>|<span data-ttu-id="5ae13-144">Varolan bir hedef uygulamayı yeniden yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5ae13-144">Reconfigures an existing target application.</span></span> <span data-ttu-id="5ae13-145">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-145">This is the default.</span></span>|  
|<span data-ttu-id="5ae13-146">**/tlb:** *TypeLibraryFile*</span><span class="sxs-lookup"><span data-stu-id="5ae13-146">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="5ae13-147">Yüklenecek tür kitaplığı dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-147">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="5ae13-148">**p**</span><span class="sxs-lookup"><span data-stu-id="5ae13-148">**/u**</span></span>|<span data-ttu-id="5ae13-149">Hedef uygulamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5ae13-149">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="5ae13-150">**/**</span><span class="sxs-lookup"><span data-stu-id="5ae13-150">**/quiet**</span></span>|<span data-ttu-id="5ae13-151">Sessiz modu belirtir; logo ve başarı iletisi görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="5ae13-151">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="5ae13-152">**/?**</span><span class="sxs-lookup"><span data-stu-id="5ae13-152">**/?**</span></span>|<span data-ttu-id="5ae13-153">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5ae13-153">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ae13-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ae13-154">Remarks</span></span>  

 <span data-ttu-id="5ae13-155">Regsvcs.exe, *assemblyFile.dll* tarafından belirtilen bir kaynak derleme dosyası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-155">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="5ae13-156">Bu derlemenin tanımlayıcı ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-156">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="5ae13-157">Tanımlayıcı ad imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi tanımlayıcı bir adla imzalama](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="5ae13-157">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="5ae13-158">Hedef uygulamanın ve tür kitaplığı dosyasının adları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5ae13-158">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="5ae13-159">*ApplicationName* bağımsız değişkeni kaynak derleme dosyasından oluşturulabilir ve henüz yoksa Regsvcs.exe tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5ae13-159">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="5ae13-160">*TypeLibraryFile* bağımsız değişkeni bir tür kitaplığı adı belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-160">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="5ae13-161">Bir tür kitaplığı adı belirtmezseniz, Regsvcs.exe derleme adını varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ae13-161">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="5ae13-162">Regsvcs.exe bir bileşenin yöntemlerini kaydettiğinde, bu yöntemler için [talepler](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) ve [bağlantı taleplerine](../misc/link-demands.md) tabidir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-162">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="5ae13-163">Araç tam olarak güvenilen bir ortamda yürütüldüğünden, izin taleplerinin çoğu başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="5ae13-163">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="5ae13-164">Ancak Regsvcs.exe, veya için talep veya bağlantı talebi tarafından korunan yöntemlerle bileşenleri kaydedemez <xref:System.Security.Permissions.StrongNameIdentityPermission> <xref:System.Security.Permissions.PublisherIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="5ae13-164">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="5ae13-165">Regsvcs.exe'yi kullanmak için yerel bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-165">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="5ae13-166">Bu eylemlerden herhangi birini gerçekleştirirken Regsvcs.exe başarısız olursa, ilgili hata iletilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5ae13-166">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5ae13-167">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5ae13-167">Examples</span></span>  

 <span data-ttu-id="5ae13-168">Aşağıdaki komut ' de bulunan tüm ortak sınıfları `myTest.dll` `myTargetApp` (var olan bir com+ uygulaması) öğesine ekler ve `myTest.tlb` tür kitaplığını üretir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="5ae13-169">Aşağıdaki komut ' de bulunan tüm ortak sınıfları `myTest.dll` `myTargetApp` (var olan bir com+ uygulaması) öğesine ekler ve `newTest.tlb` tür kitaplığını üretir.</span><span class="sxs-lookup"><span data-stu-id="5ae13-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ae13-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ae13-170">See also</span></span>

- [<span data-ttu-id="5ae13-171">Araçlar</span><span class="sxs-lookup"><span data-stu-id="5ae13-171">Tools</span></span>](index.md)
- [<span data-ttu-id="5ae13-172">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="5ae13-172">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="5ae13-173">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="5ae13-173">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
