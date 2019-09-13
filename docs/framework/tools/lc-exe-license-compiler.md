---
title: Lc.exe (Lisans Derleyici)
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
ms.openlocfilehash: 753312005cd60b5be6bf5504fa9b7f14bd6367fe
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894671"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="c7597-102">Lc.exe (Lisans Derleyici)</span><span class="sxs-lookup"><span data-stu-id="c7597-102">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="c7597-103">Lisans Derleyicisi lisans bilgilerini içeren metin dosyalarını okur ve kaynak olarak bir ortak dil çalışma zamanı çalıştırılabilir dosyasının içinde katıştırılabilir bir ikili dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7597-103">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="c7597-104">Bir .licx metin dosyası otomatik olarak üretilir veya forma lisanslı bir denetim eklendiğinde Windows Form Tasarlayıcısı tarafından güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c7597-104">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="c7597-105">Derlemenin parçası olarak, proje sistemi .licx metin dosyasını .NET kontrol lisanslaması için destek sağlayan bir .licenses ikili kaynağına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c7597-105">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="c7597-106">İkili kaynak daha sonra proje çıktısına gömülecektir.</span><span class="sxs-lookup"><span data-stu-id="c7597-106">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="c7597-107">Projenizi oluştururken Lisans Derleyicisi'ni kullandığınızda, 32 bit ve 64 arasında çapraz derleme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c7597-107">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="c7597-108">Bunun nedeni, Lisans Derleyicisi'nin derlemeler yüklemek zorunda olması ve 64 bit derlemelerin 32 bit'lik bir uygulamadan yüklenmesine veya bunun tersinin yapılmasına izin verilmemesidir.</span><span class="sxs-lookup"><span data-stu-id="c7597-108">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="c7597-109">Bu durumda, lisansı el ile derlemek için Lisans Derleyicisi'ni komut satırından kullanın ilgili mimariyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="c7597-109">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="c7597-110">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c7597-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="c7597-111">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7597-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="c7597-112">Daha fazla bilgi için bkz. [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c7597-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="c7597-113">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="c7597-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7597-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7597-114">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="c7597-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="c7597-115">Option</span></span>|<span data-ttu-id="c7597-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7597-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c7597-117">**/complist:** *dosya adı*</span><span class="sxs-lookup"><span data-stu-id="c7597-117">**/complist:** *filename*</span></span>|<span data-ttu-id="c7597-118">.licenses dosyasına eklenecek lisanslı bileşenlerin listesini içeren dosyanın adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="c7597-118">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="c7597-119">Her bir bileşene, her satırda yalnızca bir bileşen olacak şekilde, bileşenin tam adı kullanılarak başvurulur.</span><span class="sxs-lookup"><span data-stu-id="c7597-119">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="c7597-120">Komut satırı kullanıcıları projedeki her bir form için ayrı bir dosya belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="c7597-120">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="c7597-121">Lc.exe birden çok giriş dosyasını kabul eder ve tek bir .licenses dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="c7597-121">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="c7597-122">**/h** [**ELP**]</span><span class="sxs-lookup"><span data-stu-id="c7597-122">**/h**[**elp**]</span></span>|<span data-ttu-id="c7597-123">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c7597-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="c7597-124">**/i:** *Modül*</span><span class="sxs-lookup"><span data-stu-id="c7597-124">**/i:** *module*</span></span>|<span data-ttu-id="c7597-125">**/Complist** dosyasında listelenen bileşenleri içeren modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7597-125">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="c7597-126">Birden fazla modül belirtmek için birden çok **/i** bayrağı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7597-126">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="c7597-127">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="c7597-127">**/nologo**</span></span>|<span data-ttu-id="c7597-128">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="c7597-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="c7597-129">**/OutDir:** *yol*</span><span class="sxs-lookup"><span data-stu-id="c7597-129">**/outdir:** *path*</span></span>|<span data-ttu-id="c7597-130">Çıkış .licenses dosyasının yerleştirileceği dizin belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7597-130">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="c7597-131">**/target:** *Targetpe*</span><span class="sxs-lookup"><span data-stu-id="c7597-131">**/target:** *targetPE*</span></span>|<span data-ttu-id="c7597-132">.licenses dosyasının kendisi için üretilmekte olduğu yürütülebilir dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7597-132">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="c7597-133">**çıktıda**</span><span class="sxs-lookup"><span data-stu-id="c7597-133">**/v**</span></span>|<span data-ttu-id="c7597-134">Ayrıntılı modu belirtir; derleme ilerleme bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c7597-134">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="c7597-135">**@** *Dosya*</span><span class="sxs-lookup"><span data-stu-id="c7597-135">**@** *file*</span></span>|<span data-ttu-id="c7597-136">Yanıt (. rsp) dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7597-136">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="c7597-137">**/?**</span><span class="sxs-lookup"><span data-stu-id="c7597-137">**/?**</span></span>|<span data-ttu-id="c7597-138">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c7597-138">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7597-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7597-139">Example</span></span>  
  
1. <span data-ttu-id="c7597-140">Adlı `MyCompany.Samples.LicControl1` `Samples.DLL` `HostAppLic.txt` bir uygulamada bulunan lisanslı bir denetim kullanıyorsanız, aşağıdakileri içeren oluşturabilirsiniz. `HostApp.exe`</span><span class="sxs-lookup"><span data-stu-id="c7597-140">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="c7597-141">Aşağıdaki komutu kullanarak adlı `HostApp.exe.licenses` . lisansları dosyasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c7597-141">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="c7597-142">. `HostApp.exe` Lisanslar dosyasını kaynak olarak içeren derleme.</span><span class="sxs-lookup"><span data-stu-id="c7597-142">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="c7597-143">Bir C# uygulaması oluşturuyorsanız, uygulamanızı oluşturmak için aşağıdaki komutu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c7597-143">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="c7597-144">Aşağıdaki `myApp.licenses` komut, `hostapplic.txt` `hostapplic2.txt` ve tarafındanbelirtilenlisanslıbileşenlerlistesindenderlenir.`hostapplic3.txt`</span><span class="sxs-lookup"><span data-stu-id="c7597-144">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="c7597-145">`modulesList` Bağımsız değişkeni, lisanslı bileşenleri içeren modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7597-145">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="c7597-146">Yanıt dosyası örneği</span><span class="sxs-lookup"><span data-stu-id="c7597-146">Response File Example</span></span>  
 <span data-ttu-id="c7597-147">Aşağıdaki listede bir yanıt dosyası `response.rsp`örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7597-147">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="c7597-148">Yanıt dosyaları hakkında daha fazla bilgi için bkz. [yanıt dosyaları](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="c7597-148">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="c7597-149">Aşağıdaki komut satırı `response.rsp` dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7597-149">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7597-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7597-150">See also</span></span>

- [<span data-ttu-id="c7597-151">Araçlar</span><span class="sxs-lookup"><span data-stu-id="c7597-151">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="c7597-152">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="c7597-152">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="c7597-153">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="c7597-153">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
