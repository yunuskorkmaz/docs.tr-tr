---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: fbe3634d1fbc03acd56ef7276d65fd54493b9806
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002422"
---
# <a name="-addmodule"></a><span data-ttu-id="3e392-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="3e392-102">-addmodule</span></span>
<span data-ttu-id="3e392-103">Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="3e392-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e392-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e392-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e392-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3e392-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="3e392-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3e392-106">Required.</span></span> <span data-ttu-id="3e392-107">Meta veri içeren ancak derleme bildirimleri içermeyen dosyaların virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="3e392-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="3e392-108">Boşluk içeren dosya adları tırnak işaretleri ("") içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e392-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e392-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e392-109">Remarks</span></span>  
 <span data-ttu-id="3e392-110">@No__t-0 parametresiyle listelenen dosyalar `-target:module` seçeneği ile oluşturulmalıdır ya da başka bir derleyicinin `-target:module` ' ye denk gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e392-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="3e392-111">@No__t-0 ile eklenen tüm modüller, çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e392-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="3e392-112">Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e392-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="3e392-113">Değilse, @no__t 0 hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="3e392-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="3e392-114">@No__t-2 ile `-target:module` dışında herhangi bir[hedef Visual Basic (](../../../visual-basic/reference/command-line-compiler/target.md) örtük veya açık) seçeneğini belirtirseniz, `-addmodule` ' e geçirdiğiniz dosyalar projenin derlemesinin bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="3e392-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="3e392-115">@No__t-0 ile eklenen bir veya daha fazla dosya içeren bir çıkış dosyası çalıştırmak için bütünleştirilmiş kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e392-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="3e392-116">Bütünleştirilmiş kod içeren bir dosyadan meta verileri içeri aktarmak için [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e392-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e392-117">@No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e392-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e392-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e392-118">Example</span></span>  
 <span data-ttu-id="3e392-119">Aşağıdaki kod bir modül oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e392-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="3e392-120">Aşağıdaki kod modülün türlerini içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="3e392-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="3e392-121">@No__t-0 ' ı çalıştırdığınızda `802` çıkışı yapılır.</span><span class="sxs-lookup"><span data-stu-id="3e392-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e392-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e392-122">See also</span></span>

- [<span data-ttu-id="3e392-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3e392-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3e392-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e392-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="3e392-125">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e392-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="3e392-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3e392-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
