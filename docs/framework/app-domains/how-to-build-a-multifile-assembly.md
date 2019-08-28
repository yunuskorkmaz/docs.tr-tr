---
title: 'Nasıl yapılır: Birden Fazla Dosya Derlemesi Oluşturma'
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
ms.openlocfilehash: a964e73cc41cebad33a3edc34b89ef240fbc62c8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040850"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="ae144-102">Nasıl yapılır: Birden Fazla Dosya Derlemesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ae144-102">How to: Build a Multifile Assembly</span></span>

<span data-ttu-id="ae144-103">Bu makalede, çok dosyalı bir derlemenin nasıl oluşturulacağı ve yordamdaki her adımın gösterildiği kod nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae144-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="ae144-104">Ve Visual Basic için C# VISUAL Studio IDE yalnızca tek dosya derlemeler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae144-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="ae144-105">Çok dosyalı derlemeler oluşturmak istiyorsanız, komut satırı derleyicilerini veya Visual Studio 'Yu Visual C++Studio kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae144-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>

### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="ae144-106">Çoklu dosya derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ae144-106">To create a multifile assembly</span></span>

01. <span data-ttu-id="ae144-107">Derlemedeki diğer modüller tarafından kod modüllerine başvuruda bulunulan ad alanlarını içeren tüm dosyaları derleyin.</span><span class="sxs-lookup"><span data-stu-id="ae144-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="ae144-108">Kod modülleri için varsayılan uzantı. netmodule 'dir.</span><span class="sxs-lookup"><span data-stu-id="ae144-108">The default extension for code modules is .netmodule.</span></span>

    <span data-ttu-id="ae144-109">Örneğin, `Stringer` dosyada adlı bir sınıf `Stringer`içeren bir `myStringer`ad alanı olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ae144-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="ae144-110">Sınıfı, konsola tek bir satır `StringerMethod` yazan adlı bir yöntemi içerir. `Stringer`</span><span class="sxs-lookup"><span data-stu-id="ae144-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    <span data-ttu-id="ae144-111">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="ae144-111">Use the following command to compile this code:</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    <span data-ttu-id="ae144-112">**/T:** derleyici seçeneğiyle *Modül* parametresini belirtme, dosyanın derleme yerine bir modül olarak derlenmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae144-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="ae144-113">Derleyici, bir derlemeye eklenebilen adlı `Stringer.netmodule`bir modül üretir.</span><span class="sxs-lookup"><span data-stu-id="ae144-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>

02. <span data-ttu-id="ae144-114">Kodda başvurulan diğer modülleri göstermek için gerekli derleyici seçeneklerini kullanarak diğer tüm modülleri derleyin.</span><span class="sxs-lookup"><span data-stu-id="ae144-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="ae144-115">Bu adım, **/addmodule** derleyici seçeneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae144-115">This step uses the **/addmodule** compiler option.</span></span>

    <span data-ttu-id="ae144-116">Aşağıdaki örnekte, adlı `Client` bir kod modülünün, 1. adımda oluşturulan `Stringer.dll` modüldeki `Main` bir yönteme başvuran bir giriş noktası yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="ae144-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    <span data-ttu-id="ae144-117">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="ae144-117">Use the following command to compile this code:</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    <span data-ttu-id="ae144-118">Bu modül gelecekteki bir adımda bir derlemeye eklenecağından **/t: Module** seçeneğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ae144-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="ae144-119">İçindeki`Client` kod, içindeki `Stringer.netmodule`kod tarafından oluşturulan bir ad alanına başvurduğundan **/addmodule** seçeneğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ae144-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="ae144-120">Derleyici, `Client.netmodule` `Stringer.netmodule`başka bir modüle başvuru içeren adlı bir modül üretir.</span><span class="sxs-lookup"><span data-stu-id="ae144-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>

    >[!NOTE]
    ><span data-ttu-id="ae144-121">C# Ve Visual Basic derleyicileri, aşağıdaki iki farklı sözdizimleri kullanılarak çok dosyalı derlemeler doğrudan oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="ae144-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
    >
    >- <span data-ttu-id="ae144-122">İki derleme iki dosya derleme oluşturur:[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]</span><span class="sxs-lookup"><span data-stu-id="ae144-122">Two compilations create a two-file assembly: [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]</span></span>
    >  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- <span data-ttu-id="ae144-123">Bir derleme iki dosya derleme oluşturur:[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]</span><span class="sxs-lookup"><span data-stu-id="ae144-123">One compilation creates a two-file assembly: [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]</span></span>
    >  [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >  [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. <span data-ttu-id="ae144-124">Derleme bildirimini içeren çıktı dosyasını oluşturmak için [derleme Bağlayıcısı (al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae144-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="ae144-125">Bu dosya, derlemenin parçası olan tüm modüller veya kaynaklar için başvuru bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ae144-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="ae144-126">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="ae144-126">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="ae144-127">**Al** \< *Modül*adımodül> adı>...\<</span><span class="sxs-lookup"><span data-stu-id="ae144-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="ae144-128">**/Main:** \<*Yöntem adı*>  **/Out:** dosyaadı\< **/target:** *Assembly dosya* türü\<> ></span><span class="sxs-lookup"><span data-stu-id="ae144-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="ae144-129">Bu komutta, *Modül adı* bağımsız değişkenleri derlemeye dahil edilecek her modülün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae144-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="ae144-130">**/Main:** seçeneği derlemenin giriş noktası olan yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae144-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="ae144-131">**/Out:** seçeneği, derleme meta verilerini içeren çıkış dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae144-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="ae144-132">**/Target:** seçeneği, derlemenin bir konsol uygulaması yürütülebilir (. exe) dosyası, bir Windows yürütülebilir (. Win) dosyası veya bir kitaplık (. lib) dosyası olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae144-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>

    <span data-ttu-id="ae144-133">Aşağıdaki örnekte, al. exe adlı `myAssembly.exe`bir konsol uygulaması yürütülebilir dosyası olan bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ae144-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="ae144-134">Uygulama ve `Client.netmodule` `Stringer.netmodule`adlı iki modülden oluşur ve yalnızca derleme meta verilerini içeren yürütülebilir `myAssembly.exe,` dosya çağırılır.</span><span class="sxs-lookup"><span data-stu-id="ae144-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata.</span></span> <span data-ttu-id="ae144-135">Derlemenin `Main` giriş noktası, sınıfındaki `MainClientApp` `Client.dll`' de bulunan yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="ae144-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="ae144-136">Bir derlemenin içeriğini incelemek veya bir dosyanın derleme veya modülle olduğunu anlamak için [MSIL Disassembler (ıldadsm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae144-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae144-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae144-137">See also</span></span>

- [<span data-ttu-id="ae144-138">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ae144-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="ae144-139">Nasıl yapılır: Derleme Içeriğini görüntüle</span><span class="sxs-lookup"><span data-stu-id="ae144-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [<span data-ttu-id="ae144-140">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="ae144-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ae144-141">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="ae144-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
