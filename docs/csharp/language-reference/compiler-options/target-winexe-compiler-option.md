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
ms.openlocfilehash: 8a1be07455b54b375106fef1fb480d7abd2f1ca4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124727"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="21b53-103">-target: winexe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="21b53-103">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="21b53-104">**-Target: winexe** seçeneği derleyicinin YÜRÜTÜLEBILIR (exe), Windows programı oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="21b53-104">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b53-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="21b53-105">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="21b53-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21b53-106">Remarks</span></span>  
 <span data-ttu-id="21b53-107">Yürütülebilir dosya,. exe uzantısıyla oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="21b53-107">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="21b53-108">Windows programı, .NET Framework kitaplığından veya Windows API 'Leriyle bir kullanıcı arabirimi sağlayan bir programdır.</span><span class="sxs-lookup"><span data-stu-id="21b53-108">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="21b53-109">Bir konsol uygulaması oluşturmak için [-target: exe](./target-exe-compiler-option.md) ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="21b53-109">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="21b53-110">Aksi belirtilmedikçe, çıkış dosyası [adı,](./out-compiler-option.md) [ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="21b53-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="21b53-111">Komut satırında belirtildiğinde, Windows programını oluşturmak için sonraki **dışarı** veya [-hedef](./target-compiler-option.md) seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21b53-111">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="21b53-112">Bir. exe dosyasına derlenen kaynak kodu dosyalarında bir ve yalnızca bir **ana** Yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21b53-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="21b53-113">[-Main](./main-compiler-option.md) seçeneği, kodunuzun bir **Main** yöntemi olan birden fazla sınıfa sahip olduğu durumlarda, hangi sınıfın **ana** yöntemi içerdiğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="21b53-113">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="21b53-114">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="21b53-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="21b53-115">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="21b53-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="21b53-116">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="21b53-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="21b53-117">**Çıktı türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="21b53-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="21b53-118">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="21b53-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21b53-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="21b53-119">Example</span></span>  
 <span data-ttu-id="21b53-120">`in.cs`Bir Windows programında derle:</span><span class="sxs-lookup"><span data-stu-id="21b53-120">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="21b53-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21b53-121">See also</span></span>

- [<span data-ttu-id="21b53-122">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="21b53-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="21b53-123">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="21b53-123">C# Compiler Options</span></span>](./index.md)
