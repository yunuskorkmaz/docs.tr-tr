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
ms.openlocfilehash: 2e64c716ee85934bf02c016ee408b8e5f612a819
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837200"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments Yönergesi
Bir genel öğesinin kısıtlayan tür bağımsız değişkenlerini genel türün oluşturucusuna geçirir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`object`|Bir CLR genel türü tarafından desteklenen bir XAML türünün nesne öğesi bildirimi. `object`, varsayılan XAML ad alanından olmayan bir XAML türüne başvuruyorsa, `object`, `object` var olan XAML ad alanını belirtmek için bir ön ek gerektirir.|  
|`typeString`|CLR genel türü için tür bağımsız değişkenlerini sağlayan dizeler olarak bir veya daha fazla XAML tür adı bildiren bir dize. Ek sözdizimi notları için bkz. açıklamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çoğu durumda, bir `typeString` dizesinde bilgi öğesi olarak kullanılan XAML türleri önek olarak eklenir. CLR genel kısıtlamalarının tipik türleri (örneğin, <xref:System.Int32> ve <xref:System.String>) CLR temel sınıf kitaplıklarından gelir. Bu kitaplıklar, çerçeveye özgü tipik varsayılan XAML ad alanları ile eşlenmedi ve bu nedenle XAML kullanımı için bir ön ek eşlemesi gerektirir.  
  
 Bir virgül sınırlayıcısı kullanarak birden çok XAML türü adı belirtebilirsiniz.  
  
 Genel kısıtlamalar genel türler kullanıyorsa, iç içe geçmiş kısıtlama türü bağımsız değişkenleri parantez () ile yer alabilir.  
  
 Bu `x:TypeArguments` tanımının .NET Framework XAML hizmetlerine özgü olduğunu ve CLR yedeklemesini kullandığını unutmayın. Dil düzeyi tanımı [\[MS-XAML\] Bölüm 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bulunabilir.  
  
## <a name="usage-examples"></a>Kullanım örnekleri  
 Bu örnekler için aşağıdaki XAML ad alanı tanımlarının bildirildiği varsayılır:  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>\<dize > Listele  
 `<scg:List x:TypeArguments="sys:String" ...>`, <xref:System.String> Type bağımsız değişkeniyle yeni bir <xref:System.Collections.Generic.List%601> oluşturur.  
  
### <a name="dictionarystringstring"></a>Sözlük\<dize, dize >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` iki <xref:System.String> tür bağımsız değişkeni ile yeni bir <xref:System.Collections.Generic.Dictionary%602> oluşturur.  
  
### <a name="queuekeyvaluepairstringstring"></a>Sıra < KeyValuePair\<dize, dize > >  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` iç kısıtlama türü bağımsız değişkenleri <xref:System.String> ve <xref:System.String>olan <xref:System.Collections.Generic.KeyValuePair%602> kısıtlamasına sahip yeni bir <xref:System.Collections.Generic.Queue%601> oluşturur.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 ve WPF Genel XAML kullanımları  
 XAML 2006 kullanımı ve WPF uygulamaları için kullanılan XAML için, genel olarak XAML 'den `x:TypeArguments` ve genel tür kullanımları için aşağıdaki kısıtlamalar mevcuttur:  
  
- Yalnızca bir XAML dosyasının kök öğesi genel bir türe başvuran Genel XAML kullanımını destekleyebilir.  
  
- Kök öğe, en az bir tür bağımsız değişkeni olan genel bir türe eşleşmelidir. <xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir. Sayfa işlevleri, WPF 'de XAML genel kullanım desteğinin birincil senaryosudur.  
  
- Genel için kök öğe XAML nesne öğesi, `x:Class`kullanarak da kısmi bir sınıf bildirmelidir. Bu, WPF oluşturma eylemi tanımlansa bile geçerlidir.  
  
- `x:TypeArguments` iç içe geçmiş genel kısıtlamalara başvuramaz.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>WPF 3,0 veya WPF 3,5 bağımlılığı olmayan XAML 2009 veya XAML 2006  
 XAML 2006 ya da xaml 2009 için .NET Framework XAML hizmetlerinde, genel XAML kullanımıyla ilgili WPF ile ilgili kısıtlamalar gevşek bir şekilde yapılır. XAML biçimlendirmesinde, yedekleme türü sisteminin ve nesne modelinin destekleyebileceği herhangi bir konumda genel nesne öğesi örneği oluşturabilirsiniz.  
  
 Ortak dil temelleri için XAML türleri almak üzere CLR temel türlerini eşlemek yerine XAML 2009 kullanıyorsanız, bir `typeString`bilgi öğeleri olarak [ortak xaml dil temel öğeleri Için yerleşik türleri](built-in-types-for-common-xaml-language-primitives.md) kullanabilirsiniz. Örneğin, aşağıdaki bildirimi yapabilirsiniz (önek eşlemeleri gösterilmez, ancak x, XAML 2009 için XAML Language xaml ad alanıdır):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 WPF 'de ve .NET Framework 4 ' i hedeflerken, XAML 2009 özelliklerini `x:TypeArguments` ile birlikte kullanabilirsiniz ancak yalnızca gevşek XAML (biçimlendirme ile derlenen XAML) için. WPF için biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 anahtar sözcüklerini ve özelliklerini desteklememektedir. XAML 'yi derlemeyi işaretlemeyi gerekiyorsa, "XAML 2006 ve WPF Genel XAML kullanımları" bölümünde belirtilen kısıtlamalar altında işlem yapmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [x:Type İşaretleme Uzantısı](x-type-markup-extension.md)
- [XAML Dili Ortak Temelleri İçin Yerleşik Türler](built-in-types-for-common-xaml-language-primitives.md)
- [XAML'deki Genel Türler](generics-in-xaml.md)
