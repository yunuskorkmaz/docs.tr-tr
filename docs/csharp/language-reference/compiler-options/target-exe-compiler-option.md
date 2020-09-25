---
description: '-target: exe (C# derleyici seçenekleri)'
title: '-target: exe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: ae1706f1ecdd396e24711070d19420faa6d34761
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193770"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="3f69c-103">-target: exe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3f69c-103">-target:exe (C# Compiler Options)</span></span>

<span data-ttu-id="3f69c-104">**-Target: exe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), konsol uygulaması oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3f69c-104">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f69c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3f69c-105">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f69c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f69c-106">Remarks</span></span>  

 <span data-ttu-id="3f69c-107">**-Target: exe** seçeneği varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="3f69c-107">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="3f69c-108">Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="3f69c-108">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="3f69c-109">Bir Windows program yürütülebilir dosyası oluşturmak için [-target: winexe](./target-winexe-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f69c-109">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="3f69c-110">Aksi belirtilmedikçe, çıkış dosyası [adı,](./out-compiler-option.md) [ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="3f69c-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="3f69c-111">Komut satırında belirtildiğinde, bir sonraki **-Out** veya **-target: Module** seçeneğine kadar olan tüm dosyalar,. exe dosyasını oluşturmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="3f69c-111">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="3f69c-112">Bir. exe dosyasına derlenen kaynak kodu dosyalarında bir ve yalnızca bir **ana** Yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3f69c-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="3f69c-113">[-Main](./main-compiler-option.md) derleyici seçeneği, kodunuzun bir **Main** yöntemi olan birden fazla sınıfa sahip olduğu durumlarda **Main** yöntemini hangi sınıfın içerdiğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f69c-113">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3f69c-114">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3f69c-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3f69c-115">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="3f69c-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="3f69c-116">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3f69c-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="3f69c-117">**Çıktı türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3f69c-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="3f69c-118">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="3f69c-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f69c-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f69c-119">Example</span></span>  

 <span data-ttu-id="3f69c-120">Aşağıdaki komut satırlarından her biri derler `in.cs` , şunu oluşturur `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="3f69c-120">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f69c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f69c-121">See also</span></span>

- [<span data-ttu-id="3f69c-122">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3f69c-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="3f69c-123">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="3f69c-123">C# Compiler Options</span></span>](./index.md)
