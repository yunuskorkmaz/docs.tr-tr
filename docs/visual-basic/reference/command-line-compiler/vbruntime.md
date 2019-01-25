---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: 88a7a74eac5a27cdf473e161a8ffdb59c1eb9ab2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674563"
---
# <a name="-vbruntime"></a><span data-ttu-id="119de-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="119de-102">-vbruntime</span></span>
<span data-ttu-id="119de-103">Derleyici, Visual Basic çalışma zamanı kitaplığı veya bir belirli çalışma zamanı kitaplık başvurusu olan bir başvuru olmadan derlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="119de-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="119de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="119de-104">Syntax</span></span>  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="119de-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="119de-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="119de-106">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin.</span><span class="sxs-lookup"><span data-stu-id="119de-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="119de-107">Varsayılan Visual Basic çalışma zamanı kitaplığı başvurusu ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="119de-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="119de-108">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin ve Visual Basic Çalışma Zamanı Kitaplığı'ndan derleme çekirdek işlevselliği ekleme.</span><span class="sxs-lookup"><span data-stu-id="119de-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="119de-109">Belirtilen kitaplık (DLL) başvuru ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="119de-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="119de-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="119de-110">Remarks</span></span>  
 <span data-ttu-id="119de-111">`-vbruntime` Derleyici seçeneği derleyici Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derlemesi gerektiğini belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="119de-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="119de-112">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleme yaparsanız, hatalar veya uyarılar bir Visual Basic çalışma zamanı yardımcı çağrısı oluşturan kodu veya dil yapıları üzerinde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="119de-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="119de-113">(A *Visual Basic çalışma zamanı Yardımcısı* anlam belirli bir dil yürütmek için çalışma zamanında çağrılan Microsoft.VisualBasic.dll içinde tanımlanan bir işlevdir.)</span><span class="sxs-lookup"><span data-stu-id="119de-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="119de-114">`-vbruntime+` Seçeneği Hayır ise oluşan aynı davranışı üretir `-vbruntime` anahtarı belirtiliyor.</span><span class="sxs-lookup"><span data-stu-id="119de-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="119de-115">Kullanabileceğiniz `-vbruntime+` önceki geçersiz kılmak için seçeneği `-vbruntime` anahtarlar.</span><span class="sxs-lookup"><span data-stu-id="119de-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="119de-116">Çoğu nesnelerin `My` türü, kullandığınızda kullanılamaz `-vbruntime-` veya `-vbruntime:path` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="119de-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="119de-117">Visual Basic çalışma zamanı çekirdek işlevselliği ekleme</span><span class="sxs-lookup"><span data-stu-id="119de-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="119de-118">`-vbruntime*` Seçeneği bir çalışma zamanı kitaplığı başvurusu olmadan derleme olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="119de-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="119de-119">Bunun yerine, Visual Basic Çalışma Zamanı Kitaplığı'ndaki çekirdek işlevselliğini kullanıcı derlemesinde katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="119de-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="119de-120">Visual Basic çalışma zamanı içermeyen platformlarda uygulamanız çalışıyorsa, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="119de-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="119de-121">Aşağıdaki çalışma zamanı üyeleri bir parçasıdır:</span><span class="sxs-lookup"><span data-stu-id="119de-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="119de-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="119de-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="119de-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="119de-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="119de-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="119de-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="119de-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="119de-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="119de-126"><xref:Microsoft.VisualBasic.Constants.vbBack> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="119de-127"><xref:Microsoft.VisualBasic.Constants.vbCr> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="119de-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="119de-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="119de-130"><xref:Microsoft.VisualBasic.Constants.vbLf> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="119de-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="119de-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="119de-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="119de-134"><xref:Microsoft.VisualBasic.Constants.vbTab> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="119de-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Sabit</span><span class="sxs-lookup"><span data-stu-id="119de-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="119de-136">Bazı nesneler `My` türü</span><span class="sxs-lookup"><span data-stu-id="119de-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="119de-137">Kullanarak derleme yaparsanız `-vbruntime*` seçeneği ve kodunuzu çekirdek işlevselliği gömülü Visual Basic Çalışma Zamanı Kitaplığı'ndan bir üye başvuruyor, derleyici üyesi kullanılabilir olmadığını belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="119de-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="119de-138">Belirtilen kitaplık başvurma</span><span class="sxs-lookup"><span data-stu-id="119de-138">Referencing a specified library</span></span>  
 <span data-ttu-id="119de-139">Kullanabileceğiniz `path` bir Visual Basic çalışma zamanı kitaplığı varsayılan yerine özel çalışma zamanı kitaplık başvurusu olan derlemek için bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="119de-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="119de-140">Varsa değerini `path` bağımsız değişkeni bir dll dosyasının tam yolu, derleyici bu dosyayı çalışma zamanı kitaplığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="119de-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="119de-141">Varsa değerini `path` bağımsız değişkeni bir tam bir DLL yolu değil, Visual Basic Derleyicisi geçerli klasörde belirtilen DLL için ilk arama yapar.</span><span class="sxs-lookup"><span data-stu-id="119de-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="119de-142">Ardından kullanılarak belirtilen yolda arar [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="119de-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="119de-143">Varsa `-sdkpath` derleyici seçeneği kullanılmazsa, derleyici, .NET Framework klasöründe tanımlanmış DLL için arama yapar (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="119de-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="119de-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="119de-144">Example</span></span>  
 <span data-ttu-id="119de-145">Aşağıdaki örnek nasıl kullanılacağını gösterir `-vbruntime` özel bir kitaplığa bir başvuru ile derlemek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="119de-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="119de-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="119de-146">See also</span></span>
- [<span data-ttu-id="119de-147">Visual Basic çekirdek – Visual Studio 2010 SP1'de yeni derleme modu</span><span class="sxs-lookup"><span data-stu-id="119de-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)
- [<span data-ttu-id="119de-148">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="119de-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="119de-149">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="119de-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="119de-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="119de-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
