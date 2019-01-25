---
title: -alır (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 9e5adcce85c4ca4863d28784a7d7f61c441a06c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588450"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="64b7f-102">-alır (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64b7f-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="64b7f-103">Ad alanları, belirtilen bir derlemesinden içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="64b7f-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b7f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64b7f-104">Syntax</span></span>  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="64b7f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="64b7f-105">Arguments</span></span>  
  
|<span data-ttu-id="64b7f-106">Terim</span><span class="sxs-lookup"><span data-stu-id="64b7f-106">Term</span></span>|<span data-ttu-id="64b7f-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="64b7f-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="64b7f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="64b7f-108">Required.</span></span> <span data-ttu-id="64b7f-109">İçeri aktarılacak ad alanlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="64b7f-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64b7f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64b7f-110">Remarks</span></span>  
 <span data-ttu-id="64b7f-111">`-imports` Seçeneği geçerli kaynak dosyalarının veya tüm başvurulan bütünleştirilmiş koddan küme içinde tanımlanan herhangi bir ad alanı içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="64b7f-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="64b7f-112">Belirtilen bir ad alanı üyelerini `-imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64b7f-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="64b7f-113">Kullanma [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) tek kaynak kodu dosyasında bir ad alanını kullanacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="64b7f-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="64b7f-114">Ayarlamak için/Visual Studio tümleşik geliştirme ortamında içeri aktarır</span><span class="sxs-lookup"><span data-stu-id="64b7f-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="64b7f-115">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="64b7f-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="64b7f-116">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="64b7f-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="64b7f-117">2.  Tıklayın **başvuruları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="64b7f-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="64b7f-118">3.  Ad alanı adının kutuya girin **kullanıcı içeri aktarma eklemek** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="64b7f-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="64b7f-119">4.  Tıklayın **kullanıcı içeri aktarma eklemek** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="64b7f-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="64b7f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="64b7f-120">Example</span></span>  
 <span data-ttu-id="64b7f-121">Aşağıdaki kod zaman derler `/imports:system.globalization` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="64b7f-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="64b7f-122">Bu olmadan başarılı derleme ya da gerektiren bir `Imports System.Globalization` deyimi kaynak kodu dosyasının başında eklenir veya özellik tam olarak nitelenmiş `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="64b7f-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span> 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="64b7f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64b7f-123">See also</span></span>
- [<span data-ttu-id="64b7f-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="64b7f-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="64b7f-125">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="64b7f-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="64b7f-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="64b7f-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
