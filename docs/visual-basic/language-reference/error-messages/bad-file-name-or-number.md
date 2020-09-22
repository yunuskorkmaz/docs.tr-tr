---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874897"
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
