---
title: "Geçersiz bir ad için olay günlüğünü belirtildi"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fc5a2e93541063a129efaa0ce08fc19a98372126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="692c6-102">Geçersiz bir ad için olay günlüğünü belirtildi</span><span class="sxs-lookup"><span data-stu-id="692c6-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="692c6-103">Geçersiz bir ad için olay günlüğünü belirtildi.</span><span class="sxs-lookup"><span data-stu-id="692c6-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="692c6-104">Genellikle bu ad, boş bir dosya adı veya çok uzun bir dosya adı geçersiz karakterler sonucudur.</span><span class="sxs-lookup"><span data-stu-id="692c6-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="692c6-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="692c6-105">To correct this error</span></span>  
  
-   <span data-ttu-id="692c6-106">Belirtilen ad sekiz karakterden fazla çakışma diğer olay günlüklerini adlara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="692c6-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="692c6-107">Yalnızca ilk sekiz karakter adının benzersiz olup olmadığını belirlerken değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="692c6-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="692c6-108">Bir yol sağlayarak, doğru ayrıştırılır emin olun.</span><span class="sxs-lookup"><span data-stu-id="692c6-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="692c6-109">Adında geçersiz karakter olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="692c6-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="692c6-110">Bir dosya adı kullanılamaz karakterler `<`, `>`, `:`, `"`, `/`, `\`, ve `|`.</span><span class="sxs-lookup"><span data-stu-id="692c6-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="692c6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="692c6-111">See Also</span></span>  
 [<span data-ttu-id="692c6-112">Nasıl yapılır: dosya yollarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="692c6-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="692c6-113">Nasıl yapılır: bir dosyayı yeniden adlandırın</span><span class="sxs-lookup"><span data-stu-id="692c6-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [<span data-ttu-id="692c6-114">Nasıl yapılır: oluşturma ve kaldırma özel olay günlükleri</span><span class="sxs-lookup"><span data-stu-id="692c6-114">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
