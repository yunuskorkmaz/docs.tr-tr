---
title: "-target: module (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2b54ea9085ecc23d4a535d440d0634c997f22615
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="targetmodule-c-compiler-options"></a><span data-ttu-id="4657f-102">/target:module (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4657f-102">/target:module (C# Compiler Options)</span></span>
<span data-ttu-id="4657f-103">Bu seçenek, bir derleme bildirimi Oluştur değil derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="4657f-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4657f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4657f-104">Syntax</span></span>  
  
```console  
/target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="4657f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4657f-105">Remarks</span></span>  
 <span data-ttu-id="4657f-106">Varsayılan olarak, bu seçenek ile derleme tarafından oluşturulan çıktı dosyası .netmodule bir uzantısına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4657f-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="4657f-107">.NET Framework ortak dil çalışma zamanı tarafından bir derleme bildirimi sahip olmayan bir dosya yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="4657f-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="4657f-108">Ancak, böyle bir dosya yoluyla bir derlemenin derleme bildirimi içine birleştirilebilir [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4657f-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="4657f-109">Tek bir derleme birden fazla modülü oluşturduysanız [iç](../../../csharp/language-reference/keywords/internal.md) bir modüldeki türleri derlemedeki diğer modüllerle kullanılabilir olacak.</span><span class="sxs-lookup"><span data-stu-id="4657f-109">If more than one module is created in a single compilation, [internal](../../../csharp/language-reference/keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="4657f-110">Ne zaman bir modül başvurularında kod `internal` hem modülleri yoluyla bir derleme bildirimine birleştirilmesi gerekir sonra başka bir modülde türleri **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="4657f-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **/addmodule**.</span></span>  
  
 <span data-ttu-id="4657f-111">Visual Studio geliştirme ortamında, bir modül oluşturma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4657f-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="4657f-112">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="4657f-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4657f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4657f-113">Example</span></span>  
 <span data-ttu-id="4657f-114">Derleme `in.cs`, oluşturma `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="4657f-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc /target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4657f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4657f-115">See Also</span></span>  
 [<span data-ttu-id="4657f-116">/ target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4657f-116">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="4657f-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4657f-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
