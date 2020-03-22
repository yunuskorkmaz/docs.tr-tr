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

Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işlenirken karakterlerin nasıl temsil edilecek lerini belirtir. Unicode genellikle tercih edilse de, bir kodlama, işleyebileceği veya işleyemeyeceği dil karakterleri açısından diğerine göre tercih edilebilir.

Dosyalardan okuma veya dosyalara yazma, dosya kodlamalarının yanlış eşleşmesi özel durumlara veya yanlış sonuçlara neden olabilir.

## <a name="types-of-encodings"></a>Kodlama Türleri

Unicode, dosyalarla çalışırken tercih edilen kodlamadır. Unicode, modern bilgi işlemde kullanılan teknik semboller ve yayımlamada kullanılan özel karakterler de dahil olmak üzere tüm karakterleri temsil etmek için 16 bit kod değerlerini kullanan dünya çapında bir karakter kodlama standardıdır.

Önceki karakter kodlama standartları, belirli bir dilde veya coğrafi bölgede kullanılan karakterleri temsil etmek için 8 bit kod değerleri veya 8 bit değerlerinbirlöleri kullanan Windows ANSI karakter kümesi gibi geleneksel karakter kümelerinden oluşuyordu.

## <a name="encoding-class"></a>Kodlama Sınıfı

Sınıf, <xref:System.Text.Encoding> bir karakter kodlamasını temsil eder. Bu tablo, kullanılabilir kodlama türünü listeler ve her birini açıklar.

|Adı|Açıklama|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Unicode karakterlerinin ASCII karakterini kodlamayı temsil eder.|
|<xref:System.Text.UnicodeEncoding>|Unicode karakterlerinin UTF-16 kodlayıcılarını temsil eder.|
|<xref:System.Text.UTF32Encoding>|Unicode karakterlerinin UTF-32 kodlayıcılarını temsil eder.|
|<xref:System.Text.UTF7Encoding>|Unicode karakterlerinin UTF-7 kodlaması temsil eder.|
|<xref:System.Text.UTF8Encoding>|Unicode karakterlerinin UTF-8 kodlaması temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
