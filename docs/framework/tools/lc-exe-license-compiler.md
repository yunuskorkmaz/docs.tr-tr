---
title: Lc.exe (Lisans Derleyici)
description: Lisans derleyicisini Lc.exe kullanın. Bu araç lisanslama bilgilerine sahip metin dosyalarını okur ve bir CLR yürütülebilirini kaynak olarak eklemek için bir ikili dosya oluşturur.
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 69e79f4d2a75117f74428fdeee7684048d218e27
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654043"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="85ad2-104">Lc.exe (Lisans Derleyici)</span><span class="sxs-lookup"><span data-stu-id="85ad2-104">Lc.exe (License Compiler)</span></span>

<span data-ttu-id="85ad2-105">Lisans Derleyicisi lisans bilgilerini içeren metin dosyalarını okur ve kaynak olarak bir ortak dil çalışma zamanı çalıştırılabilir dosyasının içinde katıştırılabilir bir ikili dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="85ad2-105">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="85ad2-106">Bir .licx metin dosyası otomatik olarak üretilir veya forma lisanslı bir denetim eklendiğinde Windows Form Tasarlayıcısı tarafından güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-106">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="85ad2-107">Derlemenin parçası olarak, proje sistemi .licx metin dosyasını .NET kontrol lisanslaması için destek sağlayan bir .licenses ikili kaynağına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="85ad2-107">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="85ad2-108">İkili kaynak daha sonra proje çıktısına gömülecektir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-108">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="85ad2-109">Projenizi oluştururken Lisans Derleyicisi'ni kullandığınızda, 32 bit ve 64 arasında çapraz derleme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="85ad2-109">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="85ad2-110">Bunun nedeni, Lisans Derleyicisi'nin derlemeler yüklemek zorunda olması ve 64 bit derlemelerin 32 bit'lik bir uygulamadan yüklenmesine veya bunun tersinin yapılmasına izin verilmemesidir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-110">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="85ad2-111">Bu durumda, lisansı el ile derlemek için Lisans Derleyicisi'ni komut satırından kullanın ilgili mimariyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="85ad2-111">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="85ad2-112">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="85ad2-113">Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="85ad2-113">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="85ad2-114">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="85ad2-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85ad2-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="85ad2-115">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="85ad2-116">Seçenek</span><span class="sxs-lookup"><span data-stu-id="85ad2-116">Option</span></span>|<span data-ttu-id="85ad2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85ad2-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="85ad2-118">**/complist:** *filename*</span><span class="sxs-lookup"><span data-stu-id="85ad2-118">**/complist:** *filename*</span></span>|<span data-ttu-id="85ad2-119">.licenses dosyasına eklenecek lisanslı bileşenlerin listesini içeren dosyanın adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="85ad2-119">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="85ad2-120">Her bir bileşene, her satırda yalnızca bir bileşen olacak şekilde, bileşenin tam adı kullanılarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="85ad2-120">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="85ad2-121">Komut satırı kullanıcıları projedeki her bir form için ayrı bir dosya belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-121">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="85ad2-122">Lc.exe birden çok giriş dosyasını kabul eder ve tek bir .licenses dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-122">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="85ad2-123">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="85ad2-123">**/h**[**elp**]</span></span>|<span data-ttu-id="85ad2-124">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85ad2-124">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="85ad2-125">**/i:** *module*</span><span class="sxs-lookup"><span data-stu-id="85ad2-125">**/i:** *module*</span></span>|<span data-ttu-id="85ad2-126">**/Complist** dosyasında listelenen bileşenleri içeren modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-126">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="85ad2-127">Birden fazla modül belirtmek için birden çok **/i** bayrağı kullanın.</span><span class="sxs-lookup"><span data-stu-id="85ad2-127">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="85ad2-128">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="85ad2-128">**/nologo**</span></span>|<span data-ttu-id="85ad2-129">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="85ad2-129">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="85ad2-130">**/OutDir:** *yol*</span><span class="sxs-lookup"><span data-stu-id="85ad2-130">**/outdir:** *path*</span></span>|<span data-ttu-id="85ad2-131">Çıkış .licenses dosyasının yerleştirileceği dizin belirtir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-131">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="85ad2-132">**/target:** *targetpe*</span><span class="sxs-lookup"><span data-stu-id="85ad2-132">**/target:** *targetPE*</span></span>|<span data-ttu-id="85ad2-133">.licenses dosyasının kendisi için üretilmekte olduğu yürütülebilir dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-133">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="85ad2-134">**çıktıda**</span><span class="sxs-lookup"><span data-stu-id="85ad2-134">**/v**</span></span>|<span data-ttu-id="85ad2-135">Ayrıntılı modu belirtir; derleme ilerleme bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85ad2-135">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="85ad2-136">\**@\*\*\*Dosya*</span><span class="sxs-lookup"><span data-stu-id="85ad2-136">**@** *file*</span></span>|<span data-ttu-id="85ad2-137">Yanıt (. rsp) dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-137">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="85ad2-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="85ad2-138">**/?**</span></span>|<span data-ttu-id="85ad2-139">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85ad2-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="85ad2-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="85ad2-140">Example</span></span>  
  
1. <span data-ttu-id="85ad2-141">Adlı bir uygulamada bulunan lisanslı bir denetim kullanıyorsanız `MyCompany.Samples.LicControl1` `Samples.DLL` `HostApp.exe` *,* `HostAppLic.txt` aşağıdakileri içeren oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85ad2-141">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="85ad2-142">Aşağıdaki komutu kullanarak adlı. lisansları dosyasını oluşturun `HostApp.exe.licenses` .</span><span class="sxs-lookup"><span data-stu-id="85ad2-142">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="85ad2-143">`HostApp.exe`. Lisanslar dosyasını kaynak olarak içeren derleme.</span><span class="sxs-lookup"><span data-stu-id="85ad2-143">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="85ad2-144">Bir C# uygulaması oluşturuyorsanız, uygulamanızı oluşturmak için aşağıdaki komutu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="85ad2-144">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="85ad2-145">Aşağıdaki komut `myApp.licenses` , ve tarafından belirtilen lisanslı bileşenler listesinden derlenir `hostapplic.txt` `hostapplic2.txt` `hostapplic3.txt` .</span><span class="sxs-lookup"><span data-stu-id="85ad2-145">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="85ad2-146">`modulesList`Bağımsız değişkeni, lisanslı bileşenleri içeren modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="85ad2-146">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="85ad2-147">Yanıt dosyası örneği</span><span class="sxs-lookup"><span data-stu-id="85ad2-147">Response File Example</span></span>  

 <span data-ttu-id="85ad2-148">Aşağıdaki listede bir yanıt dosyası örneği gösterilmektedir `response.rsp` .</span><span class="sxs-lookup"><span data-stu-id="85ad2-148">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="85ad2-149">Yanıt dosyaları hakkında daha fazla bilgi için bkz. [yanıt dosyaları](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="85ad2-149">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="85ad2-150">Aşağıdaki komut satırı `response.rsp` dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="85ad2-150">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="85ad2-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85ad2-151">See also</span></span>

- [<span data-ttu-id="85ad2-152">Araçlar</span><span class="sxs-lookup"><span data-stu-id="85ad2-152">Tools</span></span>](index.md)
- [<span data-ttu-id="85ad2-153">Al.exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="85ad2-153">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="85ad2-154">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="85ad2-154">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
