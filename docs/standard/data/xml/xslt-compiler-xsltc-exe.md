---
title: XSLT derleyici (xsltc.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 36696617d1e28a370f6b15f15fb39bc816973f15
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2018
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="966b6-102">XSLT derleyici (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="966b6-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="966b6-103">XSLT derleyici (xsltc.exe) XSLT stil sayfaları derler ve bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="966b6-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="966b6-104">Derlenmiş stil sayfası ardından doğrudan geçirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="966b6-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="966b6-105">İmzalı derlemeler xsltc.exe ile oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="966b6-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="966b6-106">Xsltc.exe aracı Visual Studio ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="966b6-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="966b6-107">Daha fazla bilgi için bkz: [Visual Studio indirmeleri](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="966b6-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966b6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="966b6-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="966b6-109">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="966b6-109">Argument</span></span>  
  
|<span data-ttu-id="966b6-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="966b6-110">Argument</span></span>|<span data-ttu-id="966b6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="966b6-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="966b6-112">Stil sayfasının adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="966b6-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="966b6-113">Stil sayfası veya intranette bulunan bir yerel dosya olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="966b6-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="966b6-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="966b6-114">Options</span></span>  
  
|<span data-ttu-id="966b6-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="966b6-115">Option</span></span>|<span data-ttu-id="966b6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="966b6-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="966b6-117">`/c[lass]:``name`</span><span class="sxs-lookup"><span data-stu-id="966b6-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="966b6-118">Aşağıdaki stil sayfası sınıfın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="966b6-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="966b6-119">Sınıf adı tam olabilir.</span><span class="sxs-lookup"><span data-stu-id="966b6-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="966b6-120">Sınıf adı varsayılan olarak stil sayfasının adı.</span><span class="sxs-lookup"><span data-stu-id="966b6-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="966b6-121">Örneğin, stil sayfası customers.xsl derlenmiş ise varsayılan sınıf adını müşterileri içindir.</span><span class="sxs-lookup"><span data-stu-id="966b6-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="966b6-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="966b6-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="966b6-123">Hata ayıklama bilgilerini oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="966b6-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="966b6-124">Belirtme `+` veya `/debug`, hata ayıklama bilgileri oluşturmak ve bir program veritabanı (PDB) dosyasında yerleştirin derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="966b6-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="966b6-125">Oluşturulan PDB dosyası adı `assemblyName`.pdb.</span><span class="sxs-lookup"><span data-stu-id="966b6-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="966b6-126">Belirtme `-`, hangi değil belirtirseniz yürürlükte olan `/debug`, hiçbir hata ayıklama bilgisi oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="966b6-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="966b6-127">Bir perakende derleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="966b6-127">A retail assembly is generated.</span></span> <span data-ttu-id="966b6-128">**Not:** hata ayıklama modunda derleme etkileyebilecek XSLT performansı önemli ölçüde.</span><span class="sxs-lookup"><span data-stu-id="966b6-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="966b6-129">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="966b6-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="966b6-130">Görüntülenmesini Derleyici telif hakkı iletisi gizler.</span><span class="sxs-lookup"><span data-stu-id="966b6-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="966b6-131">`/platform:``string`</span><span class="sxs-lookup"><span data-stu-id="966b6-131">`/platform:` `string`</span></span>|<span data-ttu-id="966b6-132">Derleme çalıştırılabilir platformları belirtir.</span><span class="sxs-lookup"><span data-stu-id="966b6-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="966b6-133">Geçerli platform değerleri açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="966b6-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="966b6-134">`x86` 32-bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılacak derlemenizi</span><span class="sxs-lookup"><span data-stu-id="966b6-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="966b6-135">`x64` AMD64 veya EM64T yönerge kümesi destekleyen bir bilgisayarda 64-bit ortak dil çalışma zamanı tarafından çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="966b6-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] <span data-ttu-id="966b6-136">derlemenizi olan bir bilgisayarda 64-bit ortak dil çalışma zamanı tarafından çalıştırılacak bir [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] işlemci.</span><span class="sxs-lookup"><span data-stu-id="966b6-136">compiles your assembly to be run by the 64-bit common language runtime on a computer that has an [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] processor.</span></span><br /><br /> <span data-ttu-id="966b6-137">`anycpu` Herhangi bir platformda çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="966b6-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="966b6-138">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="966b6-138">This is the default.</span></span>|  
|<span data-ttu-id="966b6-139">`/out:``assemblyName`</span><span class="sxs-lookup"><span data-stu-id="966b6-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="966b6-140">Çıkış bütünleştirilmiş kodun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="966b6-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="966b6-141">Birden çok stil sayfaları varsa ana stil sayfası veya ilk stil sayfası adını derleme adı varsayılan olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="966b6-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="966b6-142">Stil sayfası komut dosyaları içeriyorsa, komut dosyaları için ayrı bir derleme kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="966b6-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="966b6-143">Komut dosyası derleme adları ana derleme adından üretilir.</span><span class="sxs-lookup"><span data-stu-id="966b6-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="966b6-144">Örneğin, CustOrders.dll için derleme adınızı belirttiyseniz, ilk komut dosyası derleme CustOrders_Script1.dll olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="966b6-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="966b6-145">`/settings:``document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="966b6-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="966b6-146">İzin verilip verilmeyeceğini belirtir `document()` İşlevler, XSLT komut dosyası veya belge stil sayfanızda tanımı (DTD) yazın.</span><span class="sxs-lookup"><span data-stu-id="966b6-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="966b6-147">DTD desteği varsayılan davranışı devre dışı bırakır `document()` işlevi ve komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="966b6-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="966b6-148">`@``file`</span><span class="sxs-lookup"><span data-stu-id="966b6-148">`@` `file`</span></span>|<span data-ttu-id="966b6-149">Derleyici seçenekleri içeren bir dosyayı belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="966b6-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="966b6-150">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="966b6-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="966b6-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="966b6-151">Remarks</span></span>  
 <span data-ttu-id="966b6-152">XSLT çözümleri birden çok stil sayfası modüllerini oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="966b6-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="966b6-153">Xsltc.exe aracı derlemeleri stil sayfalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="966b6-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="966b6-154">Derlemeleri sonra içine aktarılabilecek <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="966b6-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="966b6-155">Bu, bazı XSLT dağıtım senaryolarında performans maliyetleri azaltmak yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="966b6-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="966b6-156">Uygulamanızda bir başvuru olarak derlenmiş derleme de dahil etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="966b6-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="966b6-157">Xsltc.exe araç sınıfı doğrulamaz (`/class:``name`) veya derleme (`/out:``assemblyName`) adları.</span><span class="sxs-lookup"><span data-stu-id="966b6-157">The xsltc.exe tool does not validate the class (`/class:``name`) or assembly (`/out:``assemblyName`) names.</span></span> <span data-ttu-id="966b6-158">Adları geçerli değilse, hatalar ortak dil çalışma zamanı tarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="966b6-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="966b6-159">Örnekler</span><span class="sxs-lookup"><span data-stu-id="966b6-159">Examples</span></span>  
 <span data-ttu-id="966b6-160">Aşağıdaki komut, stil sayfası derler ve booksort.dll adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="966b6-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="966b6-161">Aşağıdaki komut, stil sayfası derler ve bir derleme ve booksort.dll ve booksort.pdb sırasıyla adlı PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="966b6-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="966b6-162">Aşağıdaki komutu bir msxsl: Script öğesi içeriyor ve calc.dll ve calc_Script1.dll adlı iki derlemeler oluşturan bir stil sayfası derler.</span><span class="sxs-lookup"><span data-stu-id="966b6-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="966b6-163">Aşağıdaki komut DTD işleme ve komut dosyası desteğini etkinleştirir ve myTest.dll ve myTest_Script1.dll adlı iki derlemeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="966b6-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="966b6-164">Aşağıdaki komut iki stil sayfası modülleri derler ve booksort.dll adlı tek bir bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="966b6-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="966b6-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="966b6-165">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="966b6-166">Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="966b6-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [<span data-ttu-id="966b6-167">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="966b6-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
