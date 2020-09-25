---
description: '-target: winexe (C# derleyici seçenekleri)'
title: '-target: winexe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 6e14a2aac427c7adfd69f66eaf624816b75f6ea2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168939"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="cefdb-103">-target: winexe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="cefdb-103">-target:winexe (C# Compiler Options)</span></span>

<span data-ttu-id="cefdb-104">**-Target: winexe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), Windows programı oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="cefdb-104">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cefdb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cefdb-105">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="cefdb-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cefdb-106">Remarks</span></span>  

 <span data-ttu-id="cefdb-107">Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="cefdb-107">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="cefdb-108">Bir Windows programı, .NET kitaplığından veya Windows API 'Leriyle bir kullanıcı arabirimi sağlayan bir programdır.</span><span class="sxs-lookup"><span data-stu-id="cefdb-108">A Windows program is one that provides a user interface from either the .NET library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="cefdb-109">Bir konsol uygulaması oluşturmak için [-target: exe](./target-exe-compiler-option.md) ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="cefdb-109">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="cefdb-110">Aksi belirtilmedikçe, çıkış dosyası [adı,](./out-compiler-option.md) [ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="cefdb-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="cefdb-111">Komut satırında belirtildiğinde, Windows programını oluşturmak için sonraki **dışarı** veya [-hedef](./target-compiler-option.md) seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cefdb-111">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="cefdb-112">Bir. exe dosyasına derlenen kaynak kodu dosyalarında bir ve yalnızca bir **ana** Yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cefdb-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="cefdb-113">[-Main](./main-compiler-option.md) seçeneği, kodunuzun bir **Main** yöntemi olan birden fazla sınıfa sahip olduğu durumlarda, hangi sınıfın **ana** yöntemi içerdiğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cefdb-113">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cefdb-114">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cefdb-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="cefdb-115">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="cefdb-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="cefdb-116">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cefdb-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="cefdb-117">**Çıktı türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cefdb-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="cefdb-118">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="cefdb-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cefdb-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="cefdb-119">Example</span></span>  

 <span data-ttu-id="cefdb-120">`in.cs`Bir Windows programında derle:</span><span class="sxs-lookup"><span data-stu-id="cefdb-120">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="cefdb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cefdb-121">See also</span></span>

- [<span data-ttu-id="cefdb-122">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="cefdb-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="cefdb-123">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="cefdb-123">C# Compiler Options</span></span>](./index.md)
