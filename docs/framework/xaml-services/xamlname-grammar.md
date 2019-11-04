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
ms.openlocfilehash: a39d25f03583ab9020878b7a659bc99489231ff9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458890"
---
# <a name="xamlname-grammar"></a>XamlName Dilbilgisi
XamlName dilbilgisi, daha kolay bir şekilde yeniden oluşturulduğu XAML dil belirtimi [MS-XAML] içinde tanımlanan belirli bir dildilidir.  
  
## <a name="from-the-xaml-specification"></a>XAML belirtiminden  
 [MS-XAML] belirtimi, türler ve özellikler için kullanılan yasal sembolik tanımlayıcılar kümesini tanımlamak için XamlName adlı dilbilgisi tanımlar.  
  
 XamlName türünde dize değerleri aşağıdaki dilbilgisinde uyumlu olmalıdır:  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Bu, Unicode karakter veritabanında tanımlanan aşağıdaki genel kategori değerlerini kabul eder  

| Unicode kategorisi   | Açıklama                   |
|--------------------|-------------------------------|
| Lu                 | Harf, Büyük Harf             |
| Ll                 | Harf, Küçük Harf             |
| Lt                 | Harf, Başlık Düzeni             |
| Lm                 | Harf, Değiştirici              |
| Lo                 | Harf, Diğer                 |
| Sütun                 | İşaret, Aralık dışı             |
| Mc                 | İşaret, Boşluklu Birleşik       |
| Nd                 | Sayı, ondalık               |
| NL                 | Sayı, Harf                |
 
 XAML, özellik ve olay nitelikli başvurular ve ayrıca ekli Üyeler için kullanılan ikinci bir dilbilgisini, DottedXamlName öğesini tanımlar. Daha fazla bilgi için bkz. <xref:System.Windows.DependencyProperty> ve [xaml 'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md).  
  
 DottedXamlName türünde dize değerleri aşağıdaki dilbilgisinde uyumlu olmalıdır:  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tam belirtim için bkz. [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).
