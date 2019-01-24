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
ms.openlocfilehash: 89139867cb0a207dbe82168015629fcb9e2fa6eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601902"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="4debb-102">-target: module (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4debb-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="4debb-103">Bu seçenek, bir derleme bildirimi oluşturulmayacağını derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="4debb-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4debb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4debb-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="4debb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4debb-105">Remarks</span></span>  
 <span data-ttu-id="4debb-106">Varsayılan olarak, bu seçenekle derlenerek oluşturulan çıktı dosyası, bir .netmodule uzantısına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4debb-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="4debb-107">.NET Framework ortak dil çalışma zamanı tarafından bir derleme bildirimi içermeyen bir dosya yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="4debb-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="4debb-108">Ancak, böyle bir dosya derleme bildirimi aracılığıyla bir derlemenin içine dahil edilebilir [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4debb-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="4debb-109">Tek bir derlemede birden fazla modülü oluşturulursa [iç](../../../csharp/language-reference/keywords/internal.md) bir modüldeki türler derlemeye diğer modüller için kullanıma sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="4debb-109">If more than one module is created in a single compilation, [internal](../../../csharp/language-reference/keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="4debb-110">Bir modül başvurularında kod `internal` iki modülü yoluyla bir derleme bildirimine birleştirilmesi gerekir sonra başka bir modülde türleri **- addmodule**.</span><span class="sxs-lookup"><span data-stu-id="4debb-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="4debb-111">Visual Studio geliştirme ortamında, bir modül oluşturma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4debb-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="4debb-112">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="4debb-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4debb-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4debb-113">Example</span></span>  
 <span data-ttu-id="4debb-114">Derleme `in.cs`, oluşturma `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="4debb-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4debb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4debb-115">See also</span></span>

- [<span data-ttu-id="4debb-116">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4debb-116">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="4debb-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4debb-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
