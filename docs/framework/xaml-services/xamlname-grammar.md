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
ms.openlocfilehash: 837a18ca18d0c634dfa5cc133aa013919cfb9d96
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053893"
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
 
 XAML, özellik ve olay nitelikli başvurular ve ayrıca ekli Üyeler için kullanılan ikinci bir dilbilgisini, DottedXamlName öğesini tanımlar. Daha fazla bilgi için bkz <xref:System.Windows.DependencyProperty> . ve [xaml 'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md).  
  
 DottedXamlName türünde dize değerleri aşağıdaki dilbilgisinde uyumlu olmalıdır:  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tam belirtim için bkz [ \[. ms-xaml\]](https://go.microsoft.com/fwlink/?LinkId=114525).
