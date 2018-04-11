---
title: Otomasyon hatası
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 790b171b8d4022bd6d8b038c4221f24805ae42f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="automation-error"></a><span data-ttu-id="8a9d7-102">Otomasyon hatası</span><span class="sxs-lookup"><span data-stu-id="8a9d7-102">Automation error</span></span>
<span data-ttu-id="8a9d7-103">Yöntem yürütme veya alma veya bir nesne değişkeninin bir özellik ayarlama bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="8a9d7-104">Hata nesnesi oluşturdu uygulama tarafından bildirildi.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8a9d7-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8a9d7-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="8a9d7-106">Özelliklerini denetleyin `Err` kaynak hem de hatanın yapısını belirlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="8a9d7-107">Kullanım `On Error Resume Next` deyimi erişilirken deyimi hemen önce ve sonra hemen erişilirken deyimi hata olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9d7-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a9d7-108">See Also</span></span>  
 [<span data-ttu-id="8a9d7-109">Hata türleri</span><span class="sxs-lookup"><span data-stu-id="8a9d7-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="8a9d7-110">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="8a9d7-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
