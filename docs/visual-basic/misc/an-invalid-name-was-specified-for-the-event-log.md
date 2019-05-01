---
title: Olay günlüğü için geçersiz ad belirtildi
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 2b9c934272d0f3392c845dcd2f0062a98dc50c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940679"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="1c7a3-102">Olay günlüğü için geçersiz ad belirtildi</span><span class="sxs-lookup"><span data-stu-id="1c7a3-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="1c7a3-103">Olay günlüğü için geçersiz ad belirtildi.</span><span class="sxs-lookup"><span data-stu-id="1c7a3-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="1c7a3-104">Genellikle bu ad, boş bir dosya adı veya çok uzun bir dosya adı geçersiz karakterler sonucudur.</span><span class="sxs-lookup"><span data-stu-id="1c7a3-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c7a3-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1c7a3-105">To correct this error</span></span>  
  
- <span data-ttu-id="1c7a3-106">Belirtilen ada sekiz karakterden daha uzun olması durumunda, diğer günlüklerinin adlarla çakışma olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c7a3-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="1c7a3-107">Yalnızca ilk sekiz karakterini adının benzersiz olup olmadığını belirlerken değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1c7a3-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="1c7a3-108">Bir yol sağlayarak, doğru bir şekilde ayrıştırılır emin olun.</span><span class="sxs-lookup"><span data-stu-id="1c7a3-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="1c7a3-109">Adında geçersiz karakter olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1c7a3-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="1c7a3-110">Dosya adında kullanılan karakterler `<`, `>`, `:`, `"`, `/`, `\`, ve `|`.</span><span class="sxs-lookup"><span data-stu-id="1c7a3-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c7a3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c7a3-111">See also</span></span>

- [<span data-ttu-id="1c7a3-112">Nasıl yapılır: Dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="1c7a3-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="1c7a3-113">Nasıl yapılır: Dosyayı yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="1c7a3-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
