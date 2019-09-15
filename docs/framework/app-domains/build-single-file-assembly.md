---
title: 'Nasıl yapılır: Tek dosya .NET Framework derleme oluşturma'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98f06e62e1070f78faa77ef7d83fd80a62984684
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991244"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="6dc97-102">Nasıl yapılır: Tek dosya .NET Framework derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="6dc97-102">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="6dc97-103">En basit derleme türü olan tek dosya derlemesi, tür bilgilerini ve uygulamayı, ayrıca [derleme bildirimini](../../standard/assembly/manifest.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="6dc97-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="6dc97-104">.NET Framework hedefleyen tek dosya derleme oluşturmak için komut satırı derleyicilerini veya Visual Studio 'Yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6dc97-104">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="6dc97-105">Varsayılan olarak, derleyici *. exe* uzantılı bir derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dc97-105">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="6dc97-106">Ve Visual Basic için C# Visual Studio yalnızca tek dosya derlemeler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc97-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="6dc97-107">Çok dosyalı derlemeler oluşturmak istiyorsanız, komut satırı derleyicileri veya görsel C++kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6dc97-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="6dc97-108">Aşağıdaki yordamlarda, komut satırı derleyicileri kullanılarak tek dosya derlemelerinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6dc97-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="6dc97-109">. Exe uzantısıyla derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="6dc97-109">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="6dc97-110">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6dc97-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="6dc97-111">\<*derleyici komut*> modül\<*adı*></span><span class="sxs-lookup"><span data-stu-id="6dc97-111">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="6dc97-112">Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="6dc97-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="6dc97-113">Aşağıdaki örnek, adlı `myCode`bir kod modülünden *MyCode. exe* adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dc97-113">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="6dc97-114">. Exe uzantısıyla bir derleme oluşturun ve çıkış dosyası adını belirtin</span><span class="sxs-lookup"><span data-stu-id="6dc97-114">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="6dc97-115">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6dc97-115">At the command prompt, type the following command:</span></span>

<span data-ttu-id="6dc97-116">\<*Derleyici komutu*>  **/Out:** \<*Dosya*adımodül> adı\<></span><span class="sxs-lookup"><span data-stu-id="6dc97-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="6dc97-117">Bu komutta *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu, *dosya adı* ise çıkış dosyası adı ve *Modül adı* , derlemeye derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="6dc97-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="6dc97-118">Aşağıdaki örnek, adlı `myCode`bir kod modülünden *MyAssembly. exe* adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dc97-118">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="6dc97-119">Kitaplık derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6dc97-119">Create library assemblies</span></span>
 <span data-ttu-id="6dc97-120">Kitaplık derlemesi, sınıf kitaplığına benzer.</span><span class="sxs-lookup"><span data-stu-id="6dc97-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="6dc97-121">Diğer derlemeler tarafından başvurulacak türleri içerir, ancak yürütmeye başlamak için bir giriş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="6dc97-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="6dc97-122">Bir kitaplık derlemesi oluşturmak için, komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6dc97-122">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="6dc97-123">\<*Derleyici komutu*>  **-t:Library** \< *Modül adı*></span><span class="sxs-lookup"><span data-stu-id="6dc97-123">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="6dc97-124">Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="6dc97-124">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="6dc97-125">**-Out:** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6dc97-125">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="6dc97-126">Aşağıdaki örnek, adlı `myCode`bir kod modülünden *mycodeassembly. dll* adlı bir kitaplık derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dc97-126">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="6dc97-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dc97-127">See also</span></span>

- [<span data-ttu-id="6dc97-128">Derlemeler oluştur</span><span class="sxs-lookup"><span data-stu-id="6dc97-128">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="6dc97-129">Çoklu dosya derlemeleri</span><span class="sxs-lookup"><span data-stu-id="6dc97-129">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="6dc97-130">Nasıl yapılır: Çoklu dosya derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6dc97-130">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="6dc97-131">Bütünleştirilmiş kod içeren program</span><span class="sxs-lookup"><span data-stu-id="6dc97-131">Program with assemblies</span></span>](../../standard/assembly/program.md)
