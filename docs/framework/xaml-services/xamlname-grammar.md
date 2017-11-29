---
title: XamlName Dilbilgisi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 92327c8ff6232e64bf8b6b2a9d78e4a9eb30f3e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xamlname-grammar"></a>XamlName Dilbilgisi
XamlName dilbilgisi kolaylık sağlamak için burada çoğaltılamaz XAML dil belirtimi [MS-XAML], tanımlanan belirli bir dil bilgisi ' dir.  
  
## <a name="from-the-xaml-specification"></a>XAML belirtiminden  
 [MS-XAML] belirtimi türleri ve özellikler için kullanılan yasal simgesel tanımlayıcıları kümesini tanımlamak için XamlName dilbilgisi tanımlar.  
  
 XamlName aşağıdaki dilbilgisi uymalıdır türünde olan değerleri dize:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Aşağıdaki genel kategori değerleri Unicode karakter veritabanında tanımlanan varsayan  
  
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
  
 Özelliği için kullanılan DottedXamlName, ikinci bir dilbilgisi XAML tanımlar ve olay başvuruları tam ve ayrıca için üyeleri bağlı. Daha fazla bilgi için bkz: <xref:System.Windows.DependencyProperty> ve [XAML genel bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
 DottedXamlName aşağıdaki dilbilgisi uymalıdır türünde olan değerleri dize:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tam belirtimi için bkz: [ \[MS XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).
