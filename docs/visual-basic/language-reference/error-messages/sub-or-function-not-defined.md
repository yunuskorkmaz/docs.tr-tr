---
title: Yordam veya İşlev tanımlı değil
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 9eb13d943f9f1cffc984847f7339111e06f5aa6b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373933"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="9d315-102">Sub veya Function tanımlı değil (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d315-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="9d315-103">Bir `Sub` veya `Function` çağrılabilmesi için tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d315-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="9d315-104">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d315-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="9d315-105">Yordam adı yanlış hatalı.</span><span class="sxs-lookup"><span data-stu-id="9d315-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="9d315-106">**Başvurular** iletişim kutusunda ilgili projeye açıkça bir başvuru eklemek zorunda kalmadan başka bir projeden yordam çağrılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="9d315-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="9d315-107">Çağıran yordama görünmeyen bir yordam belirtme.</span><span class="sxs-lookup"><span data-stu-id="9d315-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="9d315-108">Belirtilen kitaplıkta veya kod kaynağında olmayan bir Windows dinamik bağlantı kitaplığı (DLL) yordamını veya Macintosh kodu-kaynak yordamını bildirme.</span><span class="sxs-lookup"><span data-stu-id="9d315-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d315-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9d315-109">To correct this error</span></span>  
  
1. <span data-ttu-id="9d315-110">Yordam adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="9d315-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="9d315-111">**Başvurular** iletişim kutusunda çağırmak istediğiniz yordamı içeren projenin adını bulun.</span><span class="sxs-lookup"><span data-stu-id="9d315-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="9d315-112">Görünmezse, aramak için, **Gözden** geçirme düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9d315-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="9d315-113">Projenin adının solundaki onay kutusunu seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9d315-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="9d315-114">Yordamın adını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9d315-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d315-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d315-115">See also</span></span>

- [<span data-ttu-id="9d315-116">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="9d315-116">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="9d315-117">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="9d315-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="9d315-118">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="9d315-118">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="9d315-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="9d315-119">Function Statement</span></span>](../statements/function-statement.md)
