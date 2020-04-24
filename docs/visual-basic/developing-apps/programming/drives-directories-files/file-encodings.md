---
title: Dosya Kodlamaları
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 52770187568d0ba0f54ec36ee2c3d754a9b4d9a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348888"
---
# <a name="file-encodings-visual-basic"></a>Dosya Kodlamaları (Visual Basic)

Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işleme sırasında karakterlerin nasıl temsil edileceğini belirtir. Tek bir kodlama, bir veya işleyemeyen dil karakterleri açısından başka bir şekilde tercih edilebilir, ancak UNICODE genellikle tercih edilir.

Dosyadan okuma veya yazma yaparken, dosya kodlamaları yanlış şekilde eşleştirilirken özel durumlar veya hatalı sonuçlar oluşabilir.

## <a name="types-of-encodings"></a>Kodlamalar türleri

Unicode, dosyalarla çalışırken tercih edilen kodlanıyor. Unicode, yayımlamak için kullanılan teknik semboller ve özel karakterler de dahil olmak üzere modern bilgi işlem 'da kullanılan tüm karakterleri temsil etmek için 16 bit kod değerlerini kullanan dünya çapındaki bir karakter kodlama standardıdır.

Önceki karakter kodlama standartları, 8 bit kod değerleri kullanan Windows ANSI karakter kümesi veya belirli bir dilde veya coğrafi bölgede kullanılan karakterleri göstermek için 8 bit değer bileşimleri gibi geleneksel karakter kümelerinden oluşur.

## <a name="encoding-class"></a>Kodlama sınıfı

<xref:System.Text.Encoding> Sınıfı bir karakter kodlamasını temsil eder. Bu tabloda, kullanılabilir kodlamalar türü listelenmekte ve her biri açıklanmaktadır.

|Adı|Açıklama|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Unicode karakterlerinin ASCII karakter kodlamasını temsil eder.|
|<xref:System.Text.UnicodeEncoding>|Unicode karakterlerinin UTF-16 kodlamasını temsil eder.|
|<xref:System.Text.UTF32Encoding>|Unicode karakterlerinin UTF-32 kodlamasını temsil eder.|
|<xref:System.Text.UTF7Encoding>|Unicode karakterlerinin UTF-7 kodlamasını temsil eder.|
|<xref:System.Text.UTF8Encoding>|Unicode karakterlerinin UTF-8 kodlamasını temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
