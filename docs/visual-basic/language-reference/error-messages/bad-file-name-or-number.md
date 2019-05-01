---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 2e5d4a3ddd66df85dc4758e22b36ac1ed495659a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935232"
---
# <a name="bad-file-name-or-number"></a>Hatalı dosya adı veya numarası
Belirtilen dosyaya erişmeye çalışırken bir hata oluştu. Bu hata için olası nedenler arasındadır:  
  
- Belirtilmedi bir dosyanın dosya adı veya numarası ile bir deyim başvurduğu `FileOpen` içinde deyim ya da, belirtilmiş bir `FileOpen` deyimi ancak olan sonradan kapalı.  
  
- Dosya numaraları aralığının dışında bir sayı içeren bir dosyaya bir bildirimi gösterir.  
  
- Bir deyim için bir dosya adı veya geçersiz sayı ifade eder.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Emin dosya adı belirtilen bir `FileOpen` deyimi. Çağrılan gerçekleştiriyorsanız `FileClose` ifadesi bağımsız değişkeni olmadan yanlışlıkla tüm açık dosyalar kapattıysanız.  
  
2. Kodunuzu dosya numaraları algorithmically oluşturuyorsa numaralarının geçerli olduğundan emin olun.  
  
3. Dosya adları, işletim sistemi kuralları için uygun emin olmak için kontrol edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
