---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 3e5c94cce8b16649854050855800ac1bf2fc6572
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580583"
---
# <a name="-addmodule"></a><span data-ttu-id="ae8f9-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="ae8f9-102">-addmodule</span></span>
<span data-ttu-id="ae8f9-103">Derleyicinin tüm kullanılabilir belirtilen dosyalar, şu anda derlemekte olduğunuz projeye kullandırmasına bilgileri yazın.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae8f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae8f9-104">Syntax</span></span>  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae8f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae8f9-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="ae8f9-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-106">Required.</span></span> <span data-ttu-id="ae8f9-107">Meta veriler içerir, ancak derleme bildirimleri içermeyen dosyaları virgülle ayrılmış liste.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="ae8f9-108">Boşluk içeren dosya adları tırnak işaretleri arasına ("").</span><span class="sxs-lookup"><span data-stu-id="ae8f9-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae8f9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae8f9-109">Remarks</span></span>  
 <span data-ttu-id="ae8f9-110">Tarafından listelenen dosyaların `fileList` parametresi ile oluşturulmalıdır `-target:module` seçeneğini veya başka bir derleyicinin eşdeğer `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="ae8f9-111">İle eklenen tüm modüller `-addmodule` çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="ae8f9-112">Diğer bir deyişle, bir modül herhangi bir dizinde derleme zamanında belirtebilirsiniz, ancak modülü, çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="ae8f9-113">Yüklü değilse, size bir <xref:System.TypeLoadException> hata.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="ae8f9-114">(Örtük veya açık) belirtirseniz herhangi[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) dışında seçeneği `-target:module` ile `-addmodule`, geçireceğiniz dosyaları `-addmodule` projenin derlemenin parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="ae8f9-115">Bir derleme varsa bir çıktı dosyası çalıştırmak için gerekli olan veya daha fazla dosya ile eklenen `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="ae8f9-116">Kullanım [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) bir derlemeyi içeren bir dosyanın meta verilerini almak için.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae8f9-117">`-addmodule` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae8f9-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae8f9-118">Example</span></span>  
 <span data-ttu-id="ae8f9-119">Aşağıdaki kod, bir modül oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="ae8f9-120">Aşağıdaki kod modülün türleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="ae8f9-121">Çalıştırdığınızda `t1`, bu çıkışları `802`.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae8f9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae8f9-122">See also</span></span>
- [<span data-ttu-id="ae8f9-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ae8f9-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ae8f9-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8f9-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="ae8f9-125">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8f9-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="ae8f9-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ae8f9-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
