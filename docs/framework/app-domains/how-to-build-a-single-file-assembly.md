---
title: "Nasıl yapılır: Tek Dosyalı Derleme Oluşturma"
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
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd4472587cabc0ebfb2cb64e0bdc15a8d4778507
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="0422b-102">Nasıl yapılır: Tek Dosyalı Derleme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0422b-102">How to: Build a Single-File Assembly</span></span>
<span data-ttu-id="0422b-103">Tür bilgilerini ve uygulama, derleme basit türü olan tek dosyalı derleme içeren yanı sıra [derleme bildirimi](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="0422b-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="0422b-104">Komut satırı derleyicileri kullanabilirsiniz veya [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] tek dosyalı derleme oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0422b-104">You can use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to create a single-file assembly.</span></span> <span data-ttu-id="0422b-105">Varsayılan olarak, derleyici .exe uzantısına bir derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0422b-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]<span data-ttu-id="0422b-106">C# ve Visual Basic için yalnızca tek dosya derlemeleri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0422b-106"> for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="0422b-107">Birden çok dosya derlemeleri oluşturmak istiyorsanız, komut satırı derleyicileri kullanmalısınız veya [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] Visual C++ için.</span><span class="sxs-lookup"><span data-stu-id="0422b-107">If you want to create multifile assemblies, you must use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++.</span></span>  
  
 <span data-ttu-id="0422b-108">Aşağıdaki yordamları kullanarak komut satırı derleyicileri tek dosya derlemeleri oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0422b-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="0422b-109">Bir .exe uzantısına bir derleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0422b-109">To create an assembly with an .exe extension</span></span>  
  
1.  <span data-ttu-id="0422b-110">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="0422b-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="0422b-111">\<*derleyici komut*> \<*modül adı*></span><span class="sxs-lookup"><span data-stu-id="0422b-111">\<*compiler command*> \<*module name*></span></span>  
  
     <span data-ttu-id="0422b-112">Bu komutta *derleyici komut* derleyici komut, kod modülünde kullanılan dil ve *modül adı* derlemeye derlemek için kod modülü adıdır.</span><span class="sxs-lookup"><span data-stu-id="0422b-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="0422b-113">Aşağıdaki örnek adlı bir derleme oluşturur `myCode.exe` kod modülünden adlı `myCode`.</span><span class="sxs-lookup"><span data-stu-id="0422b-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="0422b-114">Bir .exe uzantılı bir derlemeyi oluşturun ve çıktı dosyası adını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="0422b-114">To create an assembly with an .exe extension and specify the output file name</span></span>  
  
1.  <span data-ttu-id="0422b-115">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="0422b-115">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="0422b-116">\<*derleyici komut*> **/out:**\<*dosya adı*> \<*modül adı*></span><span class="sxs-lookup"><span data-stu-id="0422b-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>  
  
     <span data-ttu-id="0422b-117">Bu komutta *derleyici komut* , kod modülünde kullanılan dilin derleyici komut *dosya adı* çıktı dosyası adı ve *modül adı* adıdır derlemeye derlemek için kod modülü.</span><span class="sxs-lookup"><span data-stu-id="0422b-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="0422b-118">Aşağıdaki örnek adlı bir derleme oluşturur `myAssembly.exe` kod modülünden adlı `myCode`.</span><span class="sxs-lookup"><span data-stu-id="0422b-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a><span data-ttu-id="0422b-119">Kitaplık derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0422b-119">Creating Library Assemblies</span></span>  
 <span data-ttu-id="0422b-120">Kitaplık derlemesi bir sınıf kitaplığı'na benzer.</span><span class="sxs-lookup"><span data-stu-id="0422b-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="0422b-121">Diğer derlemelerden tarafından başvurulan türler içerir, ancak yürütme başlamak için hiçbir giriş noktası yok.</span><span class="sxs-lookup"><span data-stu-id="0422b-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>  
  
#### <a name="to-create-a-library-assembly"></a><span data-ttu-id="0422b-122">Kitaplık derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0422b-122">To create a library assembly</span></span>  
  
1.  <span data-ttu-id="0422b-123">Komut satırında, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="0422b-123">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="0422b-124">\<*derleyici komut*> **/t:library** \< *modül adı*></span><span class="sxs-lookup"><span data-stu-id="0422b-124">\<*compiler command*> **/t:library** \<*module name*></span></span>  
  
     <span data-ttu-id="0422b-125">Bu komutta *derleyici komut* derleyici komut, kod modülünde kullanılan dil ve *modül adı* derlemeye derlemek için kod modülü adıdır.</span><span class="sxs-lookup"><span data-stu-id="0422b-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="0422b-126">Gibi diğer derleyici seçenekleri kullanabilir **/out:** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="0422b-126">You can also use other compiler options, such as the **/out:** option.</span></span>  
  
 <span data-ttu-id="0422b-127">Aşağıdaki örnek adlı bir kitaplık derlemesi oluşturur `myCodeAssembly.dll` kod modülünden adlı `myCode`.</span><span class="sxs-lookup"><span data-stu-id="0422b-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0422b-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0422b-128">See Also</span></span>  
 [<span data-ttu-id="0422b-129">Derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0422b-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="0422b-130">Birden çok dosya derlemeleri</span><span class="sxs-lookup"><span data-stu-id="0422b-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="0422b-131">Nasıl yapılır: birden fazla dosya derleme</span><span class="sxs-lookup"><span data-stu-id="0422b-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="0422b-132">Derlemelerle programlama</span><span class="sxs-lookup"><span data-stu-id="0422b-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
