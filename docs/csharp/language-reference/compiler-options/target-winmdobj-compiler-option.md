---
title: '-target: winmdobj (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: b0b1ec0bed174484e9ed7b9ecddbe82b0c705325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218664"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="a6770-102">-target: winmdobj (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a6770-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="a6770-103">Kullanırsanız **-target: winmdobj** derleyici seçeneği derleyici Windows çalışma zamanı ikili (.winmd) dosyasına dönüştüren bir ara .winmdobj dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6770-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="a6770-104">.Winmd dosya yönetilen dil programlar yanı sıra, JavaScript ve C++ programlarla sonra kullanılabilecek.</span><span class="sxs-lookup"><span data-stu-id="a6770-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6770-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6770-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="a6770-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6770-106">Remarks</span></span>  
 <span data-ttu-id="a6770-107">**Winmdobj** Ara bir modül gerekli olduğunu derleyici sinyalleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="a6770-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="a6770-108">Yanıt olarak, Visual Studio C# sınıf kitaplığı .winmdobj dosyası olarak derler.</span><span class="sxs-lookup"><span data-stu-id="a6770-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="a6770-109">.Winmdobj dosya sonra aracılığıyla Sat <xref:Microsoft.Build.Tasks.WinMDExp> dışa aktarma Windows (.winmd) meta veri dosyası üretmek için aracı.</span><span class="sxs-lookup"><span data-stu-id="a6770-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="a6770-110">.Winmd dosyası kodu özgün kitaplık ve JavaScript ya da C++ ve Windows çalışma zamanı tarafından kullanılan WinMD meta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a6770-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="a6770-111">Kullanarak derlenmiş bir dosya çıktısını **-target: winmdobj** derleyici seçeneği, yalnızca giriş olarak WimMDExp dışarı aktarma aracı için kullanılmak üzere tasarlanmıştır; .winmdobj dosyasını doğrudan başvuruda değil.</span><span class="sxs-lookup"><span data-stu-id="a6770-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="a6770-112">Kullanmadığınız sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="a6770-112">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="a6770-113">A [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a6770-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="a6770-114">Belirtirseniz, target: winmdobj seçeneği bir komut isteminde, sonraki kadar tüm dosyaları **-out** veya [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6770-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="a6770-115">Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a6770-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1.  <span data-ttu-id="a6770-116">İçinde **Çözüm Gezgini**projeniz için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="a6770-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="a6770-117">Seçin **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="a6770-117">Choose the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="a6770-118">İçinde **çıktı türü** listesinde, seçin **WinMD dosyası**.</span><span class="sxs-lookup"><span data-stu-id="a6770-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="a6770-119">**WinMD dosyası** seçenek, yalnızca kullanılabilir [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulama şablonları.</span><span class="sxs-lookup"><span data-stu-id="a6770-119">The **WinMD File** option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="a6770-120">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6770-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6770-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6770-121">Example</span></span>  
 <span data-ttu-id="a6770-122">Aşağıdaki komut derlerken `filename.cs` bir ara .winmdobj dosyasına.</span><span class="sxs-lookup"><span data-stu-id="a6770-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6770-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6770-123">See Also</span></span>  
 [<span data-ttu-id="a6770-124">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a6770-124">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="a6770-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a6770-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
