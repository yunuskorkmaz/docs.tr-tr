---
description: '-target: winmdobj (C# derleyici seçenekleri)'
title: '-target: winmdobj (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: a13e2da02698209a514e716d65c1df3508cf1508
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171409"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="81f7e-103">-target: winmdobj (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="81f7e-103">-target:winmdobj (C# Compiler Options)</span></span>

<span data-ttu-id="81f7e-104">**-Target: winmdobj** derleyici seçeneğini kullanırsanız, derleyici Windows çalışma zamanı ikili (. winmd) dosyasına dönüştürebileceğiniz bir ara. winmdobj dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81f7e-104">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="81f7e-105">. Winmd dosyası daha sonra JavaScript ve C++ programları tarafından, yönetilen dil programlarına ek olarak tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="81f7e-105">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f7e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="81f7e-106">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="81f7e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81f7e-107">Remarks</span></span>  

 <span data-ttu-id="81f7e-108">**Winmdobj** ayarı derleyiciye bir ara modülün gerekli olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="81f7e-108">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="81f7e-109">Yanıt olarak, Visual Studio C# sınıf kitaplığını bir. winmdobj dosyası olarak derler.</span><span class="sxs-lookup"><span data-stu-id="81f7e-109">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="81f7e-110">. Winmdobj dosyası daha sonra <xref:Microsoft.Build.Tasks.WinMDExp> bir Windows meta veri (. winmd) dosyası oluşturmak için dışarı aktarma aracından beslenebilir.</span><span class="sxs-lookup"><span data-stu-id="81f7e-110">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="81f7e-111">. Winmd dosyası, özgün kitaplıktan kodu ve JavaScript ya da C++ tarafından kullanılan WinMD meta verilerini ve Windows Çalışma Zamanı içerir.</span><span class="sxs-lookup"><span data-stu-id="81f7e-111">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="81f7e-112">**-Target: winmdobj** derleyici seçeneği kullanılarak derlenen bir dosyanın çıktısı yalnızca Wımmdexp Export aracı için giriş olarak kullanılmak üzere tasarlanmıştır; . winmdobj dosyasının kendisine doğrudan başvurulmuyor.</span><span class="sxs-lookup"><span data-stu-id="81f7e-112">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="81f7e-113">[-Out](./out-compiler-option.md) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="81f7e-113">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="81f7e-114">[Main](../../programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="81f7e-114">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="81f7e-115">Bir komut isteminde-target: winmdobj seçeneğini belirtirseniz, Windows programını oluşturmak için bir sonraki **-Out** veya [-target: Module](./target-module-compiler-option.md) seçeneği görüntüleninceye kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="81f7e-115">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="81f7e-116">Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="81f7e-116">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="81f7e-117">**Çözüm Gezgini**' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="81f7e-117">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="81f7e-118">**Uygulama** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="81f7e-118">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="81f7e-119">**Çıktı türü** listesinde, **winmd dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="81f7e-119">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="81f7e-120">**Winmd dosyası** seçeneği yalnızca Windows 8. x Mağazası uygulama şablonları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81f7e-120">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="81f7e-121">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="81f7e-121">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81f7e-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="81f7e-122">Example</span></span>  

 <span data-ttu-id="81f7e-123">Aşağıdaki komut `filename.cs` bir ara. winmdobj dosyası içinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="81f7e-123">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="81f7e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81f7e-124">See also</span></span>

- [<span data-ttu-id="81f7e-125">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="81f7e-125">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="81f7e-126">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="81f7e-126">C# Compiler Options</span></span>](./index.md)
