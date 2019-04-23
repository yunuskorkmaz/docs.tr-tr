---
title: Sub veya Function tanımlı değil (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 397648618ea3764efafb5cff41deaef320bbeff3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294684"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="2264e-102">Sub veya Function tanımlı değil (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2264e-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="2264e-103">A `Sub` veya `Function` çağrılması için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2264e-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="2264e-104">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2264e-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="2264e-105">Yordam adı yazım hatası.</span><span class="sxs-lookup"><span data-stu-id="2264e-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="2264e-106">Bu projeye bir başvuru eklemeden açıkça başka bir projeden bir yordam çağırma çalışılırken **başvuruları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="2264e-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="2264e-107">Çağıran yordama görünür değil bir yordam belirtme.</span><span class="sxs-lookup"><span data-stu-id="2264e-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="2264e-108">Bir Windows dinamik bağlantı kitaplığı (DLL) yordamı veya belirtilen kitaplık veya kod kaynağı Macintosh kod kaynak yordamı bildirme.</span><span class="sxs-lookup"><span data-stu-id="2264e-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2264e-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2264e-109">To correct this error</span></span>  
  
1. <span data-ttu-id="2264e-110">Yordam adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2264e-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="2264e-111">Bulmak istediğiniz çağırmak için yordam içeren projenin adı **başvuruları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="2264e-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="2264e-112">Görünmüyorsa, tıklayın **Gözat** aramak için düğme.</span><span class="sxs-lookup"><span data-stu-id="2264e-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="2264e-113">Proje adının sol tarafındaki onay kutusunu işaretleyin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="2264e-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="2264e-114">Yordam adını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="2264e-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2264e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2264e-115">See also</span></span>

- [<span data-ttu-id="2264e-116">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="2264e-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="2264e-117">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="2264e-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="2264e-118">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2264e-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="2264e-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2264e-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
