---
title: 'Nasıl yapılır: Birden çok dosyalı derleme oluşturma'
description: Yordamın her adımını göstermek için örnek kod kullanarak .NET 'te çok dosyalı bir derleme derlemeyi (oluşturmayı) öğrenin.
ms.date: 08/20/2019
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
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: a4c298284950ba2989bb73e6d3383b3c4024e6e7
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104950"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="a8c8f-103">Nasıl yapılır: Birden çok dosyalı derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8c8f-103">How to: Build a multifile assembly</span></span>

<span data-ttu-id="a8c8f-104">Bu makalede, çok dosyalı bir derlemenin nasıl oluşturulacağı ve yordamdaki her adımın gösterildiği kod nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-104">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="a8c8f-105">C# ve Visual Basic için Visual Studio IDE yalnızca tek dosya derlemeler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-105">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="a8c8f-106">Çoklu dosya derlemeleri oluşturmak istiyorsanız, Visual C++ komut satırı derleyicilerini veya Visual Studio 'Yu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-106">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="a8c8f-107">Çok dosyalı derlemeler yalnızca .NET Framework tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-107">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="a8c8f-108">Çoklu dosya derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8c8f-108">Create a multifile assembly</span></span>

1. <span data-ttu-id="a8c8f-109">Derlemedeki diğer modüller tarafından kod modüllerine başvuruda bulunulan ad alanlarını içeren tüm dosyaları derleyin.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-109">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="a8c8f-110">Kod modülleri için varsayılan uzantı *. netmodule*'dir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-110">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="a8c8f-111">Örneğin, dosyada adlı bir `Stringer` sınıf içeren bir ad alanı olduğunu varsayalım `myStringer` `Stringer` .</span><span class="sxs-lookup"><span data-stu-id="a8c8f-111">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="a8c8f-112">`Stringer`Sınıfı, `StringerMethod` konsola tek bir satır yazan adlı bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-112">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="a8c8f-113">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a8c8f-113">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="a8c8f-114">**/T:** derleyici seçeneğiyle *Modül* parametresini belirtme, dosyanın derleme yerine bir modül olarak derlenmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-114">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="a8c8f-115">Derleyici, bir derlemeye eklenebilecek *strger. netmodule*adlı bir modül oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-115">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="a8c8f-116">Kodda başvurulan diğer modülleri göstermek için gerekli derleyici seçeneklerini kullanarak diğer tüm modülleri derleyin.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-116">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="a8c8f-117">Bu adım, **/addmodule** derleyici seçeneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-117">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="a8c8f-118">Aşağıdaki örnekte, *istemci* adlı bir kod modülünün, `Main` 1. adımda oluşturulan *Stringer.dll* modülündeki bir yönteme başvuran bir giriş noktası yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-118">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="a8c8f-119">Bu kodu derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a8c8f-119">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="a8c8f-120">Bu modül gelecekteki bir adımda bir derlemeye eklenecağından **/t: Module** seçeneğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-120">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="a8c8f-121">*İstemci* içindeki kod, *strger. netmodule*içindeki kodla oluşturulan bir ad alanına başvurduğundan **/addmodule** seçeneğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-121">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="a8c8f-122">Derleyici, farklı bir modül olan *strger. netmodule*'e yönelik bir başvuru içeren *Client. netmodule* adlı bir modül üretir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-122">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a8c8f-123">C# ve Visual Basic derleyicileri, aşağıdaki iki farklı sözdizimleri kullanılarak çok dosyalı derlemeler doğrudan oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-123">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="a8c8f-124">İki derleme iki dosya derleme oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a8c8f-124">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="a8c8f-125">Bir derleme iki dosya derleme oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a8c8f-125">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="a8c8f-126">Derleme bildirimini içeren çıktı dosyasını oluşturmak için [derleme Bağlayıcısı 'nı (Al.exe)](../tools/al-exe-assembly-linker.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-126">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="a8c8f-127">Bu dosya, derlemenin parçası olan tüm modüller veya kaynaklar için başvuru bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-127">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="a8c8f-128">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="a8c8f-128">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="a8c8f-129">**Al** \<*module name*> \<*module name*>...</span><span class="sxs-lookup"><span data-stu-id="a8c8f-129">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="a8c8f-130">**/Main:** \<*method name*> **/Out:** \<*file name*> **/target:**\<*assembly file type*></span><span class="sxs-lookup"><span data-stu-id="a8c8f-130">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="a8c8f-131">Bu komutta, *Modül adı* bağımsız değişkenleri derlemeye dahil edilecek her modülün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-131">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="a8c8f-132">**/Main:** seçeneği derlemenin giriş noktası olan yöntem adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-132">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="a8c8f-133">**/Out:** seçeneği, derleme meta verilerini içeren çıkış dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-133">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="a8c8f-134">**/Target:** seçeneği, derlemenin bir konsol uygulaması yürütülebilir (*. exe*) dosyası, bir Windows yürütülebilir (*. Win*) dosyası veya bir kitaplık (*. lib*) dosyası olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-134">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="a8c8f-135">Aşağıdaki örnekte, *Al.exe* *myAssembly.exe*adlı konsol uygulaması yürütülebilir dosyası olan bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-135">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="a8c8f-136">Uygulama, *istemci. netmodule* ve *strger. netmodule*adlı iki modülden ve yalnızca derleme meta verilerini içeren *myAssembly.exe*adlı yürütülebilir dosya ile oluşur.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-136">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="a8c8f-137">Derlemenin giriş noktası, `Main` sınıfındaki, `MainClientApp` *Client.dll*bulunan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-137">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="a8c8f-138">Bir derlemenin içeriğini incelemek veya bir dosyanın derleme ya da modülle olduğunu anlamak için [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-138">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8c8f-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8c8f-139">See also</span></span>

- [<span data-ttu-id="a8c8f-140">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8c8f-140">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="a8c8f-141">Nasıl yapılır: derleme içeriğini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a8c8f-141">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="a8c8f-142">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="a8c8f-142">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a8c8f-143">Birden çok dosyalı derlemeler</span><span class="sxs-lookup"><span data-stu-id="a8c8f-143">Multifile assemblies</span></span>](multifile-assemblies.md)
