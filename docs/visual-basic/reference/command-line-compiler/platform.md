---
description: Daha fazla bilgi edinin:-platform (Visual Basic)
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 51d7c7882c29310ef1e0c0f5790a63da3bfb91b8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432747"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="a0228-103">-Platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0228-103">-platform (Visual Basic)</span></span>

<span data-ttu-id="a0228-104">Ortak dil çalışma zamanının (CLR) hangi platform sürümünün çıkış dosyasını çalıştırabileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0228-104">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0228-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a0228-105">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0228-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a0228-106">Arguments</span></span>  
  
|<span data-ttu-id="a0228-107">Terim</span><span class="sxs-lookup"><span data-stu-id="a0228-107">Term</span></span>|<span data-ttu-id="a0228-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="a0228-108">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="a0228-109">Derlemenizi 32 bit, x86 uyumlu CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="a0228-109">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="a0228-110">, Derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="a0228-110">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="a0228-111">Derlemenizi, Itanium işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="a0228-111">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="a0228-112">Derlemenizi ARM (Gelişmiş RıSC makinesi) işlemcisi olan bir bilgisayarda çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="a0228-112">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="a0228-113">Derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="a0228-113">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="a0228-114">Uygulama Windows 'un 32 bit sürümlerinde 32 bitlik bir uygulama olarak ve Windows 'un 64 bit sürümlerinde bir 64 bit uygulama olarak çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="a0228-114">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="a0228-115">Bu bayrak varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a0228-115">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="a0228-116">Derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="a0228-116">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="a0228-117">Uygulama, Windows 'un hem 32 bit hem de 64-bit sürümlerinde 32 bitlik bir uygulama olarak çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="a0228-117">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="a0228-118">Bu bayrak yalnızca yürütülebilir dosyalar için geçerlidir (. EXE) ve .NET Framework 4,5 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a0228-118">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0228-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0228-119">Remarks</span></span>  

 <span data-ttu-id="a0228-120">`-platform`Çıkış dosyası tarafından hedeflenen işlemcinin türünü belirtmek için seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0228-120">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="a0228-121">Genel olarak, Visual Basic yazılan .NET Framework derlemeleri platformdan bağımsız olarak aynı çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="a0228-121">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="a0228-122">Ancak, farklı platformlarda farklı şekilde davranan bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="a0228-122">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="a0228-123">Bu ortak durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a0228-123">These common cases are:</span></span>  
  
- <span data-ttu-id="a0228-124">Herhangi bir işaretçi türü gibi, platforma bağlı olarak boyutu değiştiren Üyeler içeren yapılar.</span><span class="sxs-lookup"><span data-stu-id="a0228-124">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="a0228-125">Sabit boyutlar içeren işaretçi aritmetiği.</span><span class="sxs-lookup"><span data-stu-id="a0228-125">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="a0228-126">Tanıtıcılar için `Integer` yerine <xref:System.IntPtr> kullanan yanlış platform çağrıları veya COM bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="a0228-126">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="a0228-127"><xref:System.IntPtr>Öğesine atama `Integer` .</span><span class="sxs-lookup"><span data-stu-id="a0228-127">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="a0228-128">Tüm platformlarda mevcut olmayan bileşenlerle platform Invoke veya COM birlikte çalışma kullanma.</span><span class="sxs-lookup"><span data-stu-id="a0228-128">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="a0228-129">Kodunuzun çalışacağı mimariyle ilgili varsayımlar yaptığını biliyorsanız, **-Platform** seçeneği bazı sorunları azaltır.</span><span class="sxs-lookup"><span data-stu-id="a0228-129">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="a0228-130">Özellikle:</span><span class="sxs-lookup"><span data-stu-id="a0228-130">Specifically:</span></span>  
  
- <span data-ttu-id="a0228-131">64 bitlik bir platformu hedefistemediğinize karar verirseniz ve uygulama 32 bit makinede çalışıyorsa, hata iletisi daha önce gelir ve sorunu bu anahtarı kullanmadan oluşan hatadan daha da hedeflenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0228-131">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="a0228-132">`x86`Seçeneğini seçenekte ayarlarsanız ve uygulama daha sonra bir 64 bit makinede çalışıyorsa, uygulama yerel olarak çalıştırmak yerıne wow alt sisteminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="a0228-132">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="a0228-133">64 bitlik bir Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="a0228-133">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="a0228-134">İle derlenen derlemeler `-platform:x86` , WOW64 altında çalışan 32 BITLIK clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a0228-134">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="a0228-135">İle derlenen çalıştırılabilir dosyalar `-platform:anycpu` 64 BITLIK clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a0228-135">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="a0228-136">İle derlenen bir DLL, `-platform:anycpu` yüklendiği işlemle aynı CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a0228-136">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="a0228-137">İle derlenen yürütülebilir dosyalar `-platform:anycpu32bitpreferred` 32 BITLIK clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a0228-137">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="a0228-138">Windows 'un 64 bitlik bir sürümünde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="a0228-138">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="a0228-139">Visual Studio IDE 'de set-platform</span><span class="sxs-lookup"><span data-stu-id="a0228-139">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="a0228-140">**Çözüm Gezgini**, projeyi seçin, **Proje** menüsünü açın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a0228-140">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="a0228-141">**Derle** sekmesinde, **32 bit tercih** et onay kutusunu seçin veya temizleyin veya **hedef CPU** listesinden bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="a0228-141">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="a0228-142">Daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a0228-142">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0228-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0228-143">Example</span></span>  

 <span data-ttu-id="a0228-144">Aşağıdaki örnek, derleyici seçeneğinin nasıl kullanılacağını göstermektedir `-platform` .</span><span class="sxs-lookup"><span data-stu-id="a0228-144">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0228-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0228-145">See also</span></span>

- [<span data-ttu-id="a0228-146">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0228-146">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="a0228-147">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a0228-147">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a0228-148">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a0228-148">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
