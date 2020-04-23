---
title: XamlName Dilbilgisi
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 2fc74990b15caaa9b58e6eea5b0212ea22505674
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071831"
---
# <a name="xamlname-grammar"></a>XamlName Dilbilgisi

XamlName Grammar, XAML dil belirtiminde [MS-XAML], burada kolaylık sağlamak için çoğaltılan tanımlanan belirli bir dilbilgisidir.

## <a name="from-the-xaml-specification"></a>XAML Belirtiminden

[MS-XAML] belirtimi, türleri ve özellikleri için kullanılan yasal sembolik tanımlayıcılar kümesini tanımlamak için XamlName dilbilgisini tanımlar.

XamlName türünden olan dize değerleri aşağıdaki dilbilgisine uygun olmalıdır:

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

Unicode Karakter Veritabanında tanımlandığı şekilde aşağıdaki genel kategori değerlerini varsayar

| Unicode kategorisi   | Açıklama                   |
|--------------------|-------------------------------|
| Lu                 | Harf, Büyük Harf             |
| Ll                 | Harf, Küçük Harf             |
| Lt                 | Harf, Başlık Düzeni             |
| Lm                 | Harf, Değiştirici              |
| Lo                 | Harf, Diğer                 |
| Sütun                 | İşaretleme, Aralıksız             |
| Mc                 | İşaret, Boşluklu Birleşik       |
| Nd                 | Sayı, Ondalık               |
| Nl                 | Sayı, Harf                |

XAML, özellik ve etkinlik nitelikli başvurular için ve ekli üyeler için kullanılan ikinci bir dilbilgisi olan Noktalı XamlName'yi tanımlar. Daha fazla bilgi <xref:System.Windows.DependencyProperty> için bkz ve [XAML Genel Bakış (WPF)](../fundamentals/xaml.md).

DottedXamlName türünden dize değerleri aşağıdaki dilbilgisine uygun olmalıdır:

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a>Açıklamalar

Tam belirtim için [ \[\]MS-XAML'ye](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.
