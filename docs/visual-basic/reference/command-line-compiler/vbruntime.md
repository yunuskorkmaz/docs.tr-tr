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
ms.openlocfilehash: a1988fcd19c6629d85ae0e739681fd39fe033c0d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843870"
---
# <a name="-vbruntime"></a><span data-ttu-id="c75f0-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="c75f0-102">-vbruntime</span></span>
<span data-ttu-id="c75f0-103">Derleyici, Visual Basic çalışma zamanı kitaplığı veya bir belirli çalışma zamanı kitaplık başvurusu olan bir başvuru olmadan derlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c75f0-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c75f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c75f0-104">Syntax</span></span>  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="c75f0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c75f0-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="c75f0-106">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin.</span><span class="sxs-lookup"><span data-stu-id="c75f0-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="c75f0-107">Varsayılan Visual Basic çalışma zamanı kitaplığı başvurusu ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="c75f0-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="c75f0-108">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin ve Visual Basic Çalışma Zamanı Kitaplığı'ndan derleme çekirdek işlevselliği ekleme.</span><span class="sxs-lookup"><span data-stu-id="c75f0-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="c75f0-109">Belirtilen kitaplık (DLL) başvuru ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="c75f0-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c75f0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c75f0-110">Remarks</span></span>  
 <span data-ttu-id="c75f0-111">`-vbruntime` Derleyici seçeneği derleyici Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derlemesi gerektiğini belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="c75f0-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="c75f0-112">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleme yaparsanız, hatalar veya uyarılar bir Visual Basic çalışma zamanı yardımcı çağrısı oluşturan kodu veya dil yapıları üzerinde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c75f0-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="c75f0-113">(A *Visual Basic çalışma zamanı Yardımcısı* anlam belirli bir dil yürütmek için çalışma zamanında çağrılan Microsoft.VisualBasic.dll içinde tanımlanan bir işlevdir.)</span><span class="sxs-lookup"><span data-stu-id="c75f0-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="c75f0-114">`-vbruntime+` Seçeneği Hayır ise oluşan aynı davranışı üretir `-vbruntime` anahtarı belirtiliyor.</span><span class="sxs-lookup"><span data-stu-id="c75f0-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="c75f0-115">Kullanabileceğiniz `-vbruntime+` önceki geçersiz kılmak için seçeneği `-vbruntime` anahtarlar.</span><span class="sxs-lookup"><span data-stu-id="c75f0-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="c75f0-116">Çoğu nesnelerin `My` türü, kullandığınızda kullanılamaz `-vbruntime-` veya `-vbruntime:path` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="c75f0-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="c75f0-117">Visual Basic çalışma zamanı çekirdek işlevselliği ekleme</span><span class="sxs-lookup"><span data-stu-id="c75f0-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="c75f0-118">`-vbruntime*` Seçeneği bir çalışma zamanı kitaplığı başvurusu olmadan derleme olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c75f0-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="c75f0-119">Bunun yerine, Visual Basic Çalışma Zamanı Kitaplığı'ndaki çekirdek işlevselliğini kullanıcı derlemesinde katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="c75f0-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="c75f0-120">Visual Basic çalışma zamanı içermeyen platformlarda uygulamanız çalışıyorsa, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c75f0-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="c75f0-121">Aşağıdaki çalışma zamanı üyeleri bir parçasıdır:</span><span class="sxs-lookup"><span data-stu-id="c75f0-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="c75f0-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="c75f0-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="c75f0-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c75f0-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="c75f0-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c75f0-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="c75f0-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c75f0-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="c75f0-126"><xref:Microsoft.VisualBasic.Constants.vbBack> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="c75f0-127"><xref:Microsoft.VisualBasic.Constants.vbCr> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="c75f0-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="c75f0-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="c75f0-130"><xref:Microsoft.VisualBasic.Constants.vbLf> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="c75f0-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="c75f0-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="c75f0-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="c75f0-134"><xref:Microsoft.VisualBasic.Constants.vbTab> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="c75f0-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Sabit</span><span class="sxs-lookup"><span data-stu-id="c75f0-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="c75f0-136">Bazı nesneler `My` türü</span><span class="sxs-lookup"><span data-stu-id="c75f0-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="c75f0-137">Kullanarak derleme yaparsanız `-vbruntime*` seçeneği ve kodunuzu çekirdek işlevselliği gömülü Visual Basic Çalışma Zamanı Kitaplığı'ndan bir üye başvuruyor, derleyici üyesi kullanılabilir olmadığını belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="c75f0-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="c75f0-138">Belirtilen kitaplık başvurma</span><span class="sxs-lookup"><span data-stu-id="c75f0-138">Referencing a specified library</span></span>  
 <span data-ttu-id="c75f0-139">Kullanabileceğiniz `path` bir Visual Basic çalışma zamanı kitaplığı varsayılan yerine özel çalışma zamanı kitaplık başvurusu olan derlemek için bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="c75f0-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="c75f0-140">Varsa değerini `path` bağımsız değişkeni bir dll dosyasının tam yolu, derleyici bu dosyayı çalışma zamanı kitaplığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c75f0-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="c75f0-141">Varsa değerini `path` bağımsız değişkeni bir tam bir DLL yolu değil, Visual Basic Derleyicisi geçerli klasörde belirtilen DLL için ilk arama yapar.</span><span class="sxs-lookup"><span data-stu-id="c75f0-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="c75f0-142">Ardından kullanılarak belirtilen yolda arar [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c75f0-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="c75f0-143">Varsa `-sdkpath` derleyici seçeneği kullanılmazsa, derleyici, .NET Framework klasöründe tanımlanmış DLL için arama yapar (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="c75f0-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c75f0-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="c75f0-144">Example</span></span>  
 <span data-ttu-id="c75f0-145">Aşağıdaki örnek nasıl kullanılacağını gösterir `-vbruntime` özel bir kitaplığa bir başvuru ile derlemek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c75f0-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="c75f0-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c75f0-146">See also</span></span>

- [<span data-ttu-id="c75f0-147">Visual Basic çekirdek – Visual Studio 2010 SP1'de yeni derleme modu</span><span class="sxs-lookup"><span data-stu-id="c75f0-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="c75f0-148">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="c75f0-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c75f0-149">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="c75f0-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="c75f0-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="c75f0-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
