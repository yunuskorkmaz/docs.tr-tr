---
title: 'Nasıl yapılır: tek dosya .NET Framework derleme oluşturma'
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
ms.openlocfilehash: b7cb06da74a21dab6f60f0d4c3ac1748fcbe4526
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644298"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="f0093-102">Nasıl yapılır: tek dosya .NET Framework derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0093-102">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="f0093-103">En basit derleme türü olan tek dosya derlemesi, tür bilgilerini ve uygulamayı, ayrıca [derleme bildirimini](../../standard/assembly/manifest.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="f0093-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="f0093-104">.NET Framework hedefleyen tek dosya derleme oluşturmak için komut satırı derleyicilerini veya Visual Studio 'Yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0093-104">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="f0093-105">Varsayılan olarak, derleyici *. exe* uzantılı bir derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0093-105">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="f0093-106">C# ve Visual Basic için Visual Studio yalnızca tek dosya derlemeler oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0093-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="f0093-107">Çoklu dosya derlemeleri oluşturmak istiyorsanız, komut satırı derleyicilerini veya Visual C++ kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0093-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="f0093-108">Aşağıdaki yordamlarda, komut satırı derleyicileri kullanılarak tek dosya derlemelerinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f0093-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="f0093-109">. Exe uzantısıyla derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0093-109">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="f0093-110">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="f0093-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="f0093-111">\<*derleyici komut*> \<*Modül adı*></span><span class="sxs-lookup"><span data-stu-id="f0093-111">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="f0093-112">Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="f0093-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="f0093-113">Aşağıdaki örnek, adlı `myCode`bir kod modülünden *MyCode. exe* adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0093-113">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="f0093-114">. Exe uzantısıyla bir derleme oluşturun ve çıkış dosyası adını belirtin</span><span class="sxs-lookup"><span data-stu-id="f0093-114">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="f0093-115">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="f0093-115">At the command prompt, type the following command:</span></span>

<span data-ttu-id="f0093-116">\<*Derleyici komutu*> **/Out:**\<*dosya adı*> \<*Modül adı*></span><span class="sxs-lookup"><span data-stu-id="f0093-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="f0093-117">Bu komutta *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu, *dosya adı* ise çıkış dosyası adı ve *Modül adı* , derlemeye derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="f0093-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="f0093-118">Aşağıdaki örnek, adlı `myCode`bir kod modülünden *MyAssembly. exe* adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0093-118">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="f0093-119">Kitaplık derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0093-119">Create library assemblies</span></span>
 <span data-ttu-id="f0093-120">Kitaplık derlemesi, sınıf kitaplığına benzer.</span><span class="sxs-lookup"><span data-stu-id="f0093-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="f0093-121">Diğer derlemeler tarafından başvurulacak türleri içerir, ancak yürütmeye başlamak için bir giriş noktası yoktur.</span><span class="sxs-lookup"><span data-stu-id="f0093-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="f0093-122">Bir kitaplık derlemesi oluşturmak için, komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="f0093-122">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="f0093-123">\<*Derleyici komutu*> **-t:Library** \< *Modül adı*></span><span class="sxs-lookup"><span data-stu-id="f0093-123">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="f0093-124">Bu komutta, *derleyici komutu* , kod modülünüzün kullandığı dilin derleyici komutu ve *Modül adı* derlemede derlenecek kod modülünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="f0093-124">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="f0093-125">**-Out:** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0093-125">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="f0093-126">Aşağıdaki örnek, adlı `myCode`bir kod modülünden *mycodeassembly. dll* adlı bir kitaplık derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0093-126">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="f0093-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0093-127">See also</span></span>

- [<span data-ttu-id="f0093-128">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0093-128">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="f0093-129">Çoklu dosya derlemeleri</span><span class="sxs-lookup"><span data-stu-id="f0093-129">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="f0093-130">Nasıl yapılır: çok dosyalı bütünleştirilmiş kod derleme</span><span class="sxs-lookup"><span data-stu-id="f0093-130">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="f0093-131">Derlemeler ile programlama</span><span class="sxs-lookup"><span data-stu-id="f0093-131">Program with assemblies</span></span>](../../standard/assembly/index.md)
