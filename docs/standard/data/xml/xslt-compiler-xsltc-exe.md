---
title: XSLT derleyicisi (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 470dd0eb37d8081d388ef69b204293f568096a5e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44364786"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="29632-102">XSLT derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="29632-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="29632-103">XSLT derleyicisi (xsltc.exe) XSLT stil sayfalarını derler ve bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29632-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="29632-104">Derlenmiş bir stil sayfası sonra doğrudan geçirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="29632-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="29632-105">İmzalı derlemeler xsltc.exe ile oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="29632-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="29632-106">Xsltc.exe aracı Visual Studio ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="29632-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="29632-107">Daha fazla bilgi için [Visual Studio indirmeleri](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="29632-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29632-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29632-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="29632-109">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="29632-109">Argument</span></span>  
  
|<span data-ttu-id="29632-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="29632-110">Argument</span></span>|<span data-ttu-id="29632-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29632-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="29632-112">Stil sayfası adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29632-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="29632-113">Stil sayfası, yerel bir dosya olmalıdır veya intranette yer.</span><span class="sxs-lookup"><span data-stu-id="29632-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="29632-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="29632-114">Options</span></span>  
  
|<span data-ttu-id="29632-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="29632-115">Option</span></span>|<span data-ttu-id="29632-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29632-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="29632-117">`/c[lass]:``name`</span><span class="sxs-lookup"><span data-stu-id="29632-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="29632-118">Aşağıdaki stil sayfası için sınıfın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29632-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="29632-119">Sınıf adı, tam olabilir.</span><span class="sxs-lookup"><span data-stu-id="29632-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="29632-120">Sınıf adı, stil sayfası adını varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="29632-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="29632-121">Örneğin, stil sayfası customers.xsl derlenirse, varsayılan sınıf adını Müşteriler ' dir.</span><span class="sxs-lookup"><span data-stu-id="29632-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="29632-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="29632-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="29632-123">Hata ayıklama bilgilerini oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29632-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="29632-124">Belirtme `+` veya `/debug`, derleyicinin hata ayıklama bilgileri üret ve program veritabanı (PDB) dosyası içinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="29632-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="29632-125">Oluşturulan PDB dosyası adıdır `assemblyName`.pdb.</span><span class="sxs-lookup"><span data-stu-id="29632-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="29632-126">Belirtme `-`, hangi belirtmezseniz, geçerli olduğu `/debug`, oluşturulacak hata ayıklama bilgisi yok neden olur.</span><span class="sxs-lookup"><span data-stu-id="29632-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="29632-127">Bir perakende derleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29632-127">A retail assembly is generated.</span></span> <span data-ttu-id="29632-128">**Not:** hata ayıklama modunda derleme etkileyebilir XSLT performansı önemli ölçüde.</span><span class="sxs-lookup"><span data-stu-id="29632-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="29632-129">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="29632-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="29632-130">Derleyici telif hakkı iletisini görüntülenmesini bastırır.</span><span class="sxs-lookup"><span data-stu-id="29632-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="29632-131">`/platform:``string`</span><span class="sxs-lookup"><span data-stu-id="29632-131">`/platform:` `string`</span></span>|<span data-ttu-id="29632-132">Derleme çalıştırılabileceği platformları belirtir.</span><span class="sxs-lookup"><span data-stu-id="29632-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="29632-133">Geçerli platform değerleri açıklar:</span><span class="sxs-lookup"><span data-stu-id="29632-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="29632-134">`x86` derlemenizi 32-bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılmak üzere</span><span class="sxs-lookup"><span data-stu-id="29632-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="29632-135">`x64` derlemenizi 64 bit ortak dil çalışma zamanı tarafından AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda çalıştırılması için derler.</span><span class="sxs-lookup"><span data-stu-id="29632-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]<span data-ttu-id="29632-136"> derlemenizi 64 bit ortak dil çalışma zamanı tarafından olan bir bilgisayarda çalıştırılması için bir [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] işlemci.</span><span class="sxs-lookup"><span data-stu-id="29632-136"> compiles your assembly to be run by the 64-bit common language runtime on a computer that has an [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] processor.</span></span><br /><br /> <span data-ttu-id="29632-137">`anycpu` Herhangi bir platform üzerinde çalıştırmasını derlemenizin derler.</span><span class="sxs-lookup"><span data-stu-id="29632-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="29632-138">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="29632-138">This is the default.</span></span>|  
|<span data-ttu-id="29632-139">`/out:``assemblyName`</span><span class="sxs-lookup"><span data-stu-id="29632-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="29632-140">Çıkış derlemesi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29632-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="29632-141">Birden çok stil sayfaları varsa ana stil sayfası veya ilk stil sayfası adı için varsayılan derleme adı içerir.</span><span class="sxs-lookup"><span data-stu-id="29632-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="29632-142">Betikleri stil sayfası içeriyorsa, komut dosyaları için ayrı bir derleme kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="29632-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="29632-143">Komut dosyası derleme adları ana derleme adından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="29632-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="29632-144">Örneğin, derleme adınız için CustOrders.dll belirttiyseniz, ilk betik derleme CustOrders_Script1.dll olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="29632-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="29632-145">`/settings:``document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="29632-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="29632-146">İzin verilip verilmeyeceğini belirten `document()` işlevleri, XSLT betik veya belge stil sayfası içinde tür tanımı (DTD'nin).</span><span class="sxs-lookup"><span data-stu-id="29632-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="29632-147">DTD desteği varsayılan davranışı devre dışı bırakır `document()` işlev ve betik oluşturma.</span><span class="sxs-lookup"><span data-stu-id="29632-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="29632-148">`@``file`</span><span class="sxs-lookup"><span data-stu-id="29632-148">`@` `file`</span></span>|<span data-ttu-id="29632-149">Derleyici seçenekleri içeren bir dosya belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="29632-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="29632-150">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="29632-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29632-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29632-151">Remarks</span></span>  
 <span data-ttu-id="29632-152">XSLT çözümleri birden çok stil sayfası modüllerini oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="29632-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="29632-153">Xsltc.exe araç derlemeleri stil sayfası içinden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29632-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="29632-154">Derlemeleri ardından uygulamasına geçirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="29632-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="29632-155">Bu, bazı XSLT dağıtım senaryolarında performans maliyetleri azaltma yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="29632-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29632-156">Uygulamanızda bir başvuru olarak derlenmiş derlemenin de dahil etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="29632-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="29632-157">Xsltc.exe araç, sınıf doğrulamaz (`/class:``name`) veya derleme (`/out:``assemblyName`) adları.</span><span class="sxs-lookup"><span data-stu-id="29632-157">The xsltc.exe tool does not validate the class (`/class:``name`) or assembly (`/out:``assemblyName`) names.</span></span> <span data-ttu-id="29632-158">Adları geçerli değilse, hatalar ortak dil çalışma zamanı tarafından atılır.</span><span class="sxs-lookup"><span data-stu-id="29632-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="29632-159">Örnekler</span><span class="sxs-lookup"><span data-stu-id="29632-159">Examples</span></span>  
 <span data-ttu-id="29632-160">Aşağıdaki komut, stil sayfası derler ve booksort.dll adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29632-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="29632-161">Aşağıdaki komut, stil sayfası derler ve bir derleme ve booksort.dll ve booksort.pdb sırasıyla adlı PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29632-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="29632-162">Aşağıdaki komutu bir msxsl: Script öğesi içeriyor ve calc.dll ve calc_Script1.dll adlı iki derlemeler oluşturan bir stil sayfası derler.</span><span class="sxs-lookup"><span data-stu-id="29632-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="29632-163">Aşağıdaki komut, DTD işleme ve komut dosyası desteği sağlar ve myTest.dll ve myTest_Script1.dll adlı iki derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29632-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="29632-164">Aşağıdaki komut, iki stil sayfası modülleri derler ve booksort.dll adlı tek bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29632-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="29632-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29632-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [<span data-ttu-id="29632-166">Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="29632-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
- [<span data-ttu-id="29632-167">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="29632-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
