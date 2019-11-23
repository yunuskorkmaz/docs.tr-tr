---
title: XSLT Derleyicisi (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 729e6caa36ed8c2f6e77153f8d8ae356513b0603
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956990"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="42f16-102">XSLT Derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="42f16-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="42f16-103">XSLT derleyicisi (xsltc. exe) XSLT stil sayfalarını derler ve bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42f16-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="42f16-104">Derlenmiş stil sayfası daha sonra doğrudan <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="42f16-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42f16-105">Xsltc. exe ile imzalı derlemeler oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="42f16-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="42f16-106">Xsltc. exe aracı, Visual Studio 'Ya dahildir.</span><span class="sxs-lookup"><span data-stu-id="42f16-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="42f16-107">Daha fazla bilgi için bkz. [Visual Studio İndirmeleri](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="42f16-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f16-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42f16-108">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="42f16-109">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="42f16-109">Argument</span></span>  
  
|<span data-ttu-id="42f16-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="42f16-110">Argument</span></span>|<span data-ttu-id="42f16-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42f16-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="42f16-112">Stil sayfasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42f16-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="42f16-113">Stil sayfası yerel bir dosya olmalıdır veya intranette bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="42f16-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="42f16-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="42f16-114">Options</span></span>  
  
|<span data-ttu-id="42f16-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="42f16-115">Option</span></span>|<span data-ttu-id="42f16-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42f16-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="42f16-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="42f16-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="42f16-118">Aşağıdaki stil sayfası için sınıfın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42f16-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="42f16-119">Sınıf adı tam olarak nitelenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="42f16-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="42f16-120">Sınıf adı varsayılan olarak stil sayfasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="42f16-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="42f16-121">Örneğin, Customers. xsl stil sayfası derlenmişse, varsayılan sınıf adı müşteriler olur.</span><span class="sxs-lookup"><span data-stu-id="42f16-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="42f16-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="42f16-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="42f16-123">Hata ayıklama bilgilerinin oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42f16-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="42f16-124">`+` veya `/debug`belirtme, derleyicinin hata ayıklama bilgileri oluşturmasına ve bir program veritabanı (PDB) dosyasına yerleştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="42f16-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="42f16-125">Oluşturulan PDB dosyasının adı `assemblyName`. pdb ' dir.</span><span class="sxs-lookup"><span data-stu-id="42f16-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="42f16-126">`-`belirtme `/debug`belirtmezseniz, herhangi bir hata ayıklama bilgisinin oluşturulmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="42f16-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="42f16-127">Bir perakende derlemesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42f16-127">A retail assembly is generated.</span></span> <span data-ttu-id="42f16-128">**Note:**  Hata ayıklama modunda derleme, XSLT performansını önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="42f16-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="42f16-129">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42f16-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="42f16-130">Derleyicinin telif hakkı iletisinin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="42f16-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="42f16-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="42f16-131">`/platform:` `string`</span></span>|<span data-ttu-id="42f16-132">Derlemenin çalıştırılabilen platformları belirtir.</span><span class="sxs-lookup"><span data-stu-id="42f16-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="42f16-133">Geçerli platform değerlerini aşağıda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="42f16-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="42f16-134">`x86`, derlemenizi 32 bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler</span><span class="sxs-lookup"><span data-stu-id="42f16-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="42f16-135">`x64`, derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="42f16-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="42f16-136">Itanium, derlemenizi Itanium işlemcisine sahip bir bilgisayarda 64 bitlik ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="42f16-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="42f16-137">`anycpu`, derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="42f16-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="42f16-138">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="42f16-138">This is the default.</span></span>|  
|<span data-ttu-id="42f16-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="42f16-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="42f16-140">Çıktı olan derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42f16-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="42f16-141">Birden çok stil sayfası varsa, derleme adı varsayılan olarak ana stil sayfasının adı veya ilk stil sayfası olur.</span><span class="sxs-lookup"><span data-stu-id="42f16-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="42f16-142">Stil sayfası betikler içeriyorsa, betikler ayrı bir derlemeye kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="42f16-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="42f16-143">Betik derleme adları ana derleme adından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42f16-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="42f16-144">Örneğin, derleme adınız için CustOrders. dll ' yi belirttiyseniz, ilk betik derlemesi CustOrders_Script1. dll olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="42f16-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="42f16-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="42f16-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="42f16-146">Stil sayfasında `document()` işlevlere, XSLT betiğine veya belge türü tanımına (DTD) izin verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42f16-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="42f16-147">Varsayılan davranış DTD desteğini devre dışı bırakır, `document()` işlevi ve komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="42f16-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="42f16-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="42f16-148">`@` `file`</span></span>|<span data-ttu-id="42f16-149">Derleyici seçeneklerini içeren bir dosya belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="42f16-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="42f16-150">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42f16-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42f16-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42f16-151">Remarks</span></span>  
 <span data-ttu-id="42f16-152">XSLT çözümleri, birden çok stil sayfası modülünden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="42f16-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="42f16-153">Xsltc. exe aracı, stil sayfalarından derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42f16-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="42f16-154">Daha sonra derlemeler <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="42f16-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42f16-155">Bu, bazı XSLT dağıtım senaryolarında performans maliyetlerinin azaltılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="42f16-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42f16-156">Derlenen derlemeyi uygulamanıza başvuru olarak da dahil etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="42f16-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="42f16-157">Xsltc. exe aracı, Sınıf (`/class:`*adı*) veya derleme (`/out:`*AssemblyName*) adlarını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="42f16-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="42f16-158">Adlar geçerli değilse, ortak dil çalışma zamanı tarafından hatalar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42f16-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="42f16-159">Örnekler</span><span class="sxs-lookup"><span data-stu-id="42f16-159">Examples</span></span>  
 <span data-ttu-id="42f16-160">Aşağıdaki komut, stil sayfasını derler ve booksort. dll adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42f16-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="42f16-161">Aşağıdaki komut, stil sayfasını derler ve sırasıyla booksort. dll ve booksort. pdb adlı bir derleme ve PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42f16-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="42f16-162">Aşağıdaki komut bir msxsl: script öğesi içeren bir stil sayfasını derler ve calc. dll ve calc_Script1. dll adlı iki derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42f16-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="42f16-163">Aşağıdaki komut DTD işleme ve betik desteğini sunar ve myTest. dll ve myTest_Script1. dll adlı iki derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42f16-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="42f16-164">Aşağıdaki komut iki stil sayfası modülünü derler ve booksort. dll adlı tek bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42f16-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="42f16-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42f16-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="42f16-166">Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="42f16-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="42f16-167">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="42f16-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
