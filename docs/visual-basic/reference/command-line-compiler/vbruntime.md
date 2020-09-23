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
ms.openlocfilehash: 46d4b095d4a2bf9aac9124d5d4b2a09adb347ba1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085067"
---
# <a name="-vbruntime"></a><span data-ttu-id="ebac5-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="ebac5-102">-vbruntime</span></span>

<span data-ttu-id="ebac5-103">Derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan veya belirli bir çalışma zamanı kitaplığı başvurusuyla derlenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebac5-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebac5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ebac5-104">Syntax</span></span>  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="ebac5-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ebac5-105">Arguments</span></span>  

 \-  
 <span data-ttu-id="ebac5-106">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin.</span><span class="sxs-lookup"><span data-stu-id="ebac5-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="ebac5-107">Varsayılan Visual Basic çalışma zamanı kitaplığı başvurusuyla derleyin.</span><span class="sxs-lookup"><span data-stu-id="ebac5-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="ebac5-108">Visual Basic çalışma zamanı kitaplığı başvurusu olmadan derleyin ve temel işlevselliği Visual Basic çalışma zamanı kitaplığından derlemeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ebac5-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="ebac5-109">Belirtilen kitaplığa (DLL) bir başvuru ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="ebac5-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebac5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebac5-110">Remarks</span></span>  

 <span data-ttu-id="ebac5-111">`-vbruntime`Derleyici seçeneği, derleyicinin Visual Basic çalışma zamanı kitaplığına bir başvuru olmadan derlenmesi gerektiğini belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebac5-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="ebac5-112">Visual Basic çalışma zamanı kitaplığına başvuru olmadan derlerseniz, hatalar veya uyarılar bir Visual Basic çalışma zamanı Yardımcısı çağrısı üreten kod veya dil yapılarında günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ebac5-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="ebac5-113">( *Visual Basic çalışma zamanı Yardımcısı* , belirli bir dil anlam yürütmesi yürütmek için çalışma zamanında çağrılan Microsoft.VisualBasic.dll tanımlanan bir işlevdir.)</span><span class="sxs-lookup"><span data-stu-id="ebac5-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="ebac5-114">`-vbruntime+`Seçeneği, anahtar belirtilmediğinde oluşan aynı davranışı üretir `-vbruntime` .</span><span class="sxs-lookup"><span data-stu-id="ebac5-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="ebac5-115">Daha `-vbruntime+` önceki anahtarları geçersiz kılmak için seçeneğini kullanabilirsiniz `-vbruntime` .</span><span class="sxs-lookup"><span data-stu-id="ebac5-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="ebac5-116">`My`Veya seçeneklerini kullandığınızda, türün çoğu nesne kullanılamaz `-vbruntime-` `-vbruntime:path` .</span><span class="sxs-lookup"><span data-stu-id="ebac5-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="ebac5-117">Visual Basic çalışma zamanı temel işlevlerini katıştırma</span><span class="sxs-lookup"><span data-stu-id="ebac5-117">Embedding Visual Basic Runtime core functionality</span></span>  

 <span data-ttu-id="ebac5-118">`-vbruntime*`Seçeneği, bir çalışma zamanı kitaplığı başvurusu olmadan derlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebac5-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="ebac5-119">Bunun yerine, Visual Basic çalışma zamanı kitaplığındaki çekirdek işlevsellik Kullanıcı derlemesine katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="ebac5-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="ebac5-120">Uygulamanız Visual Basic çalışma zamanı içermeyen platformlarda çalışıyorsa, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebac5-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="ebac5-121">Aşağıdaki çalışma zamanı üyeleri katıştırılır:</span><span class="sxs-lookup"><span data-stu-id="ebac5-121">The following runtime members are embedded:</span></span>  
  
- <span data-ttu-id="ebac5-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> sınıfı</span><span class="sxs-lookup"><span data-stu-id="ebac5-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
- <span data-ttu-id="ebac5-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebac5-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
- <span data-ttu-id="ebac5-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebac5-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
- <span data-ttu-id="ebac5-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebac5-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
- <span data-ttu-id="ebac5-126"><xref:Microsoft.VisualBasic.Constants.vbBack> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
- <span data-ttu-id="ebac5-127"><xref:Microsoft.VisualBasic.Constants.vbCr> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
- <span data-ttu-id="ebac5-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
- <span data-ttu-id="ebac5-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
- <span data-ttu-id="ebac5-130"><xref:Microsoft.VisualBasic.Constants.vbLf> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
- <span data-ttu-id="ebac5-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
- <span data-ttu-id="ebac5-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
- <span data-ttu-id="ebac5-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
- <span data-ttu-id="ebac5-134"><xref:Microsoft.VisualBasic.Constants.vbTab> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
- <span data-ttu-id="ebac5-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> sabit</span><span class="sxs-lookup"><span data-stu-id="ebac5-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
- <span data-ttu-id="ebac5-136">Türün bazı nesneleri `My`</span><span class="sxs-lookup"><span data-stu-id="ebac5-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="ebac5-137">Seçeneğini kullanarak derlerseniz `-vbruntime*` ve kodunuz çekirdek işlevlerle gömülü olmayan Visual Basic çalışma zamanı kitaplığından bir üyeye başvuruyorsa, derleyici üyenin kullanılamaz olduğunu belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="ebac5-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="ebac5-138">Belirtilen bir kitaplığa başvurma</span><span class="sxs-lookup"><span data-stu-id="ebac5-138">Referencing a specified library</span></span>  

 <span data-ttu-id="ebac5-139">`path`Varsayılan Visual Basic çalışma zamanı kitaplığı yerine özel bir çalışma zamanı kitaplığı başvurusuyla derlemek için bağımsız değişkenini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebac5-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="ebac5-140">`path`Bağımsız değişkenin değeri BIR DLL 'nin tam yolu ise, derleyici çalışma zamanı kitaplığı olarak bu dosyayı kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="ebac5-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="ebac5-141">`path`Bağımsız değişkenin değeri BIR DLL 'ye tam yol değilse, Visual Basic derleyici önce geçerli klasörde tanımlanan dll 'yi arar.</span><span class="sxs-lookup"><span data-stu-id="ebac5-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="ebac5-142">Daha sonra [-SdkPath](sdkpath.md) derleyici seçeneğini kullanarak belirttiğiniz yolda arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="ebac5-142">It will then search in the path that you have specified by using the [-sdkpath](sdkpath.md) compiler option.</span></span> <span data-ttu-id="ebac5-143">`-sdkpath`Derleyici seçeneği kullanılmazsa, derleyici .NET Framework klasöründe () tanımlanan dll 'yi arar `%systemroot%\Microsoft.NET\Framework\versionNumber` .</span><span class="sxs-lookup"><span data-stu-id="ebac5-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebac5-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebac5-144">Example</span></span>  

 <span data-ttu-id="ebac5-145">Aşağıdaki örnek, `-vbruntime` özel bir kitaplığa yönelik bir başvuruya sahip derleme için seçeneğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ebac5-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebac5-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebac5-146">See also</span></span>

- [<span data-ttu-id="ebac5-147">Visual Basic Core – Visual Studio 2010 SP1 'de yeni derleme modu</span><span class="sxs-lookup"><span data-stu-id="ebac5-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="ebac5-148">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ebac5-148">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ebac5-149">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ebac5-149">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="ebac5-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="ebac5-150">-sdkpath</span></span>](sdkpath.md)
