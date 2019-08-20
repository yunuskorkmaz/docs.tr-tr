---
title: '-target: Module (C# derleyici seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602445"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="c5c9e-102">-target: Module (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c5c9e-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="c5c9e-103">Bu seçenek derleyicinin bir derleme bildirimi üretmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5c9e-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="c5c9e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5c9e-105">Remarks</span></span>  
 <span data-ttu-id="c5c9e-106">Varsayılan olarak, bu seçenekle derleme tarafından oluşturulan çıkış dosyası. netmodule uzantısına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="c5c9e-107">Derleme bildirimine sahip olmayan bir dosya, .NET Framework ortak dil çalışma zamanı tarafından yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="c5c9e-108">Ancak, bu tür bir dosya, [-addmodule](./addmodule-compiler-option.md)aracılığıyla bir derlemenin derleme bildirimine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="c5c9e-109">Tek bir derlemede birden fazla modül oluşturulduysa, bir modüldeki [iç](../keywords/internal.md) türler derlemedeki diğer modüller için kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-109">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="c5c9e-110">Bir modüldeki kod, başka bir `internal` modüldeki türlere başvurduğunda, her iki modülün da **-addmodule**aracılığıyla bir derleme bildirimine dahil olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="c5c9e-111">Visual Studio geliştirme ortamında modül oluşturma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="c5c9e-112">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5c9e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5c9e-113">Example</span></span>  
 <span data-ttu-id="c5c9e-114">Derle `in.cs`, oluşturma `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="c5c9e-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5c9e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5c9e-115">See also</span></span>

- [<span data-ttu-id="c5c9e-116">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c5c9e-116">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="c5c9e-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c5c9e-117">C# Compiler Options</span></span>](./index.md)
