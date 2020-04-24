---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352340"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="06e60-102">-Platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06e60-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="06e60-103">Ortak dil çalışma zamanının (CLR) hangi platform sürümünün çıkış dosyasını çalıştırabileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="06e60-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e60-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06e60-104">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="06e60-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="06e60-105">Arguments</span></span>  
  
|<span data-ttu-id="06e60-106">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="06e60-106">Term</span></span>|<span data-ttu-id="06e60-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="06e60-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="06e60-108">Derlemenizi 32 bit, x86 uyumlu CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="06e60-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="06e60-109">, Derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="06e60-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="06e60-110">Derlemenizi, Itanium işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="06e60-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="06e60-111">Derlemenizi ARM (Gelişmiş RıSC makinesi) işlemcisi olan bir bilgisayarda çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="06e60-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="06e60-112">Derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="06e60-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="06e60-113">Uygulama Windows 'un 32 bit sürümlerinde 32 bitlik bir uygulama olarak ve Windows 'un 64 bit sürümlerinde bir 64 bit uygulama olarak çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="06e60-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="06e60-114">Bu bayrak varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="06e60-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="06e60-115">Derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="06e60-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="06e60-116">Uygulama, Windows 'un hem 32 bit hem de 64-bit sürümlerinde 32 bitlik bir uygulama olarak çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="06e60-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="06e60-117">Bu bayrak yalnızca yürütülebilir dosyalar için geçerlidir (. EXE) ve .NET Framework 4,5 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="06e60-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06e60-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06e60-118">Remarks</span></span>  
 <span data-ttu-id="06e60-119">Çıkış dosyası `-platform` tarafından hedeflenen işlemcinin türünü belirtmek için seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="06e60-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="06e60-120">Genel olarak, Visual Basic yazılan .NET Framework derlemeleri platformdan bağımsız olarak aynı çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="06e60-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="06e60-121">Ancak, farklı platformlarda farklı şekilde davranan bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="06e60-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="06e60-122">Bu ortak durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="06e60-122">These common cases are:</span></span>  
  
- <span data-ttu-id="06e60-123">Herhangi bir işaretçi türü gibi, platforma bağlı olarak boyutu değiştiren Üyeler içeren yapılar.</span><span class="sxs-lookup"><span data-stu-id="06e60-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="06e60-124">Sabit boyutlar içeren işaretçi aritmetiği.</span><span class="sxs-lookup"><span data-stu-id="06e60-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="06e60-125">Tanıtıcılar için `Integer` yerine <xref:System.IntPtr> kullanan yanlış platform çağrıları veya COM bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="06e60-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="06e60-126">Öğesine <xref:System.IntPtr> `Integer`atama.</span><span class="sxs-lookup"><span data-stu-id="06e60-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="06e60-127">Tüm platformlarda mevcut olmayan bileşenlerle platform Invoke veya COM birlikte çalışma kullanma.</span><span class="sxs-lookup"><span data-stu-id="06e60-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="06e60-128">Kodunuzun çalışacağı mimariyle ilgili varsayımlar yaptığını biliyorsanız, **-Platform** seçeneği bazı sorunları azaltır.</span><span class="sxs-lookup"><span data-stu-id="06e60-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="06e60-129">Daha ayrıntılı şekilde belirtmek gerekirse:</span><span class="sxs-lookup"><span data-stu-id="06e60-129">Specifically:</span></span>  
  
- <span data-ttu-id="06e60-130">64 bitlik bir platformu hedefistemediğinize karar verirseniz ve uygulama 32 bit makinede çalışıyorsa, hata iletisi daha önce gelir ve sorunu bu anahtarı kullanmadan oluşan hatadan daha da hedeflenmiştir.</span><span class="sxs-lookup"><span data-stu-id="06e60-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="06e60-131">Seçeneğini seçenekte ayarlarsanız `x86` ve uygulama daha sonra bir 64 bit makinede çalışıyorsa, uygulama yerel olarak ÇALıŞTıRMAK yerine wow alt sisteminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="06e60-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="06e60-132">64 bitlik bir Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="06e60-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="06e60-133">İle `-platform:x86` derlenen derlemeler, WOW64 altında çalışan 32 bitlik clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="06e60-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="06e60-134">İle `-platform:anycpu` derlenen çalıştırılabilir dosyalar 64 bitlik clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="06e60-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="06e60-135">İle `-platform:anycpu` derlenen bir dll, yüklendiği IŞLEMLE aynı CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="06e60-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="06e60-136">İle `-platform:anycpu32bitpreferred` derlenen yürütülebilir dosyalar 32 bitlik clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="06e60-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="06e60-137">Windows 'un 64 bitlik bir sürümünde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="06e60-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="06e60-138">Visual Studio IDE 'de set-platform</span><span class="sxs-lookup"><span data-stu-id="06e60-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="06e60-139">**Çözüm Gezgini**, projeyi seçin, **Proje** menüsünü açın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="06e60-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="06e60-140">**Derle** sekmesinde, **32 bit tercih** et onay kutusunu seçin veya temizleyin veya **hedef CPU** listesinden bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="06e60-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="06e60-141">Daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="06e60-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06e60-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="06e60-142">Example</span></span>  
 <span data-ttu-id="06e60-143">Aşağıdaki örnek, `-platform` derleyici seçeneğinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="06e60-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="06e60-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06e60-144">See also</span></span>

- [<span data-ttu-id="06e60-145">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06e60-145">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="06e60-146">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="06e60-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="06e60-147">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="06e60-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
