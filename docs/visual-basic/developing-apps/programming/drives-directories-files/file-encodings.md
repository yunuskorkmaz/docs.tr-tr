---
title: "Dosya Kodlamaları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: deaab4371ab0d5d15c627bfd6352a7090bf08024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Dosyaları okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Dosyalara yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
