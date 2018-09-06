---
title: '-target: module (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 7cc0e48a7a4a3ec3f28c89e80fadf6aa7e1130f2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724584"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="4bea7-102">-target: module (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4bea7-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="4bea7-103">Bu seçenek, bir derleme bildirimi oluşturulmayacağını derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="4bea7-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bea7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bea7-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="4bea7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bea7-105">Remarks</span></span>  
 <span data-ttu-id="4bea7-106">Varsayılan olarak, bu seçenekle derlenerek oluşturulan çıktı dosyası, bir .netmodule uzantısına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4bea7-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="4bea7-107">.NET Framework ortak dil çalışma zamanı tarafından bir derleme bildirimi içermeyen bir dosya yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="4bea7-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="4bea7-108">Ancak, böyle bir dosya derleme bildirimi aracılığıyla bir derlemenin içine dahil edilebilir [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4bea7-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="4bea7-109">Tek bir derlemede birden fazla modülü oluşturulursa [iç](../../../csharp/language-reference/keywords/internal.md) bir modüldeki türler derlemeye diğer modüller için kullanıma sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="4bea7-109">If more than one module is created in a single compilation, [internal](../../../csharp/language-reference/keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="4bea7-110">Bir modül başvurularında kod `internal` iki modülü yoluyla bir derleme bildirimine birleştirilmesi gerekir sonra başka bir modülde türleri **- addmodule**.</span><span class="sxs-lookup"><span data-stu-id="4bea7-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="4bea7-111">Visual Studio geliştirme ortamında, bir modül oluşturma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4bea7-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="4bea7-112">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="4bea7-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bea7-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bea7-113">Example</span></span>  
 <span data-ttu-id="4bea7-114">Derleme `in.cs`, oluşturma `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="4bea7-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bea7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4bea7-115">See Also</span></span>  

- [<span data-ttu-id="4bea7-116">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4bea7-116">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="4bea7-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4bea7-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
