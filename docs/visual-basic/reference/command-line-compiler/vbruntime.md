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
ms.openlocfilehash: 8c7789c6af7b82ecb40ecd73d09f64aa1da3fd4b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005059"
---
# <a name="-vbruntime"></a><span data-ttu-id="8adec-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="8adec-102">-vbruntime</span></span>
<span data-ttu-id="8adec-103">Derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan veya belirli bir çalışma zamanı kitaplığı başvurusuyla derlenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adec-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8adec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8adec-104">Syntax</span></span>  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="8adec-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="8adec-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="8adec-106">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin.</span><span class="sxs-lookup"><span data-stu-id="8adec-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="8adec-107">Varsayılan Visual Basic çalışma zamanı kitaplığı başvurusuyla derleyin.</span><span class="sxs-lookup"><span data-stu-id="8adec-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="8adec-108">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin ve temel işlevselliği Visual Basic çalışma zamanı kitaplığından derlemeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8adec-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="8adec-109">Belirtilen kitaplığa (DLL) bir başvuru ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="8adec-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8adec-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8adec-110">Remarks</span></span>  
 <span data-ttu-id="8adec-111">@No__t-0 derleyici seçeneği, derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan derlenmesi gerektiğini belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8adec-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="8adec-112">Visual Basic çalışma zamanı kitaplığına başvuru olmadan derlerseniz, hatalar veya uyarılar bir Visual Basic çalışma zamanı Yardımcısı çağrısı üreten kod veya dil yapılarında günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="8adec-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="8adec-113">( *Visual Basic çalışma zamanı Yardımcısı* , belirli bir dil anlam yürütmesi yürütmek için çalışma zamanında çağrılan Microsoft. VisualBasic. dll ' de tanımlanan bir işlevdir.)</span><span class="sxs-lookup"><span data-stu-id="8adec-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="8adec-114">@No__t-0 seçeneği, hiçbir `-vbruntime` anahtarı belirtilmemişse oluşan aynı davranışı üretir.</span><span class="sxs-lookup"><span data-stu-id="8adec-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="8adec-115">Önceki `-vbruntime` anahtarlarını geçersiz kılmak için `-vbruntime+` seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adec-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="8adec-116">@No__t-0 türündeki nesnelerin çoğu, `-vbruntime-` veya `-vbruntime:path` seçeneklerini kullandığınızda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8adec-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="8adec-117">Visual Basic çalışma zamanı temel işlevlerini katıştırma</span><span class="sxs-lookup"><span data-stu-id="8adec-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="8adec-118">@No__t-0 seçeneği, bir çalışma zamanı kitaplığı başvurusu olmadan derlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8adec-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="8adec-119">Bunun yerine, Visual Basic çalışma zamanı kitaplığındaki çekirdek işlevsellik Kullanıcı derlemesine katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="8adec-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="8adec-120">Uygulamanız Visual Basic çalışma zamanı içermeyen platformlarda çalışıyorsa, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adec-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="8adec-121">Aşağıdaki çalışma zamanı üyeleri katıştırılır:</span><span class="sxs-lookup"><span data-stu-id="8adec-121">The following runtime members are embedded:</span></span>  
  
- <span data-ttu-id="8adec-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> sınıfı</span><span class="sxs-lookup"><span data-stu-id="8adec-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
- <span data-ttu-id="8adec-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> yöntemi</span><span class="sxs-lookup"><span data-stu-id="8adec-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
- <span data-ttu-id="8adec-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> yöntemi</span><span class="sxs-lookup"><span data-stu-id="8adec-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
- <span data-ttu-id="8adec-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> yöntemi</span><span class="sxs-lookup"><span data-stu-id="8adec-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
- <span data-ttu-id="8adec-126"><xref:Microsoft.VisualBasic.Constants.vbBack> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
- <span data-ttu-id="8adec-127"><xref:Microsoft.VisualBasic.Constants.vbCr> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
- <span data-ttu-id="8adec-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
- <span data-ttu-id="8adec-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
- <span data-ttu-id="8adec-130"><xref:Microsoft.VisualBasic.Constants.vbLf> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
- <span data-ttu-id="8adec-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
- <span data-ttu-id="8adec-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
- <span data-ttu-id="8adec-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
- <span data-ttu-id="8adec-134"><xref:Microsoft.VisualBasic.Constants.vbTab> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
- <span data-ttu-id="8adec-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> sabiti</span><span class="sxs-lookup"><span data-stu-id="8adec-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
- <span data-ttu-id="8adec-136">@No__t-0 türündeki bazı nesneler</span><span class="sxs-lookup"><span data-stu-id="8adec-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="8adec-137">@No__t-0 seçeneğini kullanarak derlerseniz ve kodunuz çekirdek işlevlerle gömülü olmayan Visual Basic çalışma zamanı kitaplığından bir üyeye başvuruyorsa, derleyici üyenin kullanılabilir olmadığını belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="8adec-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="8adec-138">Belirtilen bir kitaplığa başvurma</span><span class="sxs-lookup"><span data-stu-id="8adec-138">Referencing a specified library</span></span>  
 <span data-ttu-id="8adec-139">Varsayılan Visual Basic çalışma zamanı kitaplığı yerine özel bir çalışma zamanı kitaplığı başvurusuyla derlemek için `path` bağımsız değişkenini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adec-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="8adec-140">@No__t-0 bağımsız değişkeninin değeri bir DLL 'nin tam yolu ise, derleyici bu dosyayı çalışma zamanı kitaplığı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="8adec-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="8adec-141">@No__t-0 bağımsız değişkeninin değeri bir DLL 'nin tam yolu değilse, Visual Basic Derleyicisi önce geçerli klasörde tanımlanan DLL 'yi arar.</span><span class="sxs-lookup"><span data-stu-id="8adec-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="8adec-142">Daha sonra [-SdkPath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) derleyici seçeneğini kullanarak belirttiğiniz yolda arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="8adec-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="8adec-143">@No__t-0 derleyici seçeneği kullanılmazsa, derleyici .NET Framework klasöründe tanımlanan DLL 'yi (`%systemroot%\Microsoft.NET\Framework\versionNumber`) arar.</span><span class="sxs-lookup"><span data-stu-id="8adec-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8adec-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="8adec-144">Example</span></span>  
 <span data-ttu-id="8adec-145">Aşağıdaki örnek, bir özel kitaplığa başvuru ile derlemek için `-vbruntime` seçeneğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8adec-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="8adec-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8adec-146">See also</span></span>

- [<span data-ttu-id="8adec-147">Visual Basic Core – Visual Studio 2010 SP1 'de yeni derleme modu</span><span class="sxs-lookup"><span data-stu-id="8adec-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="8adec-148">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="8adec-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8adec-149">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="8adec-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="8adec-150">-SdkPath</span><span class="sxs-lookup"><span data-stu-id="8adec-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
