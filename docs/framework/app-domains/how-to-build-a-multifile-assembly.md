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
ms.openlocfilehash: 3072be4e870b64edcea32bb7159db8c64c50d840
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183106"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="886d5-102">Nasıl yapılır: Birden Fazla Dosya Derleme</span><span class="sxs-lookup"><span data-stu-id="886d5-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="886d5-103">Bu makalede, bir çoklu dosya derlemesi oluşturmak nasıl açıklanır ve yordamdaki her adımı gösteren kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="886d5-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="886d5-104">Visual Studio IDE için C# ve Visual Basic yalnızca tek dosya derlemeleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="886d5-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="886d5-105">Çok dosyalı derlemeler oluşturmak istiyorsanız, Visual C++ ile komut satırı derleyicilerini veya Visual Studio kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="886d5-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="886d5-106">Bir çoklu dosya derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="886d5-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="886d5-107">Derlemede kod modülleriyle bütünleştirilmiş diğer modüller tarafından başvurulan ad alanlarını içeren tüm dosyaları derleyin.</span><span class="sxs-lookup"><span data-stu-id="886d5-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="886d5-108">Modüllerin varsayılan uzantısı .netmodule'dür.</span><span class="sxs-lookup"><span data-stu-id="886d5-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="886d5-109">Örneğin, diyelim `Stringer` dosya adlı bir ad alanına sahip `myStringer`, adında bir sınıf içeren `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="886d5-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="886d5-110">`Stringer` Sınıf adında bir yöntem içerir `StringerMethod` , konsola tek satır yazar.</span><span class="sxs-lookup"><span data-stu-id="886d5-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     <span data-ttu-id="886d5-111">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="886d5-111">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     <span data-ttu-id="886d5-112">Belirtme *Modülü* parametresiyle **/t:** derleyici seçeneği, dosyanın bir derleme olarak değil bir modül olarak derlenmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="886d5-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="886d5-113">Derleyici adlı bir modül oluşturur `Stringer.netmodule`, derleyiciye eklenebilecek.</span><span class="sxs-lookup"><span data-stu-id="886d5-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="886d5-114">Kodda başvurulan diğer modülleri göstermek için gerekli derleyici seçeneklerini kullanarak tüm diğer modülleri derleyin.</span><span class="sxs-lookup"><span data-stu-id="886d5-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="886d5-115">Bu adımı kullanan **/addmodule** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="886d5-115">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="886d5-116">Aşağıdaki örnekte adlı kod modülünde `Client` Giriş noktasında, `Main` bir yönteme başvuran yöntemi `Stringer.dll` 1. adımda oluşturduğunuz modülü.</span><span class="sxs-lookup"><span data-stu-id="886d5-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     <span data-ttu-id="886d5-117">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="886d5-117">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     <span data-ttu-id="886d5-118">Belirtin **/t:module** olacağından bu modül gelecekteki bir adımda bir derlemeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="886d5-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="886d5-119">Belirtin **/addmodule** seçeneğini kodda `Client` kod tarafından oluşturulan bir ad alanına başvurduğundan `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="886d5-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="886d5-120">Derleyici adlı bir modül oluşturur `Client.netmodule` başka bir modül için bir başvuru içeren `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="886d5-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="886d5-121">C# Ve Visual Basic derleyicileri, aşağıdaki iki farklı sözdizimini kullanan çok dosyalı derlemeleri doğrudan oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="886d5-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="886d5-122">İki dosyalı bir derleme oluşturun:</span><span class="sxs-lookup"><span data-stu-id="886d5-122">Two compilations create a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   <span data-ttu-id="886d5-123">Tek bir derleme iki dosyalı bir derleme oluşturur:</span><span class="sxs-lookup"><span data-stu-id="886d5-123">One compilation creates a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  <span data-ttu-id="886d5-124">Kullanım [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) derleme bildirimini içeren çıktı dosyasını oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="886d5-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="886d5-125">Bu dosya, tüm modüller veya derlemenin parçası olan kaynaklar için başvuru bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="886d5-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="886d5-126">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="886d5-126">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="886d5-127">**Al** \< *modül adı*> \<*modül adı*>...</span><span class="sxs-lookup"><span data-stu-id="886d5-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="886d5-128">**/ main:**\<*yöntem adı*> **/out:**\<*dosya adı*>   **/target :**\<*derleme dosya türü*></span><span class="sxs-lookup"><span data-stu-id="886d5-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="886d5-129">Bu komutta *modül adı* bağımsız değişkenleri derlemeye eklenecek her modülün adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="886d5-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="886d5-130">**/Main:** seçeneği derlemenin giriş noktası olan yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="886d5-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="886d5-131">**/Out:** seçeneği, derleme meta verilerini içeren çıktı dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="886d5-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="886d5-132">**/Target:** seçeneği derlemenin bir konsol uygulaması yürütülebilir (.exe) dosyası, bir Windows çalıştırılabilir (.win) dosyası veya bir kitaplık (.lib) dosyası olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="886d5-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="886d5-133">Aşağıdaki örnekte, Al.exe adlı yürütülebilir bir konsol uygulaması olan derleme oluşturur. `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="886d5-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="886d5-134">Uygulama adlı iki modülden oluşur `Client.netmodule` ve `Stringer.netmodule`, ve yürütülebilir dosyanın adı `myAssembly.exe,` yalnızca birleştirme metaverilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="886d5-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata.</span></span> <span data-ttu-id="886d5-135">Derlemenin giriş noktası `Main` sınıfında yöntemi `MainClientApp`, bulunan `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="886d5-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="886d5-136">Kullanabileceğiniz [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) bir derlemenin içeriğini incelemek için ya da bir dosyanın bir derleme veya modül olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="886d5-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886d5-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="886d5-137">See Also</span></span>  
- [<span data-ttu-id="886d5-138">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="886d5-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
- [<span data-ttu-id="886d5-139">Nasıl yapılır: Bütünleştirilmiş Kod İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="886d5-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
- [<span data-ttu-id="886d5-140">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="886d5-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="886d5-141">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="886d5-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
