---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 0e0915a2534f950cec074632a59750c3f96b679d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962454"
---
# <a name="-addmodule"></a><span data-ttu-id="d85b6-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="d85b6-102">-addmodule</span></span>
<span data-ttu-id="d85b6-103">Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d85b6-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d85b6-104">Syntax</span></span>  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="d85b6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d85b6-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="d85b6-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d85b6-106">Required.</span></span> <span data-ttu-id="d85b6-107">Meta veri içeren ancak derleme bildirimleri içermeyen dosyaların virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="d85b6-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="d85b6-108">Boşluk içeren dosya adları tırnak işaretleri ("") içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d85b6-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d85b6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d85b6-109">Remarks</span></span>  
 <span data-ttu-id="d85b6-110">`fileList` Parametresi tarafından listelenen dosyaların `-target:module` seçeneğiyle oluşturulması veya `-target:module`başka bir derleyicinin eşdeğeri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d85b6-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="d85b6-111">İle `-addmodule` eklenen tüm modüller, çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d85b6-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="d85b6-112">Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d85b6-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="d85b6-113">Aksi takdirde bir <xref:System.TypeLoadException> hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d85b6-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="d85b6-114">`-target:module` İle `-addmodule` [](../../../visual-basic/reference/command-line-compiler/target.md) dışındaherhangibirhedefVisualBasic(örtükveyaaçık)herhangibirseçeneğibelirtirseniz,budosyaprojeninderlemesininbirparçasıhaline`-addmodule`gelir.</span><span class="sxs-lookup"><span data-stu-id="d85b6-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="d85b6-115">Bir veya daha fazla dosya eklenmiş `-addmodule`bir çıkış dosyası çalıştırmak için bütünleştirilmiş kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d85b6-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="d85b6-116">Bütünleştirilmiş kod içeren bir dosyadan meta verileri içeri aktarmak için [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d85b6-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d85b6-117">Bu `-addmodule` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d85b6-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d85b6-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d85b6-118">Example</span></span>  
 <span data-ttu-id="d85b6-119">Aşağıdaki kod bir modül oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d85b6-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="d85b6-120">Aşağıdaki kod modülün türlerini içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="d85b6-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="d85b6-121">Çalıştırdığınızda `t1`, çıkış çıkışları `802`.</span><span class="sxs-lookup"><span data-stu-id="d85b6-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85b6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d85b6-122">See also</span></span>

- [<span data-ttu-id="d85b6-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d85b6-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d85b6-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d85b6-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="d85b6-125">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d85b6-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="d85b6-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d85b6-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
