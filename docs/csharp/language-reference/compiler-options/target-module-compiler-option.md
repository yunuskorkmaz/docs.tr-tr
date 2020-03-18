---
title: -hedef:modül (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602445"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="f39a5-102">-hedef:modül (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f39a5-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="f39a5-103">Bu seçenek derleyicinin derleme bildirimi oluşturmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f39a5-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f39a5-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="f39a5-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f39a5-105">Remarks</span></span>  
 <span data-ttu-id="f39a5-106">Varsayılan olarak, bu seçenekle derleyerek oluşturulan çıkış dosyası .netmodule uzantısına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f39a5-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="f39a5-107">Derleme bildirimi olmayan bir dosya .NET Framework ortak dil çalışma süresi tarafından yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="f39a5-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="f39a5-108">Ancak, böyle bir dosya [-addmodule](./addmodule-compiler-option.md)yoluyla bir derleme derleme manifestosuna dahil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f39a5-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="f39a5-109">Tek bir derlemede birden fazla modül oluşturulursa, bir modüldeki [dahili](../keywords/internal.md) türler derlemedeki diğer modüller tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f39a5-109">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="f39a5-110">Bir modüldeki kod `internal` başka bir modüldeki türlere atıfta bulununca, her iki modül de **-addmodule**ile bir montaj manifestosuna dahil edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f39a5-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="f39a5-111">Visual Studio geliştirme ortamında modül oluşturma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f39a5-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="f39a5-112">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A></span><span class="sxs-lookup"><span data-stu-id="f39a5-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f39a5-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f39a5-113">Example</span></span>  
 <span data-ttu-id="f39a5-114">Derlemek `in.cs`, `in.netmodule`oluşturma :</span><span class="sxs-lookup"><span data-stu-id="f39a5-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f39a5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f39a5-115">See also</span></span>

- [<span data-ttu-id="f39a5-116">-hedef (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f39a5-116">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="f39a5-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f39a5-117">C# Compiler Options</span></span>](./index.md)
