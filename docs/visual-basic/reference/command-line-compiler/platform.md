---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 5c01136564d64d5b2f1f56d311a6b7eadf1742f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633077"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="ae85e-102">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae85e-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="ae85e-103">Çıkış dosyası hangi ortak dil çalışma zamanı (CLR) platform sürümünü çalıştırabilirsiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae85e-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae85e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae85e-104">Syntax</span></span>  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae85e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae85e-105">Arguments</span></span>  
  
|<span data-ttu-id="ae85e-106">Terim</span><span class="sxs-lookup"><span data-stu-id="ae85e-106">Term</span></span>|<span data-ttu-id="ae85e-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="ae85e-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="ae85e-108">Derlemenizi 32-bit, x86 ile uyumlu bir CLR tarafından çalıştırılacak derler.</span><span class="sxs-lookup"><span data-stu-id="ae85e-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="ae85e-109">Derlemenizi 64 bit CLR tarafından AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda çalıştırılması için derler.</span><span class="sxs-lookup"><span data-stu-id="ae85e-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="ae85e-110">Derlemenizi 64 bit CLR tarafından bir Itanium işlemci bir bilgisayarda çalıştırılması için derler.</span><span class="sxs-lookup"><span data-stu-id="ae85e-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="ae85e-111">ARM (Gelişmiş RISC makinesi) işlemciye sahip bir bilgisayarda çalıştırmak için derlemenizi derler.</span><span class="sxs-lookup"><span data-stu-id="ae85e-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="ae85e-112">Herhangi bir platform üzerinde çalıştırmasını derlemenizin derler.</span><span class="sxs-lookup"><span data-stu-id="ae85e-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="ae85e-113">Uygulamayı Windows 32-bit sürümlerinde 32 bit uygulama olarak ve Windows 64 bit sürümlerinde 64 bit uygulama olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="ae85e-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="ae85e-114">Bu bayrak varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="ae85e-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="ae85e-115">Herhangi bir platform üzerinde çalıştırmasını derlemenizin derler.</span><span class="sxs-lookup"><span data-stu-id="ae85e-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="ae85e-116">Uygulama bir 32 bit uygulama olarak, hem 32-bit hem de 64 bit Windows sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ae85e-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="ae85e-117">Bu bayrak, yalnızca yürütülebilir dosyalar için geçerlidir (. EXE) ve gerektiren [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae85e-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae85e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae85e-118">Remarks</span></span>  
 <span data-ttu-id="ae85e-119">Kullanım `-platform` çıktı dosyası tarafından hedeflenen işlemci türünü belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ae85e-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="ae85e-120">Genel olarak, .NET Framework derlemeleri Visual Basic'te yazılmış aynı platformdan bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="ae85e-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="ae85e-121">Ancak, farklı platformlarda farklı şekilde davranan bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="ae85e-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="ae85e-122">Bu yaygın durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ae85e-122">These common cases are:</span></span>  
  
- <span data-ttu-id="ae85e-123">Herhangi bir işaretçi türü gibi platforma göre boyutunu değiştiren üyeler içeren yapılar.</span><span class="sxs-lookup"><span data-stu-id="ae85e-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="ae85e-124">Sabit boyutlar içeren işaretçi aritmetiği.</span><span class="sxs-lookup"><span data-stu-id="ae85e-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="ae85e-125">Tanıtıcılar için `Integer` yerine <xref:System.IntPtr> kullanan yanlış platform çağrıları veya COM bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="ae85e-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="ae85e-126">Atama <xref:System.IntPtr> için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ae85e-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="ae85e-127">Platform kullanarak çağırma veya COM birlikte çalışma bileşenlerle tüm platformlarda mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="ae85e-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="ae85e-128">**-Platform** seçeneği kodunuzun çalışacak mimarisi hakkında varsayımlar yapmış biliyorsanız, bazı sorunları azaltmak.</span><span class="sxs-lookup"><span data-stu-id="ae85e-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="ae85e-129">Özellikle:</span><span class="sxs-lookup"><span data-stu-id="ae85e-129">Specifically:</span></span>  
  
- <span data-ttu-id="ae85e-130">Bir 64 bit platformları hedefleyen karar ve uygulamanın bir 32-bit makinede çalıştırılması, hata iletisi çok daha önce gelir ve bu anahtarı kullanmadan oluşan bir hata daha sorunu daha yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ae85e-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="ae85e-131">Ayarlarsanız `x86` seçeneğinde bayrağı ve uygulamayı daha sonra bir 64-bit makinede çalıştırmak, uygulamayı yerel olarak çalıştırmak yerine WOW alt sistemi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ae85e-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="ae85e-132">Bir 64 bit Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="ae85e-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="ae85e-133">Derlenmiş derlemelerde `-platform:x86` WOW64 altında çalışan 32 bitlik CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ae85e-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="ae85e-134">Yürütülebilir dosyalar ile derlenmiş olan `-platform:anycpu` 64 bitlik CLR yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ae85e-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="ae85e-135">Bir DLL ile derlenmiş `-platform:anycpu` aynı CLR'yi işlem içine yüklenmiş olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ae85e-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="ae85e-136">İle derlenen yürütülebilir dosyaları `-platform:anycpu32bitpreferred` 32 bitlik CLR yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ae85e-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="ae85e-137">Bir Windows 64-bit sürümünü çalıştırmak için uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ae85e-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="ae85e-138">Ayarlanacak - Visual Studio IDE'de platformu</span><span class="sxs-lookup"><span data-stu-id="ae85e-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="ae85e-139">İçinde **Çözüm Gezgini**, projeyi seçin açın **proje** menüsüne ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ae85e-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="ae85e-140">Üzerinde **derleme** sekmesinde seçin veya temizleyin **32 bit tercih et** onay kutusunu veya **hedef CPU** listesinde, bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="ae85e-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="ae85e-141">Daha fazla bilgi için [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ae85e-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae85e-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae85e-142">Example</span></span>  
 <span data-ttu-id="ae85e-143">Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir `-platform` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ae85e-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae85e-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae85e-144">See also</span></span>

- [<span data-ttu-id="ae85e-145">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae85e-145">/target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="ae85e-146">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ae85e-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ae85e-147">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ae85e-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
