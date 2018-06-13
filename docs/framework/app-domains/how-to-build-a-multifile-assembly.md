---
title: 'Nasıl yapılır: Birden Fazla Dosya Derleme'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 916db7ec9bee0c85db1f2fcf4db7a9f8a61f9be3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744089"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="5cd95-102">Nasıl yapılır: Birden Fazla Dosya Derleme</span><span class="sxs-lookup"><span data-stu-id="5cd95-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="5cd95-103">Bu makalede, birden fazla dosya derlemesi oluşturma açıklanmaktadır ve yordamda her adım gösterilmektedir kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cd95-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cd95-104">C# ve Visual Basic için Visual Studio IDE yalnızca tek dosya derlemeleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cd95-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="5cd95-105">Birden çok dosya derlemeleri oluşturmak istiyorsanız, Visual C++ ile komut satırı derleyicileri veya Visual Studio kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cd95-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="5cd95-106">Birden fazla dosya derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5cd95-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="5cd95-107">Bütünleştirilmiş kod modüllere diğer modüller tarafından başvurulan ad alanları içeren tüm dosyalar derleyin.</span><span class="sxs-lookup"><span data-stu-id="5cd95-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="5cd95-108">Kod modülleri için varsayılan .netmodule uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="5cd95-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="5cd95-109">Örneğin, diyelim `Stringer` dosya adlı bir ad alanına sahip `myStringer`, adlı bir sınıf içerir `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="5cd95-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="5cd95-110">`Stringer` Sınıfı içeren adlı bir yöntem `StringerMethod` , tek bir satır konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="5cd95-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     <span data-ttu-id="5cd95-111">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5cd95-111">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     <span data-ttu-id="5cd95-112">Belirtme *Modülü* parametresiyle **/t:** derleyici seçeneği, dosyanın bir modül olarak yerine bir derlemeyi olarak derlenmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cd95-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="5cd95-113">Adlı bir modül derleyici üreten `Stringer.netmodule`, hangi eklenebilir bir derlemeye.</span><span class="sxs-lookup"><span data-stu-id="5cd95-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="5cd95-114">Kod içinde başvurulan diğer modüller göstermek için gerekli derleyici seçenekleri kullanarak tüm diğer modüllerin derleyin.</span><span class="sxs-lookup"><span data-stu-id="5cd95-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="5cd95-115">Bu adımı kullanan **/addmodule** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5cd95-115">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="5cd95-116">Aşağıdaki örnekte, bir kod modülüne adlı `Client` bir giriş noktası sahip `Main` bir yönteme başvuran yöntemi `Stringer.dll` 1. adımda oluşturduğunuz modül.</span><span class="sxs-lookup"><span data-stu-id="5cd95-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     <span data-ttu-id="5cd95-117">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5cd95-117">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     <span data-ttu-id="5cd95-118">Belirtin **/t:module** Bu modülün derleme için bir sonraki adımda eklenen olacağından.</span><span class="sxs-lookup"><span data-stu-id="5cd95-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="5cd95-119">Belirtin **/addmodule** olacağından kodda `Client` kod tarafından oluşturulan bir ad alanı referanslarını `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="5cd95-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="5cd95-120">Adlı bir modül derleyici üreten `Client.netmodule` başka bir modül için bir başvuru içeren `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="5cd95-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5cd95-121">C# ve Visual Basic derleyicileri doğrudan aşağıdaki iki farklı sözdizimi kullanarak birden çok dosya derlemeleri oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="5cd95-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="5cd95-122">İki derlemeleri iki dosyalı derleme oluşturma:</span><span class="sxs-lookup"><span data-stu-id="5cd95-122">Two compilations create a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   <span data-ttu-id="5cd95-123">Bir derleme iki dosyalı derleme oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5cd95-123">One compilation creates a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  <span data-ttu-id="5cd95-124">Kullanım [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) derleme bildirimi içerir çıktı dosyasını oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="5cd95-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="5cd95-125">Bu dosya, tüm modülleri veya derlemenin parçası olan kaynaklar için başvuru bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5cd95-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="5cd95-126">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="5cd95-126">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="5cd95-127">**Al** \< *modül adı*> \<*modül adı*>...</span><span class="sxs-lookup"><span data-stu-id="5cd95-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="5cd95-128">**/ main:**\<*yöntem adı*> **/out:**\<*dosya adı*>   **/target :**\<*derleme dosya türü*></span><span class="sxs-lookup"><span data-stu-id="5cd95-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="5cd95-129">Bu komutta *modül adı* bağımsız değişkenleri derlemeyi dahil etmek için her modül adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="5cd95-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="5cd95-130">**/Ana:** seçeneği derlemenin giriş noktası yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cd95-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="5cd95-131">**/Out:** seçeneği derleme meta verilerini içeren çıktı dosyası adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cd95-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="5cd95-132">**/Target:** seçeneği derleme bir konsol uygulama yürütülebilir dosyanın (.exe) dosyası, bir Windows yürütülebilir dosya (.win) dosyası ya da kitaplık (.lib) dosyası olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cd95-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="5cd95-133">Aşağıdaki örnekte, Al.exe adlı bir konsol uygulaması yürütülebilir bir derleme oluşturur `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="5cd95-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="5cd95-134">Uygulama adında iki modülden oluşur `Client.netmodule` ve `Stringer.netmodule`, yürütülebilir dosya adı verilen ve `myAssembly.exe,` yalnızca derleme meta verilerini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5cd95-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata .</span></span> <span data-ttu-id="5cd95-135">Giriş noktası derlemenin `Main` sınıfında yöntemi `MainClientApp`, bulunan `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="5cd95-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="5cd95-136">Kullanabileceğiniz [MSIL ayrıştırıcı (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) bütünleştirilmiş içeriğini incelemek veya bir dosyanın bir derlemeyi ya da bir modül olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="5cd95-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd95-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cd95-137">See Also</span></span>  
 [<span data-ttu-id="5cd95-138">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5cd95-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="5cd95-139">Nasıl yapılır: Bütünleştirilmiş Kod İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5cd95-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [<span data-ttu-id="5cd95-140">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="5cd95-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="5cd95-141">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="5cd95-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
