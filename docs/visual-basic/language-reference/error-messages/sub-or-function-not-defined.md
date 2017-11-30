---
title: "Sub veya Function tanımlı değil (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="4f6d3-102">Sub veya Function tanımlı değil (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f6d3-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="4f6d3-103">A `Sub` veya `Function` çağrılması için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="4f6d3-104">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4f6d3-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="4f6d3-105">Yordam adı yazım hatası.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="4f6d3-106">Bu projeye ait bir başvuru açıkça eklemeden başka bir projeden bir yordam çağırma çalışılırken **başvuruları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="4f6d3-107">GetTypeId yordamını görünür değil bir yordam belirtme.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="4f6d3-108">Bir Windows dinamik bağlantı kitaplığı (DLL) yordamı veya belirtilen kitaplığı veya kod kaynağında değil Macintosh kod kaynak yordamı bildirme.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f6d3-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4f6d3-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="4f6d3-110">Yordam adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="4f6d3-111">Bulmak istediğiniz çağırmak için yordamı içeren projesinin adı **başvuruları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="4f6d3-112">Görünmüyorsa, tıklatın **Gözat** aramak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="4f6d3-113">Proje adının solundaki onay kutusunu seçin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="4f6d3-114">Yordam adını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f6d3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f6d3-115">See Also</span></span>  
 [<span data-ttu-id="4f6d3-116">Hata türleri</span><span class="sxs-lookup"><span data-stu-id="4f6d3-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="4f6d3-117">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="4f6d3-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="4f6d3-118">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="4f6d3-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="4f6d3-119">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="4f6d3-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
