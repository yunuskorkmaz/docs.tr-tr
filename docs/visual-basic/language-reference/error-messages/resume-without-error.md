---
title: Hatasız devam et
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597881"
---
# <a name="resume-without-error"></a>Hatasız devam et
A `Resume` deyimi görünen hata işleme kodu dışında ya da herhangi bir hata oluştu rağmen kodu atlanan bir hata işleyicisi.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Taşıma `Resume` bir hata işleyicisi INTO deyimi veya silin.  
  
2.  Etiketlere atlama yordamları arasında gerçekleşemez şekilde yordamı hata işleyicisine tanımlayan etiket için arama yapın. Hedefi olarak belirtilen bir yinelenen etiket bulursanız bir `GoTo` değil deyimi bir `On Error GoTo` ifadesi, satır etiketi amaçlanan hedefine ile uyuşacak şekilde değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Resume Deyimi](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
