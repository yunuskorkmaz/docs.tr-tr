---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec3a7e01e62b60688080fee95cf70e0ed38917f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656184"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="9e5d2-102">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e5d2-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="9e5d2-103">Ortak dil çalışma zamanı (CLR) hangi platformu sürümü çıktı dosyasını çalıştırıp belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e5d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e5d2-104">Syntax</span></span>  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e5d2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9e5d2-105">Arguments</span></span>  
  
|<span data-ttu-id="9e5d2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="9e5d2-106">Term</span></span>|<span data-ttu-id="9e5d2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="9e5d2-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="9e5d2-108">32-bit, x86 uyumlu CLR tarafından çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="9e5d2-109">AMD64 veya EM64T yönerge kümesi destekleyen bir bilgisayarda 64-bit CLR tarafından çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="9e5d2-110">64-bit CLR tarafından Itanium işlemcili bir bilgisayarda çalıştırılması için derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="9e5d2-111">ARM (Gelişmiş RISC makinesi) işlemciye sahip bir bilgisayarda çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="9e5d2-112">Herhangi bir platformda çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="9e5d2-113">Uygulama 32 bit uygulama 32 bit Windows sürümleri üzerinde ve Windows 64 bit sürümlerinde 64-bit uygulama olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="9e5d2-114">Bu bayrak varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="9e5d2-115">Herhangi bir platformda çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="9e5d2-116">Uygulama 32 bit uygulama olarak, Windows'un 32 bit ve 64 bit sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="9e5d2-117">Bu bayrak, yalnızca yürütülebilir dosyalar için geçerlidir (. EXE) ve gerektirir [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9e5d2-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e5d2-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e5d2-118">Remarks</span></span>  
 <span data-ttu-id="9e5d2-119">Kullanım `-platform` seçeneği çıktı dosyası tarafından hedeflenen işlemci türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="9e5d2-120">Genel olarak, Visual Basic'te yazılmış .NET Framework derlemeleri aynı platformdan bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="9e5d2-121">Ancak, farklı platformlarda farklı şekilde davranan bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="9e5d2-122">Bu ortak çalışmalarını şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9e5d2-122">These common cases are:</span></span>  
  
-   <span data-ttu-id="9e5d2-123">Herhangi bir işaretçi türü gibi platforma bağlı olarak boyutunu değiştirme üyeleri içeren yapıları.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
-   <span data-ttu-id="9e5d2-124">Sabit boyutlar içeren işaretçi aritmetiği.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
-   <span data-ttu-id="9e5d2-125">Tanıtıcılar için `Integer` yerine <xref:System.IntPtr> kullanan yanlış platform çağrıları veya COM bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
-   <span data-ttu-id="9e5d2-126">Atama <xref:System.IntPtr> için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
-   <span data-ttu-id="9e5d2-127">Platform kullanarak çağırma veya COM birlikte çalışma bileşenlerle tüm platformlarda mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="9e5d2-128">**-Platform** kodunuzu çalışacak mimarisi hakkında varsayımlar yapmış biliyorsanız, seçeneği bazı sorunları azaltmaya.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="9e5d2-129">Özellikle:</span><span class="sxs-lookup"><span data-stu-id="9e5d2-129">Specifically:</span></span>  
  
-   <span data-ttu-id="9e5d2-130">Bir 64-bit platformu hedefleyen karar ve uygulama 32-bit bir makineye çalıştırırsanız, hata iletisi çok daha önce gelen ve bu anahtar kullanmadan oluşan hatasından daha soruna daha yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
-   <span data-ttu-id="9e5d2-131">Ayarlarsanız `x86` bayrağı seçeneğinde ve uygulamayı daha sonra bir 64-bit makinede çalıştırın, uygulamayı yerel olarak çalıştırmak yerine WOW Subsystem çalıştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="9e5d2-132">Bir 64-bit Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="9e5d2-132">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="9e5d2-133">Derlenmiş derlemeler `-platform:x86` WOW64 altında çalışan 32 bit CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="9e5d2-134">Derlenmiş olan yürütülebilir dosyalar `-platform:anycpu` 64-bit CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="9e5d2-135">DLL ile derlenmiş `-platform:anycpu` içine yüklenen bir işlem olarak aynı CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
-   <span data-ttu-id="9e5d2-136">İle derlenmiş yürütülebilir dosyalar `-platform:anycpu32bitpreferred` 32-bit CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="9e5d2-137">Bir Windows 64-bit sürümü çalıştırmak için uygulama geliştirme hakkında daha fazla bilgi için bkz: [64-bit uygulamalar](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="9e5d2-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="9e5d2-138">Ayarlanacak - Visual Studio IDE içinde platformu</span><span class="sxs-lookup"><span data-stu-id="9e5d2-138">To set -platform in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="9e5d2-139">İçinde **Çözüm Gezgini**, proje seçme açmak **proje** menüsüne ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="9e5d2-140">Üzerinde **derleme** sekmesini seçin veya temizleyin **tercih 32-bit** onay kutusunu veya **hedef CPU** listesinde, bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="9e5d2-141">Daha fazla bilgi için bkz: [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9e5d2-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e5d2-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e5d2-142">Example</span></span>  
 <span data-ttu-id="9e5d2-143">Aşağıdaki örnekte nasıl kullanılacağını anlatan `-platform` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e5d2-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e5d2-144">See Also</span></span>  
 [<span data-ttu-id="9e5d2-145">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e5d2-145">/target (Visual Basic)</span></span>](target.md)  
 [<span data-ttu-id="9e5d2-146">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="9e5d2-146">Visual Basic Command-Line Compiler</span></span>](index.md)  
 [<span data-ttu-id="9e5d2-147">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="9e5d2-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
