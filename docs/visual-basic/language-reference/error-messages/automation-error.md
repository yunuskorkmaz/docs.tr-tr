---
title: Otomasyon hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: df153167bc8c73a2d3760c8d7db30dccfa468e35
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976157"
---
# <a name="automation-error"></a><span data-ttu-id="76d42-102">Otomasyon hatası</span><span class="sxs-lookup"><span data-stu-id="76d42-102">Automation error</span></span>

<span data-ttu-id="76d42-103">Bir yöntem yürütülürken veya bir nesne değişkeninin özelliği alınırken veya ayarlanırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="76d42-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="76d42-104">Hata, nesneyi oluşturan uygulama tarafından bildirildi.</span><span class="sxs-lookup"><span data-stu-id="76d42-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="76d42-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="76d42-105">To correct this error</span></span>  
  
1. <span data-ttu-id="76d42-106">Hatanın kaynağını ve yapısını öğrenmek için `Err` nesnesinin özelliklerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="76d42-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="76d42-107">Erişim deyimden hemen önce `On Error Resume Next` ifadesini kullanın ve ardından erişim deyimden sonra hataları kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="76d42-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d42-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76d42-108">See also</span></span>

- [<span data-ttu-id="76d42-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="76d42-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="76d42-110">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="76d42-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
