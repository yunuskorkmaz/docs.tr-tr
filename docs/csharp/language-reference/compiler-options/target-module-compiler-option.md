---
description: '-target: Module (C# derleyici seçenekleri)'
title: '-target: Module (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 2074e170ab177c39fdf3954fa93ae4b666bf853d
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466059"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="6adfe-103">-target: Module (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6adfe-103">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="6adfe-104">Bu seçenek derleyicinin bir derleme bildirimi üretmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="6adfe-104">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6adfe-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6adfe-105">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="6adfe-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6adfe-106">Remarks</span></span>  
 <span data-ttu-id="6adfe-107">Varsayılan olarak, bu seçenekle derleme tarafından oluşturulan çıkış dosyası. netmodule uzantısına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6adfe-107">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="6adfe-108">Derleme bildirimine sahip olmayan bir dosya .NET çalışma zamanı tarafından yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="6adfe-108">A file that does not have an assembly manifest cannot be loaded by the .NET runtime.</span></span> <span data-ttu-id="6adfe-109">Ancak, bu tür bir dosya, [-addmodule](./addmodule-compiler-option.md)aracılığıyla bir derlemenin derleme bildirimine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="6adfe-109">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="6adfe-110">Tek bir derlemede birden fazla modül oluşturulduysa, bir modüldeki [iç](../keywords/internal.md) türler derlemedeki diğer modüller için kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6adfe-110">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="6adfe-111">Bir modüldeki kod `internal` , başka bir modüldeki türlere başvurduğunda, her iki modülün da **-addmodule**aracılığıyla bir derleme bildirimine dahil olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6adfe-111">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="6adfe-112">Visual Studio geliştirme ortamında modül oluşturma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6adfe-112">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="6adfe-113">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="6adfe-113">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6adfe-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="6adfe-114">Example</span></span>  
 <span data-ttu-id="6adfe-115">Derle `in.cs` , oluşturma `in.netmodule` :</span><span class="sxs-lookup"><span data-stu-id="6adfe-115">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6adfe-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6adfe-116">See also</span></span>

- [<span data-ttu-id="6adfe-117">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6adfe-117">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="6adfe-118">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6adfe-118">C# Compiler Options</span></span>](./index.md)
