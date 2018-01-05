---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cdb7cff2221930113d6b49a640da0844f175f1b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="69ab3-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69ab3-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="69ab3-103">Ad alanları belirtilen derlemesinden alır.</span><span class="sxs-lookup"><span data-stu-id="69ab3-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69ab3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69ab3-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="69ab3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="69ab3-105">Arguments</span></span>  
  
|<span data-ttu-id="69ab3-106">Terim</span><span class="sxs-lookup"><span data-stu-id="69ab3-106">Term</span></span>|<span data-ttu-id="69ab3-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="69ab3-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="69ab3-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="69ab3-108">Required.</span></span> <span data-ttu-id="69ab3-109">İçeri aktarılacak ad alanları virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="69ab3-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69ab3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69ab3-110">Remarks</span></span>  
 <span data-ttu-id="69ab3-111">`/imports` Seçeneği geçerli kaynak dosyaları veya başvurulan derlemeler küme içinde tanımlanan tüm ad alanı içe aktarır.</span><span class="sxs-lookup"><span data-stu-id="69ab3-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="69ab3-112">İle belirtilen bir ad alanı üyeleri `/imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="69ab3-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="69ab3-113">Kullanmak [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) bir tek kaynak kodu dosyasına bir ad alanını kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="69ab3-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="69ab3-114">Ayarlanacak/Visual Studio tümleşik geliştirme ortamında alır</span><span class="sxs-lookup"><span data-stu-id="69ab3-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="69ab3-115">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="69ab3-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="69ab3-116">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="69ab3-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="69ab3-117">2.  Tıklatın **başvuruları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="69ab3-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="69ab3-118">3.  Ad alanı adı kutuya girin **ekleme kullanıcı alma** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69ab3-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="69ab3-119">4.  Tıklatın **ekleme kullanıcı alma** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69ab3-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="69ab3-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="69ab3-120">Example</span></span>  
 <span data-ttu-id="69ab3-121">Aşağıdaki kod ne zaman derler `/imports:system` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="69ab3-121">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="69ab3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69ab3-122">See Also</span></span>  
 [<span data-ttu-id="69ab3-123">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="69ab3-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="69ab3-124">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="69ab3-124">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="69ab3-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="69ab3-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
