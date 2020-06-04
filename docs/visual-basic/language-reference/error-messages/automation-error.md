---
title: Otomasyon hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: d62ba57db8bffefb2cfebed705251d87fe285602
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409900"
---
# <a name="automation-error"></a><span data-ttu-id="13ec8-102">Otomasyon hatası</span><span class="sxs-lookup"><span data-stu-id="13ec8-102">Automation error</span></span>

<span data-ttu-id="13ec8-103">Bir yöntem yürütülürken veya bir nesne değişkeninin özelliği alınırken veya ayarlanırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="13ec8-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="13ec8-104">Hata, nesneyi oluşturan uygulama tarafından bildirildi.</span><span class="sxs-lookup"><span data-stu-id="13ec8-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13ec8-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="13ec8-105">To correct this error</span></span>  
  
1. <span data-ttu-id="13ec8-106">`Err`Hatanın kaynağını ve yapısını öğrenmek için nesnenin özelliklerini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="13ec8-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="13ec8-107">`On Error Resume Next`' İ erişen deyimden hemen önce kullanın ve ardından erişim deyimden hemen sonra hata olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="13ec8-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ec8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13ec8-108">See also</span></span>

- [<span data-ttu-id="13ec8-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="13ec8-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="13ec8-110">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="13ec8-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
