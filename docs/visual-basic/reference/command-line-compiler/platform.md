---
title: /platform (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d52ade26bc249625a77720fe05ad9c1ab58b04f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="platform-visual-basic"></a><span data-ttu-id="dd325-102">/platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd325-102">/platform (Visual Basic)</span></span>
<span data-ttu-id="dd325-103">Ortak dil çalışma zamanı (CLR) hangi platformu sürümü çıktı dosyasını çalıştırıp belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd325-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd325-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd325-104">Syntax</span></span>  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="dd325-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dd325-105">Arguments</span></span>  
  
|<span data-ttu-id="dd325-106">Terim</span><span class="sxs-lookup"><span data-stu-id="dd325-106">Term</span></span>|<span data-ttu-id="dd325-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="dd325-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="dd325-108">32-bit, x86 uyumlu CLR tarafından çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dd325-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="dd325-109">AMD64 veya EM64T yönerge kümesi destekleyen bir bilgisayarda 64-bit CLR tarafından çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dd325-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="dd325-110">64-bit CLR tarafından Itanium işlemcili bir bilgisayarda çalıştırılması için derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dd325-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="dd325-111">ARM (Gelişmiş RISC makinesi) işlemciye sahip bir bilgisayarda çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dd325-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="dd325-112">Herhangi bir platformda çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dd325-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="dd325-113">Uygulama 32 bit uygulama 32 bit Windows sürümleri üzerinde ve Windows 64 bit sürümlerinde 64-bit uygulama olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="dd325-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="dd325-114">Bu bayrak varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="dd325-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="dd325-115">Herhangi bir platformda çalıştırılacak derlemenizi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dd325-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="dd325-116">Uygulama 32 bit uygulama olarak, Windows'un 32 bit ve 64 bit sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="dd325-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="dd325-117">Bu bayrak, yalnızca yürütülebilir dosyalar için geçerlidir (. EXE) ve gerektirir [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd325-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd325-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd325-118">Remarks</span></span>  
 <span data-ttu-id="dd325-119">Kullanım `/platform` seçeneği çıktı dosyası tarafından hedeflenen işlemci türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="dd325-119">Use the `/platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="dd325-120">Genel olarak, Visual Basic'te yazılmış .NET Framework derlemeleri aynı platformdan bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="dd325-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="dd325-121">Ancak, farklı platformlarda farklı şekilde davranan bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="dd325-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="dd325-122">Bu ortak çalışmalarını şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dd325-122">These common cases are:</span></span>  
  
-   <span data-ttu-id="dd325-123">Herhangi bir işaretçi türü gibi platforma bağlı olarak boyutunu değiştirme üyeleri içeren yapıları.</span><span class="sxs-lookup"><span data-stu-id="dd325-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
-   <span data-ttu-id="dd325-124">Sabit boyutlar içeren işaretçi aritmetiği.</span><span class="sxs-lookup"><span data-stu-id="dd325-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
-   <span data-ttu-id="dd325-125">Tanıtıcılar için `Integer` yerine <xref:System.IntPtr> kullanan yanlış platform çağrıları veya COM bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="dd325-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
-   <span data-ttu-id="dd325-126">Atama <xref:System.IntPtr> için `Integer`.</span><span class="sxs-lookup"><span data-stu-id="dd325-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
-   <span data-ttu-id="dd325-127">Platform kullanarak çağırma veya COM birlikte çalışma bileşenlerle tüm platformlarda mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="dd325-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="dd325-128">**/Platform** kodunuzu çalışacak mimarisi hakkında varsayımlar yapmış biliyorsanız, seçeneği bazı sorunları azaltmaya.</span><span class="sxs-lookup"><span data-stu-id="dd325-128">The **/platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="dd325-129">Özellikle:</span><span class="sxs-lookup"><span data-stu-id="dd325-129">Specifically:</span></span>  
  
-   <span data-ttu-id="dd325-130">Bir 64-bit platformu hedefleyen karar ve uygulama 32-bit bir makineye çalıştırırsanız, hata iletisi çok daha önce gelen ve bu anahtar kullanmadan oluşan hatasından daha soruna daha yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="dd325-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
-   <span data-ttu-id="dd325-131">Ayarlarsanız `x86` bayrağı seçeneğinde ve uygulamayı daha sonra bir 64-bit makinede çalıştırın, uygulamayı yerel olarak çalıştırmak yerine WOW Subsystem çalıştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="dd325-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="dd325-132">Bir 64-bit Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="dd325-132">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="dd325-133">Derlenmiş derlemeler `/platform:x86` WOW64 altında çalışan 32 bit CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dd325-133">Assemblies compiled with `/platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="dd325-134">Derlenmiş olan yürütülebilir dosyalar `/platform:anycpu` 64-bit CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dd325-134">Executables compiled with the `/platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="dd325-135">DLL ile derlenmiş `/platform:anycpu` içine yüklenen bir işlem olarak aynı CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dd325-135">A DLL compiled with the `/platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
-   <span data-ttu-id="dd325-136">İle derlenmiş yürütülebilir dosyalar `/platform:anycpu32bitpreferred` 32-bit CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="dd325-136">Executables that are compiled with `/platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="dd325-137">Bir Windows 64-bit sürümü çalıştırmak için uygulama geliştirme hakkında daha fazla bilgi için bkz: [64-bit uygulamalar](https://msdn.microsoft.com/library/ms241064).</span><span class="sxs-lookup"><span data-stu-id="dd325-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](https://msdn.microsoft.com/library/ms241064).</span></span>  
  
### <a name="to-set-platform-in-the-visual-studio-ide"></a><span data-ttu-id="dd325-138">Visual Studio IDE içinde/Platform ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="dd325-138">To set /platform in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="dd325-139">İçinde **Çözüm Gezgini**, proje seçme açmak **proje** menüsüne ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dd325-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="dd325-140">Daha fazla bilgi için bkz: [NIB: Proje özellikleriyle yönetme Proje Tasarımcısı](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="dd325-140">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="dd325-141">Üzerinde **derleme** sekmesini seçin veya temizleyin **tercih 32-bit** onay kutusunu veya **hedef CPU** listesinde, bir değer seçin.</span><span class="sxs-lookup"><span data-stu-id="dd325-141">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="dd325-142">Daha fazla bilgi için bkz: [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="dd325-142">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd325-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd325-143">Example</span></span>  
 <span data-ttu-id="dd325-144">Aşağıdaki örnekte nasıl kullanılacağını anlatan `/platform` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="dd325-144">The following example illustrates how to use the `/platform` compiler option.</span></span>  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd325-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd325-145">See Also</span></span>  
 [<span data-ttu-id="dd325-146">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd325-146">/target (Visual Basic)</span></span>](target.md)  
 [<span data-ttu-id="dd325-147">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="dd325-147">Visual Basic Command-Line Compiler</span></span>](index.md)  
 [<span data-ttu-id="dd325-148">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="dd325-148">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
