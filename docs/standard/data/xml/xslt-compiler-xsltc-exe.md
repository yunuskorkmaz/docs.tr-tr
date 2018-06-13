---
title: XSLT derleyici (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aef49f70f3a60151aa053a1a94a06bc71401531e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575446"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="7fa55-102">XSLT derleyici (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="7fa55-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="7fa55-103">XSLT derleyici (xsltc.exe) XSLT stil sayfaları derler ve bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="7fa55-104">Derlenmiş stil sayfası ardından doğrudan geçirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7fa55-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7fa55-105">İmzalı derlemeler xsltc.exe ile oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="7fa55-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="7fa55-106">Xsltc.exe aracı Visual Studio ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="7fa55-107">Daha fazla bilgi için bkz: [Visual Studio indirmeleri](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="7fa55-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa55-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7fa55-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="7fa55-109">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="7fa55-109">Argument</span></span>  
  
|<span data-ttu-id="7fa55-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="7fa55-110">Argument</span></span>|<span data-ttu-id="7fa55-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fa55-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="7fa55-112">Stil sayfasının adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="7fa55-113">Stil sayfası veya intranette bulunan bir yerel dosya olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7fa55-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="7fa55-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7fa55-114">Options</span></span>  
  
|<span data-ttu-id="7fa55-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="7fa55-115">Option</span></span>|<span data-ttu-id="7fa55-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fa55-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7fa55-117">`/c[lass]:``name`</span><span class="sxs-lookup"><span data-stu-id="7fa55-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="7fa55-118">Aşağıdaki stil sayfası sınıfın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="7fa55-119">Sınıf adı tam olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="7fa55-120">Sınıf adı varsayılan olarak stil sayfasının adı.</span><span class="sxs-lookup"><span data-stu-id="7fa55-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="7fa55-121">Örneğin, stil sayfası customers.xsl derlenmiş ise varsayılan sınıf adını müşterileri içindir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="7fa55-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="7fa55-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="7fa55-123">Hata ayıklama bilgilerini oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="7fa55-124">Belirtme `+` veya `/debug`, hata ayıklama bilgileri oluşturmak ve bir program veritabanı (PDB) dosyasında yerleştirin derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="7fa55-125">Oluşturulan PDB dosyası adı `assemblyName`.pdb.</span><span class="sxs-lookup"><span data-stu-id="7fa55-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="7fa55-126">Belirtme `-`, hangi değil belirtirseniz yürürlükte olan `/debug`, hiçbir hata ayıklama bilgisi oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="7fa55-127">Bir perakende derleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-127">A retail assembly is generated.</span></span> <span data-ttu-id="7fa55-128">**Not:** hata ayıklama modunda derleme etkileyebilecek XSLT performansı önemli ölçüde.</span><span class="sxs-lookup"><span data-stu-id="7fa55-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="7fa55-129">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7fa55-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="7fa55-130">Görüntülenmesini Derleyici telif hakkı iletisi gizler.</span><span class="sxs-lookup"><span data-stu-id="7fa55-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="7fa55-131">`/platform:``string`</span><span class="sxs-lookup"><span data-stu-id="7fa55-131">`/platform:` `string`</span></span>|<span data-ttu-id="7fa55-132">Derleme çalıştırılabilir platformları belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="7fa55-133">Geçerli platform değerleri açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="7fa55-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="7fa55-134">`x86` 32-bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılacak derlemenizi</span><span class="sxs-lookup"><span data-stu-id="7fa55-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="7fa55-135">`x64` AMD64 veya EM64T yönerge kümesi destekleyen bir bilgisayarda 64-bit ortak dil çalışma zamanı tarafından çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]<span data-ttu-id="7fa55-136"> derlemenizi olan bir bilgisayarda 64-bit ortak dil çalışma zamanı tarafından çalıştırılacak bir [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] işlemci.</span><span class="sxs-lookup"><span data-stu-id="7fa55-136"> compiles your assembly to be run by the 64-bit common language runtime on a computer that has an [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] processor.</span></span><br /><br /> <span data-ttu-id="7fa55-137">`anycpu` Herhangi bir platformda çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="7fa55-138">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="7fa55-138">This is the default.</span></span>|  
|<span data-ttu-id="7fa55-139">`/out:``assemblyName`</span><span class="sxs-lookup"><span data-stu-id="7fa55-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="7fa55-140">Çıkış bütünleştirilmiş kodun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="7fa55-141">Birden çok stil sayfaları varsa ana stil sayfası veya ilk stil sayfası adını derleme adı varsayılan olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7fa55-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="7fa55-142">Stil sayfası komut dosyaları içeriyorsa, komut dosyaları için ayrı bir derleme kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="7fa55-143">Komut dosyası derleme adları ana derleme adından üretilir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="7fa55-144">Örneğin, CustOrders.dll için derleme adınızı belirttiyseniz, ilk komut dosyası derleme CustOrders_Script1.dll olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7fa55-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="7fa55-145">`/settings:``document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="7fa55-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="7fa55-146">İzin verilip verilmeyeceğini belirtir `document()` İşlevler, XSLT komut dosyası veya belge stil sayfanızda tanımı (DTD) yazın.</span><span class="sxs-lookup"><span data-stu-id="7fa55-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="7fa55-147">DTD desteği varsayılan davranışı devre dışı bırakır `document()` işlevi ve komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="7fa55-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="7fa55-148">`@``file`</span><span class="sxs-lookup"><span data-stu-id="7fa55-148">`@` `file`</span></span>|<span data-ttu-id="7fa55-149">Derleyici seçenekleri içeren bir dosyayı belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fa55-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="7fa55-150">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7fa55-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fa55-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7fa55-151">Remarks</span></span>  
 <span data-ttu-id="7fa55-152">XSLT çözümleri birden çok stil sayfası modüllerini oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="7fa55-153">Xsltc.exe aracı derlemeleri stil sayfalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="7fa55-154">Derlemeleri sonra içine aktarılabilecek <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7fa55-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7fa55-155">Bu, bazı XSLT dağıtım senaryolarında performans maliyetleri azaltmak yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa55-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fa55-156">Uygulamanızda bir başvuru olarak derlenmiş derleme de dahil etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7fa55-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="7fa55-157">Xsltc.exe araç sınıfı doğrulamaz (`/class:``name`) veya derleme (`/out:``assemblyName`) adları.</span><span class="sxs-lookup"><span data-stu-id="7fa55-157">The xsltc.exe tool does not validate the class (`/class:``name`) or assembly (`/out:``assemblyName`) names.</span></span> <span data-ttu-id="7fa55-158">Adları geçerli değilse, hatalar ortak dil çalışma zamanı tarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="7fa55-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7fa55-159">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7fa55-159">Examples</span></span>  
 <span data-ttu-id="7fa55-160">Aşağıdaki komut, stil sayfası derler ve booksort.dll adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="7fa55-161">Aşağıdaki komut, stil sayfası derler ve bir derleme ve booksort.dll ve booksort.pdb sırasıyla adlı PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="7fa55-162">Aşağıdaki komutu bir msxsl: Script öğesi içeriyor ve calc.dll ve calc_Script1.dll adlı iki derlemeler oluşturan bir stil sayfası derler.</span><span class="sxs-lookup"><span data-stu-id="7fa55-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="7fa55-163">Aşağıdaki komut DTD işleme ve komut dosyası desteğini etkinleştirir ve myTest.dll ve myTest_Script1.dll adlı iki derlemeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="7fa55-164">Aşağıdaki komut iki stil sayfası modülleri derler ve booksort.dll adlı tek bir bütünleştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fa55-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fa55-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7fa55-165">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="7fa55-166">Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="7fa55-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [<span data-ttu-id="7fa55-167">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="7fa55-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
