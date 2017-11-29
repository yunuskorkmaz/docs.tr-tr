---
title: "Nasıl yapılır: Birden Fazla Dosya Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68a2217ed05588b2ba6070850dfd0d61a7a0fde2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="d3dc6-102">Nasıl yapılır: Birden Fazla Dosya Derleme</span><span class="sxs-lookup"><span data-stu-id="d3dc6-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="d3dc6-103">Bu makalede, birden fazla dosya derlemesi oluşturma açıklanmaktadır ve yordamda her adım gösterilmektedir kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3dc6-104">C# ve Visual Basic için Visual Studio IDE yalnızca tek dosya derlemeleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="d3dc6-105">Birden çok dosya derlemeleri oluşturmak istiyorsanız, Visual C++ ile komut satırı derleyicileri veya Visual Studio kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="d3dc6-106">Birden fazla dosya derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3dc6-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="d3dc6-107">Bütünleştirilmiş kod modüllere diğer modüller tarafından başvurulan ad alanları içeren tüm dosyalar derleyin.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="d3dc6-108">Kod modülleri için varsayılan .netmodule uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="d3dc6-109">Örneğin, diyelim `Stringer` dosya adlı bir ad alanına sahip `myStringer`, adlı bir sınıf içerir `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="d3dc6-110">`Stringer` Sınıfı içeren adlı bir yöntem `StringerMethod` , tek bir satır konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     <span data-ttu-id="d3dc6-111">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d3dc6-111">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     <span data-ttu-id="d3dc6-112">Belirtme *Modülü* parametresiyle **/t:** derleyici seçeneği, dosyanın bir modül olarak yerine bir derlemeyi olarak derlenmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="d3dc6-113">Adlı bir modül derleyici üreten `Stringer.netmodule`, hangi eklenebilir bir derlemeye.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="d3dc6-114">Kod içinde başvurulan diğer modüller göstermek için gerekli derleyici seçenekleri kullanarak tüm diğer modüllerin derleyin.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="d3dc6-115">Bu adımı kullanan **/addmodule** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-115">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="d3dc6-116">Aşağıdaki örnekte, bir kod modülüne adlı `Client` bir giriş noktası sahip `Main` bir yönteme başvuran yöntemi `Stringer.dll` 1. adımda oluşturduğunuz modül.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     <span data-ttu-id="d3dc6-117">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d3dc6-117">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     <span data-ttu-id="d3dc6-118">Belirtin **/t:module** Bu modülün derleme için bir sonraki adımda eklenen olacağından.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="d3dc6-119">Belirtin **/addmodule** olacağından kodda `Client` kod tarafından oluşturulan bir ad alanı referanslarını `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="d3dc6-120">Adlı bir modül derleyici üreten `Client.netmodule` başka bir modül için bir başvuru içeren `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3dc6-121">C# ve Visual Basic derleyicileri doğrudan aşağıdaki iki farklı sözdizimi kullanarak birden çok dosya derlemeleri oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="d3dc6-122">İki derlemeleri iki dosyalı derleme oluşturma:</span><span class="sxs-lookup"><span data-stu-id="d3dc6-122">Two compilations create a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   <span data-ttu-id="d3dc6-123">Bir derleme iki dosyalı derleme oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d3dc6-123">One compilation creates a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  <span data-ttu-id="d3dc6-124">Kullanım [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) derleme bildirimi içerir çıktı dosyasını oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="d3dc6-125">Bu dosya, tüm modülleri veya derlemenin parçası olan kaynaklar için başvuru bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="d3dc6-126">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="d3dc6-126">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="d3dc6-127">**Al** \< *modül adı*> \<*modül adı*>...</span><span class="sxs-lookup"><span data-stu-id="d3dc6-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="d3dc6-128">**/ main:**\<*yöntem adı*> **/out:**\<*dosya adı*> **/ Hedef:**\<*derleme dosya türü*></span><span class="sxs-lookup"><span data-stu-id="d3dc6-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="d3dc6-129">Bu komutta *modül adı* bağımsız değişkenleri derlemeyi dahil etmek için her modül adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="d3dc6-130">**/Ana:** seçeneği derlemenin giriş noktası yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="d3dc6-131">**/Out:** seçeneği derleme meta verilerini içeren çıktı dosyası adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="d3dc6-132">**/Target:** seçeneği derleme bir konsol uygulama yürütülebilir dosyanın (.exe) dosyası, bir Windows yürütülebilir dosya (.win) dosyası ya da kitaplık (.lib) dosyası olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="d3dc6-133">Aşağıdaki örnekte, Al.exe adlı bir konsol uygulaması yürütülebilir bir derleme oluşturur `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="d3dc6-134">Uygulama adında iki modülden oluşur `Client.netmodule` ve `Stringer.netmodule`, yürütülebilir dosya adı verilen ve `myAssembly.exe,` yalnızca derleme meta verilerini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata .</span></span> <span data-ttu-id="d3dc6-135">Giriş noktası derlemenin `Main` sınıfında yöntemi `MainClientApp`, bulunan `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="d3dc6-136">Kullanabileceğiniz [MSIL ayrıştırıcı (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) bütünleştirilmiş içeriğini incelemek veya bir dosyanın bir derlemeyi ya da bir modül olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3dc6-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3dc6-137">See Also</span></span>  
 [<span data-ttu-id="d3dc6-138">Derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3dc6-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="d3dc6-139">Nasıl yapılır: derleme içeriklerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d3dc6-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [<span data-ttu-id="d3dc6-140">Çalışma zamanı derlemeleri nasıl bulur</span><span class="sxs-lookup"><span data-stu-id="d3dc6-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="d3dc6-141">Birden çok dosya derlemeleri</span><span class="sxs-lookup"><span data-stu-id="d3dc6-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
