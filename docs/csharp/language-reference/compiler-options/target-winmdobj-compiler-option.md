---
title: -hedef:winmdobj (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204485"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="4c3ed-102">-hedef:winmdobj (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4c3ed-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="4c3ed-103">**-hedef:winmdobj** derleyici sebunu kullanırsanız, derleyici Windows Runtime ikili (.winmd) dosyasına dönüştürebileceğiniz bir ara .winmdobj dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="4c3ed-104">.winmd dosyası daha sonra yönetilen dil programlarına ek olarak JavaScript ve C++ programları tarafından da tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c3ed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c3ed-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="4c3ed-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c3ed-106">Remarks</span></span>  
 <span data-ttu-id="4c3ed-107">**Winmdobj** ayarı derleyiciye bir ara modülün gerekli olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="4c3ed-108">Buna karşılık, Visual Studio C# sınıf kitaplığını .winmdobj dosyası olarak derler.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="4c3ed-109">.winmdobj dosyası daha sonra bir <xref:Microsoft.Build.Tasks.WinMDExp> Windows meta data (.winmd) dosyası oluşturmak için dışa aktarma aracı üzerinden beslenebilir.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="4c3ed-110">.winmd dosyası hem özgün kitaplıktaki kodu hem de JavaScript veya C++ ve Windows Runtime tarafından kullanılan WinMD meta verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="4c3ed-111">**-target:winmdobj** derleyici seçeneği kullanılarak derlenen bir dosyanın çıktısı yalnızca WimMDExp dışa aktarma aracı nın girişi olarak kullanılmak üzere tasarlanmıştır; .winmdobj dosyasının kendisi doğrudan başvurulmuyor.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="4c3ed-112">[-out](./out-compiler-option.md) seçeneğini kullanmadığınız sürece, çıktı dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-112">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="4c3ed-113">[Ana](../../programming-guide/main-and-command-args/index.md) yöntem gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-113">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="4c3ed-114">Komut isteminde -hedef:winmdobj seçeneğini belirtirseniz, Windows programını oluşturmak için bir sonraki **-out** veya [-target:module](./target-module-compiler-option.md) seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="4c3ed-115">Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4c3ed-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="4c3ed-116">**Çözüm Gezgini'nde,** projenizin kısayol menüsünü açın ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="4c3ed-117">**Uygulama** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-117">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="4c3ed-118">Çıktı **türü** listesinde **WinMD Dosyası'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="4c3ed-119">**WinMD Dosyası** seçeneği yalnızca Windows 8.x Store uygulama şablonları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-119">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="4c3ed-120">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A></span><span class="sxs-lookup"><span data-stu-id="4c3ed-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c3ed-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c3ed-121">Example</span></span>  
 <span data-ttu-id="4c3ed-122">Aşağıdaki komut bir `filename.cs` ara .winmdobj dosyasında derler.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c3ed-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c3ed-123">See also</span></span>

- [<span data-ttu-id="4c3ed-124">-hedef (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4c3ed-124">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="4c3ed-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4c3ed-125">C# Compiler Options</span></span>](./index.md)
