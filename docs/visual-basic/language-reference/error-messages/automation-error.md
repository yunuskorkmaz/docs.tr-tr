---
title: Otomasyon hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 8370f744b916ce4a797c808ed58c5fc9580e6278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935297"
---
# <a name="automation-error"></a><span data-ttu-id="e22ec-102">Otomasyon hatası</span><span class="sxs-lookup"><span data-stu-id="e22ec-102">Automation error</span></span>
<span data-ttu-id="e22ec-103">Yöntem yürütme veya alma veya bir nesne değişkeninin bir özelliği ayarlamak bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e22ec-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="e22ec-104">Nesnesini oluşturan uygulama tarafından bildirilen hata.</span><span class="sxs-lookup"><span data-stu-id="e22ec-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e22ec-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e22ec-105">To correct this error</span></span>  
  
1. <span data-ttu-id="e22ec-106">Özelliklerini denetleyin `Err` kaynak ve hatanın yapısını belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="e22ec-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="e22ec-107">Kullanım `On Error Resume Next` deyimi erişimi deyimi hemen önce ve sonra hemen sonra erişim deyim hataları olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e22ec-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22ec-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e22ec-108">See also</span></span>

- [<span data-ttu-id="e22ec-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="e22ec-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="e22ec-110">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="e22ec-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
