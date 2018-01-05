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
ms.openlocfilehash: 76e4082710a6786ec5e743ce606e849637c26512
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="89cd6-102">Geçersiz bir ad için olay günlüğünü belirtildi</span><span class="sxs-lookup"><span data-stu-id="89cd6-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="89cd6-103">Geçersiz bir ad için olay günlüğünü belirtildi.</span><span class="sxs-lookup"><span data-stu-id="89cd6-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="89cd6-104">Genellikle bu ad, boş bir dosya adı veya çok uzun bir dosya adı geçersiz karakterler sonucudur.</span><span class="sxs-lookup"><span data-stu-id="89cd6-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="89cd6-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="89cd6-105">To correct this error</span></span>  
  
-   <span data-ttu-id="89cd6-106">Belirtilen ad sekiz karakterden fazla çakışma diğer olay günlüklerini adlara sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="89cd6-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="89cd6-107">Yalnızca ilk sekiz karakter adının benzersiz olup olmadığını belirlerken değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="89cd6-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="89cd6-108">Bir yol sağlayarak, doğru ayrıştırılır emin olun.</span><span class="sxs-lookup"><span data-stu-id="89cd6-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="89cd6-109">Adında geçersiz karakter olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="89cd6-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="89cd6-110">Bir dosya adı kullanılamaz karakterler `<`, `>`, `:`, `"`, `/`, `\`, ve `|`.</span><span class="sxs-lookup"><span data-stu-id="89cd6-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89cd6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89cd6-111">See Also</span></span>  
 [<span data-ttu-id="89cd6-112">Nasıl Yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="89cd6-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="89cd6-113">Nasıl Yapılır: Dosyayı Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="89cd6-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 
