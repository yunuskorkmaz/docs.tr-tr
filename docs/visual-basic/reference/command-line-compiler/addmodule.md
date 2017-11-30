---
title: /addmodule
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fff292605e125776ae25e667d4813d770ed0a0aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule"></a><span data-ttu-id="974f0-102">/addmodule</span><span class="sxs-lookup"><span data-stu-id="974f0-102">/addmodule</span></span>
<span data-ttu-id="974f0-103">Tüm hale getirmesine neden olur. şu anda derlediğiniz proje için belirtilen dosya veya dosyalar kullanılabilir bilgileri yazın.</span><span class="sxs-lookup"><span data-stu-id="974f0-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="974f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="974f0-104">Syntax</span></span>  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="974f0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="974f0-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="974f0-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="974f0-106">Required.</span></span> <span data-ttu-id="974f0-107">Meta veriler içeren ancak derleme bildirimlerinin içermeyen dosyaları virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="974f0-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="974f0-108">Boşluk içeren dosya adları tırnak işaretleri arasına ("").</span><span class="sxs-lookup"><span data-stu-id="974f0-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="974f0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="974f0-109">Remarks</span></span>  
 <span data-ttu-id="974f0-110">Tarafından listelenen dosyaları `fileList` parametresi ile oluşturulmalıdır `/target:module` seçeneğini veya başka bir derleyicinin eşdeğer ile `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="974f0-110">The files listed by the `fileList` parameter must be created with the `/target:module` option, or with another compiler's equivalent to `/target:module`.</span></span>  
  
 <span data-ttu-id="974f0-111">İle eklenen tüm modüller `/addmodule` çalışma zamanında çıktı dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="974f0-111">All modules added with `/addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="974f0-112">Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modül çalışma zamanında uygulama dizininde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="974f0-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="974f0-113">Değilse, size bir <xref:System.TypeLoadException> hata.</span><span class="sxs-lookup"><span data-stu-id="974f0-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="974f0-114">(Örtük veya açık olarak) belirtirseniz, tüm[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) dışında seçeneği `/target:module` ile `/addmodule`, geçireceğiniz dosyaları `/addmodule` projenin derleme bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="974f0-114">If you specify (implicitly or explicitly) any[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `/target:module` with `/addmodule`, the files you pass to `/addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="974f0-115">Bir derlemeyi varsa bir çıktı dosyasını çalıştırmak için gerekli ya da daha fazla dosya eklendi `/addmodule`.</span><span class="sxs-lookup"><span data-stu-id="974f0-115">An assembly is required to run an output file that has one or more files added with `/addmodule`.</span></span>  
  
 <span data-ttu-id="974f0-116">Kullanım [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) bir derleme içeren dosyadan meta verileri.</span><span class="sxs-lookup"><span data-stu-id="974f0-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="974f0-117">`/addmodule` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="974f0-117">The `/addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="974f0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="974f0-118">Example</span></span>  
 <span data-ttu-id="974f0-119">Aşağıdaki kod bir modül oluşturur.</span><span class="sxs-lookup"><span data-stu-id="974f0-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="974f0-120">Aşağıdaki kod modülün türlerini alır.</span><span class="sxs-lookup"><span data-stu-id="974f0-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="974f0-121">Çalıştırdığınızda `t1`, onu çıkarır `802`.</span><span class="sxs-lookup"><span data-stu-id="974f0-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974f0-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="974f0-122">See Also</span></span>  
 [<span data-ttu-id="974f0-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="974f0-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="974f0-124">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="974f0-124">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="974f0-125">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="974f0-125">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="974f0-126">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="974f0-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
