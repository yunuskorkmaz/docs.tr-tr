---
description: 'Daha fazla bilgi edinin: XSLT derleyicisi (xsltc.exe)'
title: XSLT Derleyicisi (xsltc.exe)
ms.date: 03/30/2017
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
ms.openlocfilehash: 96236e7a7c985c4a71c2f09ffd3ad720bb3d40f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782552"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="4aaf7-103">XSLT Derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="4aaf7-103">XSLT Compiler (xsltc.exe)</span></span>

<span data-ttu-id="4aaf7-104">XSLT derleyicisi (xsltc.exe) XSLT stil sayfalarını derler ve bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-104">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="4aaf7-105">Derlenmiş stil sayfası daha sonra doğrudan <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-105">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4aaf7-106">xsltc.exe ile imzalı derlemeler oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-106">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="4aaf7-107">xsltc.exe aracı Visual Studio 'Ya dahildir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-107">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="4aaf7-108">Daha fazla bilgi için bkz. [Visual Studio İndirmeleri](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="4aaf7-108">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aaf7-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="4aaf7-109">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="4aaf7-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="4aaf7-110">Argument</span></span>  
  
|<span data-ttu-id="4aaf7-111">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="4aaf7-111">Argument</span></span>|<span data-ttu-id="4aaf7-112">Description</span><span class="sxs-lookup"><span data-stu-id="4aaf7-112">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="4aaf7-113">Stil sayfasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-113">Specifies the name of the style sheet.</span></span> <span data-ttu-id="4aaf7-114">Stil sayfası yerel bir dosya olmalıdır veya intranette bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-114">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="4aaf7-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4aaf7-115">Options</span></span>  
  
|<span data-ttu-id="4aaf7-116">Seçenek</span><span class="sxs-lookup"><span data-stu-id="4aaf7-116">Option</span></span>|<span data-ttu-id="4aaf7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4aaf7-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4aaf7-118">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="4aaf7-118">`/c[lass]:` `name`</span></span>|<span data-ttu-id="4aaf7-119">Aşağıdaki stil sayfası için sınıfın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-119">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="4aaf7-120">Sınıf adı tam olarak nitelenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-120">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="4aaf7-121">Sınıf adı varsayılan olarak stil sayfasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-121">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="4aaf7-122">Örneğin, Customers. xsl stil sayfası derlenmişse, varsayılan sınıf adı müşteriler olur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-122">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="4aaf7-123">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="4aaf7-123">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="4aaf7-124">Hata ayıklama bilgilerinin oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-124">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="4aaf7-125">`+`Veya belirtildiğinde `/debug` , derleyicinin hata ayıklama bilgileri oluşturmasına ve bir program VERITABANı (pdb) dosyasına yerleştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-125">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="4aaf7-126">Oluşturulan PDB dosyasının adı `assemblyName` . pdb 'dir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-126">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="4aaf7-127">`-`Belirtmiyorsanız geçerli olan öğesini belirtme `/debug` , hiçbir hata ayıklama bilgisinin oluşturulmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-127">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="4aaf7-128">Bir perakende derlemesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-128">A retail assembly is generated.</span></span> <span data-ttu-id="4aaf7-129">**Note:**  Hata ayıklama modunda derleme, XSLT performansını önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-129">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="4aaf7-130">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-130">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="4aaf7-131">Derleyicinin telif hakkı iletisinin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-131">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="4aaf7-132">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="4aaf7-132">`/platform:` `string`</span></span>|<span data-ttu-id="4aaf7-133">Derlemenin çalıştırılabilen platformları belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-133">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="4aaf7-134">Geçerli platform değerlerini aşağıda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="4aaf7-134">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="4aaf7-135">`x86` derlemenizi 32 bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler</span><span class="sxs-lookup"><span data-stu-id="4aaf7-135">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="4aaf7-136">`x64` , derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-136">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="4aaf7-137">Itanium, derlemenizi Itanium işlemcisine sahip bir bilgisayarda 64 bitlik ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-137">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="4aaf7-138">`anycpu` derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-138">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="4aaf7-139">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-139">This is the default.</span></span>|  
|<span data-ttu-id="4aaf7-140">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="4aaf7-140">`/out:` `assemblyName`</span></span>|<span data-ttu-id="4aaf7-141">Çıktı olan derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-141">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="4aaf7-142">Birden çok stil sayfası varsa, derleme adı varsayılan olarak ana stil sayfasının adı veya ilk stil sayfası olur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-142">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="4aaf7-143">Stil sayfası betikler içeriyorsa, betikler ayrı bir derlemeye kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-143">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="4aaf7-144">Betik derleme adları ana derleme adından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-144">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="4aaf7-145">Örneğin, derleme adınız için CustOrders.dll belirttiyseniz, ilk betik derlemesi CustOrders_Script1.dll olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-145">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="4aaf7-146">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="4aaf7-146">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="4aaf7-147">`document()`Stil sayfasında işlevlere, XSLT betiğine veya belge türü tanımına (DTD) izin verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-147">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="4aaf7-148">Varsayılan davranış DTD, `document()` işlev ve komut dosyası desteğini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-148">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="4aaf7-149">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="4aaf7-149">`@` `file`</span></span>|<span data-ttu-id="4aaf7-150">Derleyici seçeneklerini içeren bir dosya belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-150">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="4aaf7-151">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-151">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aaf7-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4aaf7-152">Remarks</span></span>  

 <span data-ttu-id="4aaf7-153">XSLT çözümleri, birden çok stil sayfası modülünden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-153">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="4aaf7-154">xsltc.exe Aracı, stil sayfalarından derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-154">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="4aaf7-155">Daha sonra derlemeler <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-155">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4aaf7-156">Bu, bazı XSLT dağıtım senaryolarında performans maliyetlerinin azaltılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-156">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4aaf7-157">Derlenen derlemeyi uygulamanıza başvuru olarak da dahil etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-157">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="4aaf7-158">xsltc.exe Aracı, Sınıf ( `/class:` *ad*) veya derleme ( `/out:` *AssemblyName*) adlarını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-158">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="4aaf7-159">Adlar geçerli değilse, ortak dil çalışma zamanı tarafından hatalar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-159">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4aaf7-160">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4aaf7-160">Examples</span></span>  

 <span data-ttu-id="4aaf7-161">Aşağıdaki komut, stil sayfasını derler ve booksort.dll adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-161">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="4aaf7-162">Aşağıdaki komut stil sayfasını derler ve sırasıyla booksort.dll ve booksort. pdb adlı bir derleme ve PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-162">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="4aaf7-163">Aşağıdaki komut bir msxsl: script öğesi içeren bir stil sayfasını derler ve calc.dll ve calc_Script1.dll adlı iki derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-163">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="4aaf7-164">Aşağıdaki komut DTD işleme ve betik desteğini sunar ve myTest.dll ve myTest_Script1.dll adlı iki derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-164">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="4aaf7-165">Aşağıdaki komut iki stil sayfası modülünü derler ve booksort.dll adlı tek bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-165">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="4aaf7-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aaf7-166">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="4aaf7-167">Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4aaf7-167">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="4aaf7-168">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="4aaf7-168">XSLT Transformations</span></span>](xslt-transformations.md)
