---
title: "-optimize (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74a338336d5878cb8d6f212076bb9f1eb7ef768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optimize-c-compiler-options"></a><span data-ttu-id="80bbb-102">/optimize (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="80bbb-102">/optimize (C# Compiler Options)</span></span>
<span data-ttu-id="80bbb-103">**/ Optimize** seçeneğini etkinleştirir veya çıkış dosyanızın daha küçük, daha hızlı ve daha verimli olmak için derleyici tarafından gerçekleştirilen iyileştirmeleri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="80bbb-103">The **/optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80bbb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80bbb-104">Syntax</span></span>  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="80bbb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80bbb-105">Remarks</span></span>  
 <span data-ttu-id="80bbb-106">**/ optimize** ayrıca çalışma zamanında kod iyileştirmek için ortak dil çalışma zamanı anlatır.</span><span class="sxs-lookup"><span data-stu-id="80bbb-106">**/optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="80bbb-107">Varsayılan olarak, en iyi duruma getirme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="80bbb-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="80bbb-108">Belirtin **/ optimize +** en iyi duruma getirme etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="80bbb-108">Specify **/optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="80bbb-109">Bir derlemesi tarafından kullanılacak bir modül oluştururken, aynı kullanmanız **/ optimize** olanlar derlemenin olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="80bbb-109">When building a module to be used by an assembly, use the same **/optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="80bbb-110">**/o** kısa biçimi olan **/ optimize**.</span><span class="sxs-lookup"><span data-stu-id="80bbb-110">**/o** is the short form of **/optimize**.</span></span>  
  
 <span data-ttu-id="80bbb-111">Birleştirmek olasıdır **/ optimize** ve [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="80bbb-111">It is possible to combine the **/optimize** and [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="80bbb-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="80bbb-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="80bbb-113">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="80bbb-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="80bbb-114">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="80bbb-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="80bbb-115">Değiştirme **kodu İyileştir** özelliği.</span><span class="sxs-lookup"><span data-stu-id="80bbb-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="80bbb-116">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="80bbb-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80bbb-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="80bbb-117">Example</span></span>  
 <span data-ttu-id="80bbb-118">Derleme `t2.cs` ve derleyici iyileştirmelerini etkinleştirme:</span><span class="sxs-lookup"><span data-stu-id="80bbb-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="80bbb-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80bbb-119">See Also</span></span>  
 [<span data-ttu-id="80bbb-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="80bbb-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="80bbb-121">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="80bbb-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
