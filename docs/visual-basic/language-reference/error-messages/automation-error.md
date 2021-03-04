---
description: 'Daha fazla bilgi edinin: Otomasyon hatası'
title: Otomasyon hatası
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: bf3e61bb9b8fec9a831d211b70abdca322c1fe06
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106611"
---
# <a name="automation-error"></a><span data-ttu-id="85622-103">Otomasyon hatası</span><span class="sxs-lookup"><span data-stu-id="85622-103">Automation error</span></span>

<span data-ttu-id="85622-104">Bir yöntem yürütülürken veya bir nesne değişkeninin özelliği alınırken veya ayarlanırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="85622-104">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="85622-105">Hata, nesneyi oluşturan uygulama tarafından bildirildi.</span><span class="sxs-lookup"><span data-stu-id="85622-105">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85622-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="85622-106">To correct this error</span></span>  
  
1. <span data-ttu-id="85622-107">`Err`Hatanın kaynağını ve yapısını öğrenmek için nesnenin özelliklerini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="85622-107">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="85622-108">`On Error Resume Next`' İ erişen deyimden hemen önce kullanın ve ardından erişim deyimden hemen sonra hata olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="85622-108">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85622-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85622-109">See also</span></span>

- [<span data-ttu-id="85622-110">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="85622-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="85622-111">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="85622-111">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
