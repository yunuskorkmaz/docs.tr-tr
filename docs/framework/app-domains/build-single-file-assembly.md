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
ms.openlocfilehash: 482a973631e899b8d4bfc4640eef1ea26173605e
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104921"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="6ada8-104">Nasıl yapılır: tek dosya .NET Framework derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ada8-104">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="6ada8-105">En basit derleme türü olan tek dosya derlemesi, tür bilgilerini ve uygulamayı, ayrıca [derleme bildirimini](../../standard/assembly/manifest.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="6ada8-105">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="6ada8-106">.NET Framework hedefleyen tek dosya derleme oluşturmak için komut satırı derleyicilerini veya Visual Studio 'Yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ada8-106">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="6ada8-107">Varsayılan olarak, derleyici *. exe* uzantılı bir derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6ada8-107">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="6ada8-108">C# ve Visual Basic için Visual Studio yalnızca tek dosya derlemeler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ada8-108">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="6ada8-109">Çoklu dosya derlemeleri oluşturmak istiyorsanız, komut satırı derleyicilerini veya Visual C++ kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ada8-109">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="6ada8-110">Aşağıdaki yordamlarda, komut satırı derleyicileri kullanılarak tek dosya derlemelerinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ada8-110">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="6ada8-111">. Exe uzantısıyla derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ada8-111">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="6ada8-112">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6ada8-112">At the command prompt, type the following command:</span></span>

<span data-ttu-id="6ada8-113">\<*compiler command*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="6ada8-113">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="6ada8-114">Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="6ada8-114">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="6ada8-115">Aşağıdaki örnek, adlı bir kod modülünden *myCode.exe* adlı bir derleme oluşturur `myCode` .</span><span class="sxs-lookup"><span data-stu-id="6ada8-115">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="6ada8-116">. Exe uzantısıyla bir derleme oluşturun ve çıkış dosyası adını belirtin</span><span class="sxs-lookup"><span data-stu-id="6ada8-116">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="6ada8-117">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6ada8-117">At the command prompt, type the following command:</span></span>

<span data-ttu-id="6ada8-118">\<*compiler command*>**/Out:** \<*file name*>\<*module name*></span><span class="sxs-lookup"><span data-stu-id="6ada8-118">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="6ada8-119">Bu komutta *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu, *dosya adı* ise çıkış dosyası adı ve *Modül adı* , derlemeye derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="6ada8-119">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="6ada8-120">Aşağıdaki örnek, adlı bir kod modülünden *myAssembly.exe* adlı bir derleme oluşturur `myCode` .</span><span class="sxs-lookup"><span data-stu-id="6ada8-120">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="6ada8-121">Kitaplık derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ada8-121">Create library assemblies</span></span>
 <span data-ttu-id="6ada8-122">Kitaplık derlemesi, sınıf kitaplığına benzer.</span><span class="sxs-lookup"><span data-stu-id="6ada8-122">A library assembly is similar to a class library.</span></span> <span data-ttu-id="6ada8-123">Diğer derlemeler tarafından başvurulacak türleri içerir, ancak yürütmeye başlamak için bir giriş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="6ada8-123">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="6ada8-124">Bir kitaplık derlemesi oluşturmak için, komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6ada8-124">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="6ada8-125">\<*compiler command*>**-t:Library**\<*module name*></span><span class="sxs-lookup"><span data-stu-id="6ada8-125">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="6ada8-126">Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="6ada8-126">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="6ada8-127">**-Out:** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ada8-127">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="6ada8-128">Aşağıdaki örnek, adlı bir kod modülünden *myCodeAssembly.dll* adlı bir kitaplık derlemesi oluşturur `myCode` .</span><span class="sxs-lookup"><span data-stu-id="6ada8-128">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="6ada8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ada8-129">See also</span></span>

- [<span data-ttu-id="6ada8-130">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ada8-130">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="6ada8-131">Birden çok dosyalı derlemeler</span><span class="sxs-lookup"><span data-stu-id="6ada8-131">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="6ada8-132">Nasıl yapılır: Birden çok dosyalı derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ada8-132">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="6ada8-133">Derlemeler ile programlama</span><span class="sxs-lookup"><span data-stu-id="6ada8-133">Program with assemblies</span></span>](../../standard/assembly/index.md)
