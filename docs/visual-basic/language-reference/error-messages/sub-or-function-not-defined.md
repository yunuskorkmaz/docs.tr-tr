---
description: 'Daha fazla bilgi edinin: Sub veya Function tanımsız (Visual Basic)'
title: Yordam veya İşlev tanımlı değil
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 5726e8b23283b419577c468eee2344b234493425
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641388"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="5ba1c-103">Sub veya Function tanımlı değil (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ba1c-103">Sub or Function not defined (Visual Basic)</span></span>

<span data-ttu-id="5ba1c-104">Bir `Sub` veya `Function` çağrılabilmesi için tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-104">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="5ba1c-105">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5ba1c-105">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="5ba1c-106">Yordam adı yanlış hatalı.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-106">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="5ba1c-107">**Başvurular** iletişim kutusunda ilgili projeye açıkça bir başvuru eklemek zorunda kalmadan başka bir projeden yordam çağrılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-107">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="5ba1c-108">Çağıran yordama görünmeyen bir yordam belirtme.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-108">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="5ba1c-109">Belirtilen kitaplıkta veya kod kaynağında olmayan bir Windows dinamik bağlantı kitaplığı (DLL) yordamını veya Macintosh kodu-kaynak yordamını bildirme.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-109">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5ba1c-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5ba1c-110">To correct this error</span></span>  
  
1. <span data-ttu-id="5ba1c-111">Yordam adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-111">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="5ba1c-112">**Başvurular** iletişim kutusunda çağırmak istediğiniz yordamı içeren projenin adını bulun.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-112">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="5ba1c-113">Görünmezse, aramak için, **Gözden** geçirme düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-113">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="5ba1c-114">Projenin adının solundaki onay kutusunu seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-114">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="5ba1c-115">Yordamın adını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-115">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ba1c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ba1c-116">See also</span></span>

- [<span data-ttu-id="5ba1c-117">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="5ba1c-117">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="5ba1c-118">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="5ba1c-118">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="5ba1c-119">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="5ba1c-119">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="5ba1c-120">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="5ba1c-120">Function Statement</span></span>](../statements/function-statement.md)
