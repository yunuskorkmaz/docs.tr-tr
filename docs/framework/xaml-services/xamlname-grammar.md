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
ms.openlocfilehash: 642ca16142bdfe78a40ddf4e6a3a79ce6a8a4985
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58031608"
---
# <a name="xamlname-grammar"></a>XamlName Dilbilgisi
XamlName dilbilgisi kolaylık olması için burada tekrar üretilmektedir XAML dil belirtimi [MS-XAML], tanımlanan belirli bir dil bilgisi olur.  
  
## <a name="from-the-xaml-specification"></a>XAML belirtiminden  
 [MS-XAML] belirtimi türleri ve özellikler için kullanılan yasal sembolik tanımlayıcıları kümesini tanımlamak için XamlName dilbilgisi tanımlar.  
  
 XamlName aşağıdaki dilbilgisi uymalıdır türü olan değerleri dize:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Aşağıdaki genel kategori değerleri Unicode karakter veritabanında tanımlanan varsayılır  
  
```  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 İkinci özelliği için kullanılan DottedXamlName dilbilgisi, XAML tanımlar ve olay uygun başvuruları ve üyeleri için ve ayrıca bağlı. Daha fazla bilgi için <xref:System.Windows.DependencyProperty> ve [XAML genel bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md).  
  
 DottedXamlName aşağıdaki dilbilgisi uymalıdır türü olan değerleri dize:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tam belirtimi için bkz: [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).
