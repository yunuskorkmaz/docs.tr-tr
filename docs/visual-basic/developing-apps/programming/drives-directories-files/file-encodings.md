---
title: Dosya Kodlamaları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: c22e8046a8b88890f25bc6b671825eb6d68ec6b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814009"
---
# <a name="file-encodings-visual-basic"></a>Dosya Kodlamaları (Visual Basic)
Dosya kodlamaları olarak da bilinen karakter kodlamalarını temsil etmek nasıl belirtin ne zaman karakter metin işleme. Unicode genellikle tercih edilir olsa da bir kodlama başka hangi dil karakterlerini açısından olabilir veya işleyemez, tercih edilebilir.  
  
 Dosyalara yazma veya okuma, hatalı dosya kodlamaları eşleşen özel durumlar veya hatalı sonuçlar neden olabilir.  
  
## <a name="types-of-encodings"></a>Tür kodlamayı  
 Unicode dosyalarıyla çalışırken tercih edilen kodlamada değil. Unicode modern teknik simgeleri ve yayımlama içinde kullanılan özel karakterler dahil olmak üzere bilgi işlem, içinde kullanılan tüm karakterleri temsil etmek için 16-bit kod değerleri kullanan bir dünya çapında karakter kodlama standardıdır.  
  
 Belirli bir dil veya coğrafi bölge içinde kullanılan karakterleri temsil etmek için 8-bit kod değerleri veya 8-bit değerleri birleşimlerini kullanan Windows ANSI karakter kümesi gibi geleneksel karakter kümesi, önceki karakter kodlama standartları oluşmuştur.  
  
## <a name="encoding-class"></a>Kodlama sınıfı  
 <xref:System.Text.Encoding> Sınıfı, karakter kodlamasını temsil eder. Bu tablo, kullanılabilir Kodlamalar türünü listeler ve her açıklar.  
  
|Ad|Açıklama|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|ASCII karakter kodlama Unicode karakterini temsil eder.|  
|<xref:System.Text.UnicodeEncoding>|UTF-16 kodlamasını Unicode karakterini temsil eder.|  
|<xref:System.Text.UTF32Encoding>|UTF-32 kodlama Unicode karakterini temsil eder.|  
|<xref:System.Text.UTF7Encoding>|UTF-7 kodlaması Unicode karakterini temsil eder.|  
|<xref:System.Text.UTF8Encoding>|UTF-8 kodlamalı Unicode karakterini temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
