---
title: "Hatasız devam et"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a><span data-ttu-id="f9ab5-102">Hatasız devam et</span><span class="sxs-lookup"><span data-stu-id="f9ab5-102">Resume without error</span></span>
<span data-ttu-id="f9ab5-103">A `Resume` deyimi görünen hata işleme kodu dışında ya da herhangi bir hata oluştu rağmen kodu atlanan bir hata işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f9ab5-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f9ab5-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f9ab5-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="f9ab5-105">Taşıma `Resume` bir hata işleyicisi INTO deyimi veya silin.</span><span class="sxs-lookup"><span data-stu-id="f9ab5-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="f9ab5-106">Etiketlere atlama yordamları arasında gerçekleşemez şekilde yordamı hata işleyicisine tanımlayan etiket için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="f9ab5-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="f9ab5-107">Hedefi olarak belirtilen bir yinelenen etiket bulursanız bir `GoTo` değil deyimi bir `On Error GoTo` ifadesi, satır etiketi amaçlanan hedefine ile uyuşacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f9ab5-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ab5-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9ab5-108">See Also</span></span>  
 [<span data-ttu-id="f9ab5-109">Resume deyimi</span><span class="sxs-lookup"><span data-stu-id="f9ab5-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="f9ab5-110">On Error deyimi</span><span class="sxs-lookup"><span data-stu-id="f9ab5-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
