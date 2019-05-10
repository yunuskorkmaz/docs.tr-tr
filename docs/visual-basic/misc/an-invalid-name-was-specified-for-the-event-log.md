---
title: Olay günlüğü için geçersiz ad belirtildi
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 05f37239510482de218847f069dc74cbef91f398
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609176"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="584bc-102">Olay günlüğü için geçersiz ad belirtildi</span><span class="sxs-lookup"><span data-stu-id="584bc-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="584bc-103">Olay günlüğü için geçersiz ad belirtildi.</span><span class="sxs-lookup"><span data-stu-id="584bc-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="584bc-104">Genellikle bu ad, boş bir dosya adı veya çok uzun bir dosya adı geçersiz karakterler sonucudur.</span><span class="sxs-lookup"><span data-stu-id="584bc-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="584bc-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="584bc-105">To correct this error</span></span>  
  
- <span data-ttu-id="584bc-106">Belirtilen ada sekiz karakterden daha uzun olması durumunda, diğer günlüklerinin adlarla çakışma olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="584bc-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="584bc-107">Yalnızca ilk sekiz karakterini adının benzersiz olup olmadığını belirlerken değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="584bc-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="584bc-108">Bir yol sağlayarak, doğru bir şekilde ayrıştırılır emin olun.</span><span class="sxs-lookup"><span data-stu-id="584bc-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="584bc-109">Adında geçersiz karakter olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="584bc-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="584bc-110">Dosya adında kullanılan karakterler `<`, `>`, `:`, `"`, `/`, `\`, ve `|`.</span><span class="sxs-lookup"><span data-stu-id="584bc-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="584bc-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="584bc-111">See also</span></span>

- [<span data-ttu-id="584bc-112">Nasıl yapılır: Dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="584bc-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="584bc-113">Nasıl yapılır: Dosyayı yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="584bc-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
