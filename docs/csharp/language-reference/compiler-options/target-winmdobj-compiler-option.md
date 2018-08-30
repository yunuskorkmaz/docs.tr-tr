---
title: '-target: winmdobj (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 38d0dedbca56475d4f2561c99e8b29e01e9d7a90
ms.sourcegitcommit: 875ecc3ab2437e299b1d50076bd9b878fa8c64de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43238582"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="e4cf9-102">-target: winmdobj (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e4cf9-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="e4cf9-103">Kullanırsanız **-target: winmdobj** derleyici seçeneği, derleyicinin bir Windows çalışma zamanı (.winmd) ikili dosyasına dönüştürebileceğiniz bir ara .winmdobj dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="e4cf9-104">.Winmd dosyası yönetilen dil programlarının yanı sıra, JavaScript ve C++ programları tarafından ardından tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4cf9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4cf9-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="e4cf9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4cf9-106">Remarks</span></span>  
 <span data-ttu-id="e4cf9-107">**Winmdobj** sinyalleri bir ara modülün gerekli olduğunu ayarı.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="e4cf9-108">Yanıt olarak, Visual Studio C# sınıf kitaplığını bir .winmdobj dosyası olarak derler.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="e4cf9-109">.Winmdobj dosyası daha sonra doldurularak <xref:Microsoft.Build.Tasks.WinMDExp> dışa aktarma aracı bir Windows meta veri (.winmd) dosyası.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="e4cf9-110">.Winmd dosyası, kod özgün kitaplık ve Windows çalışma zamanı ve JavaScript veya C++ tarafından kullanılan WinMD meta verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="e4cf9-111">Kullanılarak derlenmiş bir dosya çıktısı **-target: winmdobj** derleyici seçeneği, giriş olarak yalnızca WimMDExp verme aracı için kullanılmak üzere tasarlanmıştır; .winmdobj dosyasının kendisine doğrudan başvuru yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="e4cf9-112">Kullanmadığınız sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıkış dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-112">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="e4cf9-113">A [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="e4cf9-114">Belirtirseniz - target: winmdobj seçeneğini bir komut isteminde, sonraki kadar tüm dosyaları **-out** veya [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="e4cf9-115">Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e4cf9-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1.  <span data-ttu-id="e4cf9-116">İçinde **Çözüm Gezgini**, projeniz için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="e4cf9-117">Seçin **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-117">Choose the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="e4cf9-118">İçinde **çıkış türü** listesinde **WinMD dosyası**.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="e4cf9-119">**WinMD dosyası** yalnızca seçeneğin kullanılabilir [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulama şablonları.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-119">The **WinMD File** option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="e4cf9-120">Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4cf9-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4cf9-121">Example</span></span>  
 <span data-ttu-id="e4cf9-122">Aşağıdaki komut `filename.cs` bir ara .winmdobj dosyasına.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4cf9-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4cf9-123">See Also</span></span>  

- [<span data-ttu-id="e4cf9-124">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e4cf9-124">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="e4cf9-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e4cf9-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
