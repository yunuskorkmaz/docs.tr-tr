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
ms.openlocfilehash: e8e9cd761263b3b61a4e6d3e33c5f7f875be7a1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="36bce-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36bce-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="36bce-103">Ad alanları belirtilen derlemesinden alır.</span><span class="sxs-lookup"><span data-stu-id="36bce-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36bce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36bce-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="36bce-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="36bce-105">Arguments</span></span>  
  
|<span data-ttu-id="36bce-106">Terim</span><span class="sxs-lookup"><span data-stu-id="36bce-106">Term</span></span>|<span data-ttu-id="36bce-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="36bce-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="36bce-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="36bce-108">Required.</span></span> <span data-ttu-id="36bce-109">İçeri aktarılacak ad alanları virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="36bce-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36bce-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36bce-110">Remarks</span></span>  
 <span data-ttu-id="36bce-111">`/imports` Seçeneği geçerli kaynak dosyaları veya başvurulan derlemeler küme içinde tanımlanan tüm ad alanı içe aktarır.</span><span class="sxs-lookup"><span data-stu-id="36bce-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="36bce-112">İle belirtilen bir ad alanı üyeleri `/imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36bce-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="36bce-113">Kullanmak [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) bir tek kaynak kodu dosyasına bir ad alanını kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="36bce-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="36bce-114">Ayarlanacak/Visual Studio tümleşik geliştirme ortamında alır</span><span class="sxs-lookup"><span data-stu-id="36bce-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="36bce-115">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="36bce-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="36bce-116">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="36bce-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="36bce-117">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="36bce-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="36bce-118">2.  Tıklatın **başvuruları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="36bce-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="36bce-119">3.  Ad alanı adı kutuya girin **ekleme kullanıcı alma** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="36bce-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="36bce-120">4.  Tıklatın **ekleme kullanıcı alma** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="36bce-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="36bce-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="36bce-121">Example</span></span>  
 <span data-ttu-id="36bce-122">Aşağıdaki kod ne zaman derler `/imports:system` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="36bce-122">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="36bce-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36bce-123">See Also</span></span>  
 [<span data-ttu-id="36bce-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="36bce-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="36bce-125">References ve Imports deyimi</span><span class="sxs-lookup"><span data-stu-id="36bce-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="36bce-126">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="36bce-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
