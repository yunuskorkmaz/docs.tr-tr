---
title: Dosya Kodlamaları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 30aba517b3b0fbb5fa5bea48134934b2c2d26e50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="file-encodings-visual-basic"></a>Dosya Kodlamaları (Visual Basic)
Dosya kodlamaları, olarak da bilinen karakter kodlamaları temsil etmek nasıl belirtin ne zaman karakter metin işleme. Unicode genellikle tercih edilen olmasına rağmen bir kodlama başka hangi dil karakterlerini bakımından veya yükleyebilir işleyemez, tercih edilebilir.  
  
 Dosyalara yazma veya okuma, hatalı dosya kodlamaları eşleşen özel durumları veya hatalı sonuçlar neden olabilir.  
  
## <a name="types-of-encodings"></a>Kodlamalar türleri  
 Unicode dosyaları ile çalışırken, tercih edilen kodlamayı ' dir. Unicode modern, teknik simgeler ve yayımlama içinde kullanılan özel karakterleri dahil olmak üzere bilgisayar kullanılan tüm karakterleri temsil edecek 16 bit kod değerleri kullanan bir dünya çapında karakter kodlamasını standardıdır.  
  
 Belirli bir dil veya coğrafi bölge içinde kullanılan karakterleri temsil etmek için 8 bit kod değerleri veya 8 bit değerleri birleşimlerini kullanan Windows ANSI karakter kümesini gibi geleneksel karakter kümesinden karakter kodlamasını önceki standartları içermektedir.  
  
## <a name="encoding-class"></a>Kodlama sınıfı  
 <xref:System.Text.Encoding> Sınıfı, bir karakter kodlama temsil eder. Bu tabloda Kodlamalar kullanılabilir türünü listeler ve her açıklanmaktadır.  
  
|Ad|Açıklama|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|Bir ASCII karakteri Unicode karakter kodlama temsil eder.|  
|<xref:System.Text.UnicodeEncoding>|UTF-16 kodlamasını Unicode karakterinden temsil eder.|  
|<xref:System.Text.UTF32Encoding>|UTF-32 kodlama Unicode karakterinden temsil eder.|  
|<xref:System.Text.UTF7Encoding>|UTF-7 kodlama Unicode karakterinden temsil eder.|  
|<xref:System.Text.UTF8Encoding>|UTF-8 kodlaması Unicode karakterinden temsil eder.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
