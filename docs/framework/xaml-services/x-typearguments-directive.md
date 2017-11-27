---
title: "x:TypeArguments Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
caps.latest.revision: "18"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a63a8080c71ad026664e2e14fc1762fcdd4bdb36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xtypearguments-directive"></a>x:TypeArguments Yönergesi
Sınırlama geçişleri genel tür oluşturucuya genel bağımsız değişkenlerini yazın.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`object`|Bir nesne öğesi bildirimi CLR genel türü tarafından yedeklenen bir XAML türü. Varsa `object` varsayılan XAML ad alanından değil bir XAML türü başvurduğu `object` XAML ad uzayı belirtmek için bir önek gerektirir nerede `object` bulunmaktadır.|  
|`typeString`|Bir veya daha fazla XAML bildiren bir dize türü adları dize olarak, tür bağımsız değişkenleri CLR genel tür için sağladığı. Açıklamalar için ek sözdizimi notlarına bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çoğu durumda, bir bilgi öğesi olarak kullanılan XAML türleri bir `typeString` dize öneki. CLR genel kısıtlamalar tipik türleri (örneğin, <xref:System.Int32> ve <xref:System.String>) CLR temel sınıf kitaplıklarından gelir. Bu kitaplıklar eşlenmemiş tipik çerçeveye özel varsayılan XAML ad uzayları olup olmadığı ve bu nedenle, bir önek eşleştirme için XAML kullanımı gerektirir.  
  
 Bir virgül ayırıcısı kullanarak birden fazla XAML tür adı belirtebilirsiniz.  
  
 Genel türler genel kısıtlamalar kullanırsanız, iç içe geçmiş kısıtlaması tür bağımsız değişkenleri bulunabilir parantez (tarafından).  
  
 Unutmayın, bu tanımı `x:TypeArguments` .NET Framework XAML Hizmetleri için özeldir ve CLR yedekleme kullanma. Bir dil düzeyi tanımı bulunabilir [ \[MS XAML\] bölüm 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Kullanım örnekleri  
 Bu örnekler için aşağıdaki XAML ad alanı tanımları bildirilir varsayın:  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Liste\<dize >  
 `<scg:List x:TypeArguments="sys:String" ...>`Yeni bir örneğini oluşturur <xref:System.Collections.Generic.List%601> ile bir <xref:System.String> bağımsız değişkeni yazın.  
  
### <a name="dictionarystringstring"></a>Sözlük\<dize, dize >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`Yeni bir örneğini oluşturur <xref:System.Collections.Generic.Dictionary%602> iki <xref:System.String> tür bağımsız değişkenleri.  
  
### <a name="queuekeyvaluepairstringstring"></a>Sıra < KeyValuePair\<dize, dize >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`Yeni bir örneğini oluşturur <xref:System.Collections.Generic.Queue%601> bir kısıtlaması olan <xref:System.Collections.Generic.KeyValuePair%602> iç kısıtlama tür bağımsız değişkenleri ile <xref:System.String> ve <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 ve WPF XAML genel kullanımları  
 XAML 2006 kullanım ve WPF uygulamaları için kullanılan XAML için aşağıdaki kısıtlamalar mevcut `x:TypeArguments` ve genel olarak genel tür kullanımları XAML gelen:  
  
-   XAML dosyasının kök öğesinin yalnızca genel bir tür başvuran genel bir XAML kullanımını destekler.  
  
-   Kök öğesi en az bir tür bağımsız değişkeni ile genel tür eşlenmelidir. Örnek <xref:System.Windows.Navigation.PageFunction%601>. WPF XAML genel kullanım desteği için birincil senaryo sayfa işlevlerdir.  
  
-   Genel için kök öğesi XAML object öğesi, ayrıca kullanarak bir parçalı sınıf bildirmelidir `x:Class`. Bir WPF tanımlama yapı eylemi bile bu geçerlidir.  
  
-   `x:TypeArguments`iç içe geçmiş genel kısıtlamalar başvuramaz.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 veya herhangi bir WPF 3.0 veya 3.5 WPF XAML 2006 bağımlılık  
 .NET Framework XAML Hizmetleri XAML 2006 ya da XAML 2009, genel XAML kullanımı WPF ile ilgili kısıtlamalar rahat. Yedekleme türü sistem ve nesne modeli destekleyebilir XAML işaretleme herhangi bir konumda bir genel nesne öğesi örneğini oluşturabilirsiniz.  
  
 XAML 2009 kullanırsanız, ortak dil temelleri için XAML türlerinin edinilir türleri temel CLR eşleme yerine, kullanabileceğiniz [XAML dili ortak temelleri için yerleşik türler](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) bilgi öğeleri olarak bir `typeString`. Örneğin, aşağıdaki bildirebilirsiniz (önek eşlemeleri gösterilmez, ancak x olduğu XAML dili XAML ad uzayı XAML 2009 için):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 WPF ve hedeflerken [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], XAML 2009 özellikleri ile birlikte kullanabileceğiniz `x:TypeArguments` ancak yalnızca gevşek XAML (işaretleme-derlenmemiş XAML). XAML biçimlendirme derlenmiş WPF ve XAML BAML form için şu anda desteklemediği XAML 2009 anahtar sözcükleri ve özellikler. XAML biçimlendirme derleme varsa, "XAML 2006 ve WPF genel XAML kullanımları" bölümünde belirtildiği kısıtlamaları altında çalışması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md)  
 [x: Type işaretleme uzantısı](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [XAML dili ortak temelleri için yerleşik türler](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [XAML'deki genel türler](../../../docs/framework/xaml-services/generics-in-xaml.md)
