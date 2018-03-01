---
title: "Hatalı dosya adı veya numarası"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a>Hatalı dosya adı veya numarası
Belirtilen dosyaya erişmeye çalışırken bir hata oluştu. Bu hatanın olası nedenleri arasında aşağıdakiler vardır:  
  
-   Bir ifade belirtilmedi bir dosya adı veya numarası sahip bir dosya başvuruyor `FileOpen` deyimi ya da değeri belirtilmiş bir `FileOpen` deyimi ancak edildi sonradan kapalı.  
  
-   Bir deyim bir dosyayı dosya sayı aralık dışında bir sayı ile ifade eder.  
  
-   Bir deyim bir dosya adı veya geçersiz sayı başvuruyor.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Emin olun dosya adında belirtilen bir `FileOpen` deyimi. Çağrılan gerçekleştiriyorsanız `FileClose` deyimi bağımsız değişkenler olmadan, yanlışlıkla tüm açık dosyalar kapanır.  
  
2.  Kodunuzu dosya numaraları algorithmically oluşturuyorsa sayıları geçerli olduğundan emin olun.  
  
3.  İşletim sistemi kuralları için uygun emin olmak için dosya adlarını denetleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
