---
title: x:TypeArguments Yönergesi
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 1d1b10b4da1263843bdce5447f0716569c7700e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085812"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments Yönergesi
Sınırlama geçişleri bir genel oluşturucuya genel tür bağımsız değişkenlerini yazın.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`object`|Bir CLR genel türü tarafından desteklenen bir XAML türündeki bir nesne öğe bildirimi. Varsa `object` varsayılan XAML ad alanından değil bir XAML türü başvurduğu `object` XAML ad alanı belirtmek için bir önek gerektirir burada `object` bulunmaktadır.|  
|`typeString`|Bir veya daha fazla XAML bildiren bir dize tür adları dize olarak hangi CLR genel tür için tür bağımsız değişkenleri sağlar. Açıklamalar için ek söz dizimi notlarına bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çoğu durumda, bir bilgi öğesi olarak kullanılan XAML türleri bir `typeString` dize ön eki bulunur. CLR genel kısıtlamalara tipik türleri (örneğin, <xref:System.Int32> ve <xref:System.String>) CLR temel sınıf kitaplıklarını gelir. Bu kitaplıklar eşlenmemiş tipik çerçeveye özgü varsayılan XAML ad alanları değildir ve bu nedenle, XAML kullanım için bir önek eşleştirme gerektiren.  
  
 Bir virgül olan sınırlayıcıyı kullanarak birden fazla XAML türü adını belirtebilirsiniz.  
  
 Genel sınırlamalar genel türleri kullanıyorsanız, iç içe geçmiş kısıtlaması tür bağımsız değişkenlerini bulunabilir parantezleri () tarafından.  
  
 Unutmayın, bu tanımı `x:TypeArguments` için .NET Framework XAML hizmetlerinde özeldir ve CLR yedekleme kullanma. Dil düzeyi tanımı bulunabilir [ \[MS-XAML\] bölümü 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Kullanım örnekleri  
 Bu örnekler için aşağıdaki XAML ad alanı tanımları bildirilir varsayın:  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Liste\<dizesi >  
 `<scg:List x:TypeArguments="sys:String" ...>` Yeni bir örneğini oluşturur <xref:System.Collections.Generic.List%601> ile bir <xref:System.String> tür bağımsız değişkeni.  
  
### <a name="dictionarystringstring"></a>Sözlük\<String, String >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` Yeni bir örneğini oluşturur <xref:System.Collections.Generic.Dictionary%602> iki <xref:System.String> tür bağımsız değişkenleri.  
  
### <a name="queuekeyvaluepairstringstring"></a>Kuyruk < KeyValuePair\<dize, dize >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` Yeni bir örneğini oluşturur <xref:System.Collections.Generic.Queue%601> kısıtlaması, olan <xref:System.Collections.Generic.KeyValuePair%602> iç kısıtlaması tür bağımsız değişkenleri ile <xref:System.String> ve <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 ve WPF'de XAML genel kullanımları  
 XAML 2006 kullanım ve WPF uygulamaları için kullanılan XAML için aşağıdaki kısıtlamalar için mevcut `x:TypeArguments` ve genel XAML gelen genel tür kullanımları:  
  
-   Yalnızca bir XAML dosyasının kök öğesini bir genel türe başvuran genel bir XAML kullanımını destekler.  
  
-   Kök öğe en az bir tür bağımsız değişkeni ile genel tür eşlenmelidir. <xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir. WPF XAML genel kullanım desteği için birincil senaryosu sayfasında işlevlerdir.  
  
-   Genel için kök öğesi XAML nesne öğesi de kullanarak bir parçalı sınıf bildirmeniz gerekir `x:Class`. Bir WPF tanımlama derleme eylemi bile bu geçerlidir.  
  
-   `x:TypeArguments` iç içe geçmiş genel kısıtlamalara başvuramaz.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 ya da WPF 3.0 veya 3.5 WPF XAML 2006 bağımlılık  
 .NET Framework XAML hizmetlerinde XAML 2006 ya da XAML 2009, WPF ile ilgili sınırlamalar genel XAML kullanım esnek. Yedekleme türü sistem ve nesne modelini desteklemek XAML biçimlendirmesi içinde herhangi bir konumda bir genel nesne öğesi örneği oluşturabilir.  
  
 XAML 2009 kullanıyorsanız, CLR eşleme yerine temel türleri XAML dili ortak temelleri için elde etmek için türler, kullanabileceğiniz [XAML dili ortak temelleri için yerleşik türler](built-in-types-for-common-xaml-language-primitives.md) bilgi öğeleri olarak bir `typeString`. Örneğin, aşağıdaki bildirebilirsiniz (önek eşletirmeleri gösterilmez, ancak x olan XAML dil XAML ad alanı için XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 WPF ve hedeflenirken [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], XAML 2009 özelliklerini ile birlikte kullanabileceğiniz `x:TypeArguments` ancak yalnızca gevşek XAML (biçimlendirme yapılmayan XAML). WPF ve XAML, BAML formu için biçimlendirme derlenmiş XAML şu anda desteklemediğinden XAML 2009 anahtar sözcükleri ve özellikleri. XAML biçimlendirme için derlerseniz, "XAML 2006 ve WPF genel XAML kullanım" bölümünde belirtildiği kısıtlamaları'nın altında çalışması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [x:Type İşaretleme Uzantısı](x-type-markup-extension.md)
- [XAML Dili Ortak Temelleri İçin Yerleşik Türler](built-in-types-for-common-xaml-language-primitives.md)
- [XAML'deki Genel Türler](generics-in-xaml.md)
