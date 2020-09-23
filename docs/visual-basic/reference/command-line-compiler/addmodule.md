---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2db122acc03056a9cb6f355119d4c4e6da6ed175
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097793"
---
# <a name="-addmodule"></a><span data-ttu-id="b1bf9-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="b1bf9-102">-addmodule</span></span>

<span data-ttu-id="b1bf9-103">Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bf9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b1bf9-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="b1bf9-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b1bf9-105">Arguments</span></span>  

 `fileList`  
 <span data-ttu-id="b1bf9-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-106">Required.</span></span> <span data-ttu-id="b1bf9-107">Meta veri içeren ancak derleme bildirimleri içermeyen dosyaların virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="b1bf9-108">Boşluk içeren dosya adları tırnak işaretleri ("") içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1bf9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1bf9-109">Remarks</span></span>  

 <span data-ttu-id="b1bf9-110">Parametresi tarafından listelenen dosyaların `fileList` `-target:module` seçeneğiyle oluşturulması veya başka bir derleyicinin eşdeğeri olması gerekir `-target:module` .</span><span class="sxs-lookup"><span data-stu-id="b1bf9-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="b1bf9-111">İle eklenen tüm modüller `-addmodule` , çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="b1bf9-112">Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="b1bf9-113">Aksi takdirde bir <xref:System.TypeLoadException> hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="b1bf9-114">İle dışında herhangi bir[hedef Visual Basic (](target.md) örtük veya açık) herhangi bir seçeneği belirtirseniz, bu `-target:module` `-addmodule` Dosya `-addmodule` projenin derlemesinin bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="b1bf9-115">Bir veya daha fazla dosya eklenmiş bir çıkış dosyası çalıştırmak için bütünleştirilmiş kod gereklidir `-addmodule` .</span><span class="sxs-lookup"><span data-stu-id="b1bf9-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="b1bf9-116">Derleme içeren bir dosyadan meta verileri içeri aktarmak için [-Reference (Visual Basic)](reference.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-116">Use [-reference (Visual Basic)](reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1bf9-117">`-addmodule`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1bf9-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1bf9-118">Example</span></span>  

 <span data-ttu-id="b1bf9-119">Aşağıdaki kod bir modül oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="b1bf9-120">Aşağıdaki kod modülün türlerini içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="b1bf9-121">Çalıştırdığınızda `t1` , çıkış çıkışları `802` .</span><span class="sxs-lookup"><span data-stu-id="b1bf9-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bf9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1bf9-122">See also</span></span>

- [<span data-ttu-id="b1bf9-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b1bf9-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b1bf9-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1bf9-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="b1bf9-125">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1bf9-125">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="b1bf9-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b1bf9-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
