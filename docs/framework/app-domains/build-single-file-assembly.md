---
title: 'Nasıl yapılır: tek dosya .NET Framework derleme oluşturma'
description: .NET ' te tek dosya derleme oluşturmayı öğrenin. Tek dosya derlemesi, .NET 'i hedefleyen bir kitaplık (. dll) olabilir veya bir yürütülebilir (. exe) dosya olabilir.
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: bdffa9417a7d52e9c825ca6455997b9bfa7408e4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271531"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="13627-104">Nasıl yapılır: tek dosya .NET Framework derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="13627-104">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="13627-105">En basit derleme türü olan tek dosya derlemesi, tür bilgilerini ve uygulamayı, ayrıca [derleme bildirimini](../../standard/assembly/manifest.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="13627-105">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="13627-106">.NET Framework hedefleyen tek dosya derleme oluşturmak için komut satırı derleyicilerini veya Visual Studio 'Yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13627-106">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="13627-107">Varsayılan olarak, derleyici *. exe* uzantılı bir derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13627-107">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="13627-108">C# ve Visual Basic için Visual Studio yalnızca tek dosya derlemeler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13627-108">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="13627-109">Çoklu dosya derlemeleri oluşturmak istiyorsanız, komut satırı derleyicilerini veya Visual C++ kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="13627-109">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="13627-110">Aşağıdaki yordamlarda, komut satırı derleyicileri kullanılarak tek dosya derlemelerinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="13627-110">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="13627-111">. Exe uzantısıyla derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="13627-111">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="13627-112">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="13627-112">At the command prompt, type the following command:</span></span>

<span data-ttu-id="13627-113">\<*compiler command*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="13627-113">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="13627-114">Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="13627-114">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="13627-115">Aşağıdaki örnek, adlı bir kod modülünden *myCode.exe* adlı bir derleme oluşturur `myCode` .</span><span class="sxs-lookup"><span data-stu-id="13627-115">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="13627-116">. Exe uzantısıyla bir derleme oluşturun ve çıkış dosyası adını belirtin</span><span class="sxs-lookup"><span data-stu-id="13627-116">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="13627-117">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="13627-117">At the command prompt, type the following command:</span></span>

<span data-ttu-id="13627-118">\<*compiler command*>**/Out:** \<*file name*>\<*module name*></span><span class="sxs-lookup"><span data-stu-id="13627-118">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="13627-119">Bu komutta *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu, *dosya adı* ise çıkış dosyası adı ve *Modül adı* , derlemeye derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="13627-119">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="13627-120">Aşağıdaki örnek, adlı bir kod modülünden *myAssembly.exe* adlı bir derleme oluşturur `myCode` .</span><span class="sxs-lookup"><span data-stu-id="13627-120">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="13627-121">Kitaplık derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="13627-121">Create library assemblies</span></span>

 <span data-ttu-id="13627-122">Kitaplık derlemesi, sınıf kitaplığına benzer.</span><span class="sxs-lookup"><span data-stu-id="13627-122">A library assembly is similar to a class library.</span></span> <span data-ttu-id="13627-123">Diğer derlemeler tarafından başvurulacak türleri içerir, ancak yürütmeye başlamak için bir giriş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="13627-123">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="13627-124">Bir kitaplık derlemesi oluşturmak için, komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="13627-124">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="13627-125">\<*compiler command*>**-t:Library**\<*module name*></span><span class="sxs-lookup"><span data-stu-id="13627-125">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="13627-126">Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="13627-126">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="13627-127">**-Out:** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13627-127">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="13627-128">Aşağıdaki örnek, adlı bir kod modülünden *myCodeAssembly.dll* adlı bir kitaplık derlemesi oluşturur `myCode` .</span><span class="sxs-lookup"><span data-stu-id="13627-128">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="13627-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13627-129">See also</span></span>

- [<span data-ttu-id="13627-130">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="13627-130">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="13627-131">Birden çok dosyalı derlemeler</span><span class="sxs-lookup"><span data-stu-id="13627-131">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="13627-132">Nasıl yapılır: Birden çok dosyalı derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="13627-132">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="13627-133">Derlemeler ile programlama</span><span class="sxs-lookup"><span data-stu-id="13627-133">Program with assemblies</span></span>](../../standard/assembly/index.md)
