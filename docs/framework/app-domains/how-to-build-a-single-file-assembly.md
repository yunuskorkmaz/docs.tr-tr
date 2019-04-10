---
title: 'Nasıl yapılır: Tek Dosyalı Derleme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a73b2d8948c9a046fd77c02f1bcc87f5738105d9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304005"
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="6300f-102">Nasıl yapılır: Tek Dosyalı Derleme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6300f-102">How to: Build a Single-File Assembly</span></span>

<span data-ttu-id="6300f-103">Tür bilgilerini ve uygulama, derlemenin basit türü olan bir tek dosyalı bütünleştirilmiş kod içeren yanı sıra [derleme bildirimi](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="6300f-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="6300f-104">Komut satırı derleyicilerini veya Visual Studio, tek dosyalı derleme oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6300f-104">You can use command-line compilers or Visual Studio to create a single-file assembly.</span></span> <span data-ttu-id="6300f-105">Varsayılan olarak, derleyici bir .exe uzantılı bir derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6300f-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>

> [!NOTE]
> <span data-ttu-id="6300f-106">Visual Studio C# ve Visual Basic için yalnızca tek dosya derlemeleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6300f-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="6300f-107">Çok dosyalı derlemeler oluşturmak istiyorsanız, komut satırı derleyicilerini veya Visual C++ kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6300f-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="6300f-108">Aşağıdaki yordamlar, komut satırı derleyicilerini kullanarak tek dosya derlemeleri oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6300f-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="6300f-109">.Exe uzantısına bir derleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6300f-109">To create an assembly with an .exe extension</span></span>

1. <span data-ttu-id="6300f-110">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6300f-110">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="6300f-111">\<*derleyici komut*> \<*modül adı*></span><span class="sxs-lookup"><span data-stu-id="6300f-111">\<*compiler command*> \<*module name*></span></span>

     <span data-ttu-id="6300f-112">Bu komutta *derleyici komut* kod modülünde, kullanılan dil derleyici komut ve *modül adı* birleştirme dosyasına derlemek için kod modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="6300f-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="6300f-113">Aşağıdaki örnekte adlı bir derleme oluşturur `myCode.exe` adlı kod modülünde `myCode`.</span><span class="sxs-lookup"><span data-stu-id="6300f-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="6300f-114">Bir .exe uzantılı bir derleme oluşturun ve çıktı dosyası adını belirtin</span><span class="sxs-lookup"><span data-stu-id="6300f-114">To create an assembly with an .exe extension and specify the output file name</span></span>

1. <span data-ttu-id="6300f-115">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6300f-115">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="6300f-116">\<*derleyici komut*> **/out:**\<*dosya adı*> \<*modül adı*></span><span class="sxs-lookup"><span data-stu-id="6300f-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

     <span data-ttu-id="6300f-117">Bu komutta *derleyici komut* kod modülünde, kullanılan dil derleyici komut *dosya adı* çıkış dosyası adı ve *modül adı* adıdır bir birleştirme dosyasına derlemek için kod modülü.</span><span class="sxs-lookup"><span data-stu-id="6300f-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="6300f-118">Aşağıdaki örnekte adlı bir derleme oluşturur `myAssembly.exe` adlı kod modülünde `myCode`.</span><span class="sxs-lookup"><span data-stu-id="6300f-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a><span data-ttu-id="6300f-119">Kitaplık derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6300f-119">Creating Library Assemblies</span></span>
 <span data-ttu-id="6300f-120">Kitaplık derlemesi, bir sınıf kitaplığı'na benzer.</span><span class="sxs-lookup"><span data-stu-id="6300f-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="6300f-121">Diğer derlemeler tarafından başvurulan türleri içerir, ancak bu yürütme başlamak için hiç giriş noktası yok.</span><span class="sxs-lookup"><span data-stu-id="6300f-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

### <a name="to-create-a-library-assembly"></a><span data-ttu-id="6300f-122">Bir kitaplığı derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6300f-122">To create a library assembly</span></span>

1. <span data-ttu-id="6300f-123">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6300f-123">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="6300f-124">\<*derleyici komut*> **- t: Kitaplık** \< *modül adı*></span><span class="sxs-lookup"><span data-stu-id="6300f-124">\<*compiler command*> **-t:library** \<*module name*></span></span>

     <span data-ttu-id="6300f-125">Bu komutta *derleyici komut* kod modülünde, kullanılan dil derleyici komut ve *modül adı* birleştirme dosyasına derlemek için kod modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="6300f-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="6300f-126">Gibi diğer derleyici seçenekleri kullanabilirsiniz **-out:** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6300f-126">You can also use other compiler options, such as the **-out:** option.</span></span>

 <span data-ttu-id="6300f-127">Aşağıdaki örnekte adlı Kitaplık derlemesi oluşturur `myCodeAssembly.dll` adlı kod modülünde `myCode`.</span><span class="sxs-lookup"><span data-stu-id="6300f-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="6300f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6300f-128">See also</span></span>

- [<span data-ttu-id="6300f-129">Derlemeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6300f-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="6300f-130">Birden Çok Dosya Derlemeleri</span><span class="sxs-lookup"><span data-stu-id="6300f-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="6300f-131">Nasıl yapılır: Birden Fazla Dosya Derlemesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6300f-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="6300f-132">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="6300f-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)