---
title: Olay günlüğü için geçersiz bir ad belirtildi
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 70b1de2a3776a9c68260cc431b65e754d7247a0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412929"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="40940-102">Olay günlüğü için geçersiz bir ad belirtildi</span><span class="sxs-lookup"><span data-stu-id="40940-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="40940-103">Olay günlüğü için geçersiz bir ad belirtildi.</span><span class="sxs-lookup"><span data-stu-id="40940-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="40940-104">Genellikle bu, ad, boş bir dosya adı veya çok uzun bir dosya adı içindeki geçersiz karakterlerin bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="40940-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40940-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="40940-105">To correct this error</span></span>  
  
- <span data-ttu-id="40940-106">Belirtilen ad sekiz karakterden daha büyükse, diğer olay günlüklerinin adlarıyla çakışma olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="40940-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="40940-107">Adın benzersiz olup olmadığı belirlenirken yalnızca ilk sekiz karakter değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="40940-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="40940-108">Bir yol gerekiyorsa, doğru ayrıştırıladığına emin olun.</span><span class="sxs-lookup"><span data-stu-id="40940-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="40940-109">Adda geçersiz karakter olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="40940-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="40940-110">Dosya adında kullanılamayan karakterler,,,,, `<` `>` `:` `"` `/` `\` , ve içerir `|` .</span><span class="sxs-lookup"><span data-stu-id="40940-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40940-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40940-111">See also</span></span>

- [<span data-ttu-id="40940-112">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="40940-112">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="40940-113">Nasıl yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="40940-113">How to: Rename a File</span></span>](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
