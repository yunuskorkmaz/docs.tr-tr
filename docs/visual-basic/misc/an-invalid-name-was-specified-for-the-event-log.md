---
description: 'Daha fazla bilgi edinin: olay günlüğü için geçersiz bir ad belirtildi'
title: Olay günlüğü için geçersiz bir ad belirtildi
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 4786483fe0b1ae32a16b67bfb4f406587719011b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787376"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="e2595-103">Olay günlüğü için geçersiz bir ad belirtildi</span><span class="sxs-lookup"><span data-stu-id="e2595-103">An invalid name was specified for the event log</span></span>

<span data-ttu-id="e2595-104">Olay günlüğü için geçersiz bir ad belirtildi.</span><span class="sxs-lookup"><span data-stu-id="e2595-104">An invalid name was specified for the event log.</span></span> <span data-ttu-id="e2595-105">Genellikle bu, ad, boş bir dosya adı veya çok uzun bir dosya adı içindeki geçersiz karakterlerin bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="e2595-105">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e2595-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e2595-106">To correct this error</span></span>  
  
- <span data-ttu-id="e2595-107">Belirtilen ad sekiz karakterden daha büyükse, diğer olay günlüklerinin adlarıyla çakışma olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2595-107">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="e2595-108">Adın benzersiz olup olmadığı belirlenirken yalnızca ilk sekiz karakter değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e2595-108">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="e2595-109">Bir yol gerekiyorsa, doğru ayrıştırıladığına emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2595-109">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="e2595-110">Adda geçersiz karakter olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2595-110">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="e2595-111">Dosya adında kullanılamayan karakterler,,,,, `<` `>` `:` `"` `/` `\` , ve içerir `|` .</span><span class="sxs-lookup"><span data-stu-id="e2595-111">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2595-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2595-112">See also</span></span>

- [<span data-ttu-id="e2595-113">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="e2595-113">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="e2595-114">Nasıl yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="e2595-114">How to: Rename a File</span></span>](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
