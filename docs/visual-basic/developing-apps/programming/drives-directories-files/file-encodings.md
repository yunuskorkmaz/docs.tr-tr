---
description: 'Daha fazla bilgi edinin: dosya kodlamaları (Visual Basic)'
title: Dosya Kodlamaları
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f573b5d8f83c27cbf4ddacb9fd40474d7d1be1ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675370"
---
# <a name="file-encodings-visual-basic"></a>Dosya Kodlamaları (Visual Basic)

Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işleme sırasında karakterlerin nasıl temsil edileceğini belirtir. Tek bir kodlama, bir veya işleyemeyen dil karakterleri açısından başka bir şekilde tercih edilebilir, ancak UNICODE genellikle tercih edilir.

Dosyadan okuma veya yazma yaparken, dosya kodlamaları yanlış şekilde eşleştirilirken özel durumlar veya hatalı sonuçlar oluşabilir.

## <a name="types-of-encodings"></a>Kodlamalar türleri

Unicode, dosyalarla çalışırken tercih edilen kodlanıyor. Unicode, yayımlamak için kullanılan teknik semboller ve özel karakterler de dahil olmak üzere modern bilgi işlem 'da kullanılan tüm karakterleri temsil etmek için 16 bit kod değerlerini kullanan dünya çapındaki bir karakter kodlama standardıdır.

Önceki karakter kodlama standartları, 8 bit kod değerleri kullanan Windows ANSI karakter kümesi veya belirli bir dilde veya coğrafi bölgede kullanılan karakterleri göstermek için 8 bit değer bileşimleri gibi geleneksel karakter kümelerinden oluşur.

## <a name="encoding-class"></a>Kodlama sınıfı

<xref:System.Text.Encoding>Sınıfı bir karakter kodlamasını temsil eder. Bu tabloda, kullanılabilir kodlamalar türü listelenmekte ve her biri açıklanmaktadır.

|Ad|Açıklama|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Unicode karakterlerinin ASCII karakter kodlamasını temsil eder.|
|<xref:System.Text.UnicodeEncoding>|Unicode karakterlerinin UTF-16 kodlamasını temsil eder.|
|<xref:System.Text.UTF32Encoding>|Unicode karakterlerinin UTF-32 kodlamasını temsil eder.|
|<xref:System.Text.UTF7Encoding>|Unicode karakterlerinin UTF-7 kodlamasını temsil eder.|
|<xref:System.Text.UTF8Encoding>|Unicode karakterlerinin UTF-8 kodlamasını temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalardan Okuma](reading-from-files.md)
- [Dosyalara Yazma](writing-to-files.md)
