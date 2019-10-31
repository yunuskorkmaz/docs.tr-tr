---
title: Otomasyon hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 25c3b71eb818223c58ab17d9be885033a5d4ded0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197040"
---
# <a name="automation-error"></a><span data-ttu-id="462fa-102">Otomasyon hatası</span><span class="sxs-lookup"><span data-stu-id="462fa-102">Automation error</span></span>
<span data-ttu-id="462fa-103">Bir yöntem yürütülürken veya bir nesne değişkeninin özelliği alınırken veya ayarlanırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="462fa-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="462fa-104">Hata, nesneyi oluşturan uygulama tarafından bildirildi.</span><span class="sxs-lookup"><span data-stu-id="462fa-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="462fa-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="462fa-105">To correct this error</span></span>  
  
1. <span data-ttu-id="462fa-106">Hatanın kaynağını ve yapısını öğrenmek için `Err` nesnesinin özelliklerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="462fa-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="462fa-107">Erişim deyimden hemen önce `On Error Resume Next` ifadesini kullanın ve ardından erişim deyimden sonra hataları kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="462fa-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462fa-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="462fa-108">See also</span></span>

- [<span data-ttu-id="462fa-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="462fa-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="462fa-110">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="462fa-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
