---
title: Dosya Kodlamaları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: d73226c58d39c970ec02c32a2c188f2747a7d87e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583472"
---
# <a name="file-encodings-visual-basic"></a>Dosya Kodlamaları (Visual Basic)

Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işleme sırasında karakterlerin nasıl temsil edileceğini belirtir. Tek bir kodlama, bir veya işleyemeyen dil karakterleri açısından başka bir şekilde tercih edilebilir, ancak UNICODE genellikle tercih edilir.

Dosyadan okuma veya yazma yaparken, dosya kodlamaları yanlış şekilde eşleştirilirken özel durumlar veya hatalı sonuçlar oluşabilir.

## <a name="types-of-encodings"></a>Kodlamalar türleri

Unicode, dosyalarla çalışırken tercih edilen kodlanıyor. Unicode, yayımlamak için kullanılan teknik semboller ve özel karakterler de dahil olmak üzere modern bilgi işlem 'da kullanılan tüm karakterleri temsil etmek için 16 bit kod değerlerini kullanan dünya çapındaki bir karakter kodlama standardıdır.

Önceki karakter kodlama standartları, 8 bit kod değerleri kullanan Windows ANSI karakter kümesi veya belirli bir dilde veya coğrafi bölgede kullanılan karakterleri göstermek için 8 bit değer bileşimleri gibi geleneksel karakter kümelerinden oluşur.

## <a name="encoding-class"></a>Kodlama sınıfı

@No__t_0 sınıfı bir karakter kodlamasını temsil eder. Bu tabloda, kullanılabilir kodlamalar türü listelenmekte ve her biri açıklanmaktadır.

|Name|Açıklama|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Unicode karakterlerinin ASCII karakter kodlamasını temsil eder.|
|<xref:System.Text.UnicodeEncoding>|Unicode karakterlerinin UTF-16 kodlamasını temsil eder.|
|<xref:System.Text.UTF32Encoding>|Unicode karakterlerinin UTF-32 kodlamasını temsil eder.|
|<xref:System.Text.UTF7Encoding>|Unicode karakterlerinin UTF-7 kodlamasını temsil eder.|
|<xref:System.Text.UTF8Encoding>|Unicode karakterlerinin UTF-8 kodlamasını temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
