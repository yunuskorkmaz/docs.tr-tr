---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585573"
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
