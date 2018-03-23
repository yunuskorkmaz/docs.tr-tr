---
title: -içeri aktarmalar (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d81e9d2bd55e6e38e337805b950a0b85680d129b
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="8c9b2-102">-içeri aktarmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c9b2-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="8c9b2-103">Ad alanları belirtilen derlemesinden alır.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c9b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c9b2-104">Syntax</span></span>  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c9b2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8c9b2-105">Arguments</span></span>  
  
|<span data-ttu-id="8c9b2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="8c9b2-106">Term</span></span>|<span data-ttu-id="8c9b2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="8c9b2-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="8c9b2-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-108">Required.</span></span> <span data-ttu-id="8c9b2-109">İçeri aktarılacak ad alanları virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c9b2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c9b2-110">Remarks</span></span>  
 <span data-ttu-id="8c9b2-111">`-imports` Seçeneği geçerli kaynak dosyaları veya başvurulan derlemeler küme içinde tanımlanan tüm ad alanı içe aktarır.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="8c9b2-112">İle belirtilen bir ad alanı üyeleri `-imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="8c9b2-113">Kullanmak [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) bir tek kaynak kodu dosyasına bir ad alanını kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="8c9b2-114">Ayarlanacak/Visual Studio tümleşik geliştirme ortamında alır</span><span class="sxs-lookup"><span data-stu-id="8c9b2-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8c9b2-115">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8c9b2-116">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8c9b2-117">2.  Tıklatın **başvuruları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="8c9b2-118">3.  Ad alanı adı kutuya girin **ekleme kullanıcı alma** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="8c9b2-119">4.  Tıklatın **ekleme kullanıcı alma** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8c9b2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c9b2-120">Example</span></span>  
 <span data-ttu-id="8c9b2-121">Aşağıdaki kod ne zaman derler `/imports:system.globalization` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="8c9b2-122">Bu olmadan başarılı derleme ya da gerektiren bir `Imports System.Globalization` deyimi dahil kaynak kodu dosyasının başında veya özelliği tam olarak `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span> 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8c9b2-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-123">See Also</span></span>  
 [<span data-ttu-id="8c9b2-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="8c9b2-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8c9b2-125">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="8c9b2-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="8c9b2-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="8c9b2-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
