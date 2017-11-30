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
# <a name="resume-without-error"></a>Hatasız devam et
A `Resume` deyimi görünen hata işleme kodu dışında ya da herhangi bir hata oluştu rağmen kodu atlanan bir hata işleyicisi.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Taşıma `Resume` bir hata işleyicisi INTO deyimi veya silin.  
  
2.  Etiketlere atlama yordamları arasında gerçekleşemez şekilde yordamı hata işleyicisine tanımlayan etiket için arama yapın. Hedefi olarak belirtilen bir yinelenen etiket bulursanız bir `GoTo` değil deyimi bir `On Error GoTo` ifadesi, satır etiketi amaçlanan hedefine ile uyuşacak şekilde değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Resume deyimi](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [On Error deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
