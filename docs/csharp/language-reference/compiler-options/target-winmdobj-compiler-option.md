---
title: '-target: winmdobj (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: fe1332f9ed6de9c50c2509e29f22ed7c0e57ade9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606350"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="48130-102">-target: winmdobj (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="48130-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="48130-103">**-Target: winmdobj** derleyici seçeneğini kullanırsanız, derleyici Windows çalışma zamanı ikili (. winmd) dosyasına dönüştürebileceğiniz bir ara. winmdobj dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48130-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="48130-104">. Winmd dosyası daha sonra JavaScript ve C++ programlar tarafından, yönetilen dil programlarına ek olarak tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="48130-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48130-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48130-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="48130-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48130-106">Remarks</span></span>  
 <span data-ttu-id="48130-107">**Winmdobj** ayarı derleyiciye bir ara modülün gerekli olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="48130-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="48130-108">Yanıt olarak, Visual Studio C# sınıf kitaplığını bir. winmdobj dosyası olarak derler.</span><span class="sxs-lookup"><span data-stu-id="48130-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="48130-109">. Winmdobj dosyası daha sonra bir Windows meta veri ( <xref:Microsoft.Build.Tasks.WinMDExp> . winmd) dosyası oluşturmak için dışarı aktarma aracından beslenebilir.</span><span class="sxs-lookup"><span data-stu-id="48130-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="48130-110">. Winmd dosyası, özgün kitaplıktan kodu ve JavaScript veya C++ Windows çalışma zamanı tarafından kullanılan winmd meta verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="48130-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="48130-111">**-Target: winmdobj** derleyici seçeneği kullanılarak derlenen bir dosyanın çıktısı yalnızca Wımmdexp Export aracı için giriş olarak kullanılmak üzere tasarlanmıştır; . winmdobj dosyasının kendisine doğrudan başvurulmuyor.</span><span class="sxs-lookup"><span data-stu-id="48130-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="48130-112">[-Out](./out-compiler-option.md) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="48130-112">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="48130-113">[Main](../../programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="48130-113">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="48130-114">Bir komut isteminde-target: winmdobj seçeneğini belirtirseniz, Windows programını oluşturmak için bir sonraki **-Out** veya [-target: Module](./target-module-compiler-option.md) seçeneği görüntüleninceye kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48130-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="48130-115">Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="48130-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="48130-116">**Çözüm Gezgini**' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="48130-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="48130-117">**Uygulama** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="48130-117">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="48130-118">**Çıktı türü** listesinde, **winmd dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="48130-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="48130-119">**Winmd dosyası** seçeneği yalnızca uygulama şablonları için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48130-119">The **WinMD File** option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="48130-120">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="48130-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48130-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="48130-121">Example</span></span>  
 <span data-ttu-id="48130-122">Aşağıdaki komut bir ara `filename.cs` . winmdobj dosyası içinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="48130-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="48130-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48130-123">See also</span></span>

- [<span data-ttu-id="48130-124">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="48130-124">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="48130-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="48130-125">C# Compiler Options</span></span>](./index.md)
