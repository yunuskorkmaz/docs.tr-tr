---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 11e866d9a8da7ad1ecc5f788fc31f6ac96d32f2c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409835"
---
# <a name="bad-file-name-or-number"></a>Hatalı dosya adı veya numarası
Belirtilen dosyaya erişmeye çalışırken bir hata oluştu. Bu hatanın olası nedenleri arasında aşağıdakiler bulunur:  
  
- Bir ifade, içinde belirtilmeyen `FileOpen` veya bir `FileOpen` ifadede belirtilen ancak daha sonra kapatılan bir dosya adı veya numarası olan bir dosyaya başvurur.  
  
- Bir ifade, dosya numarası aralığının dışında bir sayı içeren bir dosyaya başvurur.  
  
- Bir ifade, geçerli olmayan bir dosya adı veya sayı anlamına gelir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Dosya adının bir bildirimde belirtildiğinden emin olun `FileOpen` . `FileClose`Deyiminizi bağımsız değişkenler olmadan çağırdıysanız, tüm açık dosyaları yanlışlıkla kapattığını unutmayın.  
  
2. Kodunuz algorithmically dosya numaralarını üretiyorsa, sayıların geçerli olduğundan emin olun.  
  
3. İşletim sistemi kurallarına uyduğundan emin olmak için dosya adlarını denetleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic Adlandırma Kuralları](../../programming-guide/program-structure/naming-conventions.md)
