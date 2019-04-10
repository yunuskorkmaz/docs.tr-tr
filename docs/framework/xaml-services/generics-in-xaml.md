---
title: XAML'deki Genel Türler
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9263edf18872f510f5f2f4e3e9cb793e45c5d0b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221606"
---
# <a name="generics-in-xaml"></a>XAML'deki Genel Türler
.NET Framework XAML System.Xaml içinde uygulandığı şekilde hizmetleri genel CLR Türleri kullanma desteği sağlar. Bu destek sınırlamalar genel türler tür bağımsız değişkeni belirtmek ve uygun çağırarak kısıtlamanın zorlanması içerir `Add` genel koleksiyon çalışmaları için yöntemi. Bu konuda, kullanma ve XAML genel türleri başvuran yönleri açıklanmaktadır.  
  
## <a name="xtypearguments"></a>x: TypeArguments  
 `x:TypeArguments` bir yönerge XAML dili tarafından tanımlanır. Genel bir tür tarafından desteklenen bir XAML türünün bir üyesi olarak kullanıldığında `x:TypeArguments` sınırlama geçişleri genel yedekleme oluşturucusuna bağımsız değişkenlerini yazın. .NET Framework XAML hizmetlerinde için ilgili başvuru sözdizimi için kullanım `x:TypeArguments`söz dizimi örneklerini içerir, bkz: [x: TypeArguments yönergesi](x-typearguments-directive.md).  
  
 Çünkü `x:TypeArguments` bir dize alır ve tür dönüştürücüsünü yedekleme sahip genellikle XAML kullanımı özniteliği olarak bildirilir.  
  
 XAML düğüm akış bilgileri tarafından bildirilen `x:TypeArguments` örneğinden alınabilen <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> konumundaki bir `StartObject` düğüm akışta konumu. Dönüş değeri <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> listesidir <xref:System.Xaml.XamlType> değerleri. XAML tür genel bir tür olup olmadığını temsil belirleme çağırarak yapılabilir <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>XAML'nda genel türler için söz dizimi kurallar  
 XAML içinde genel bir tür her zaman kısıtlı genel temsil edilmesi gereken; Sınırlandırılmamış bir genel hiçbir zaman XAML tür sistemine veya XAML düğümü akışı bulunur ve XAML biçimlendirmede gösterilemez. Genel bir iç içe geçmiş tür kısıtlaması tarafından başvurulan genel olduğu durumlar için XAML öznitelik sözdizimi içinde başvurulabilir `x:TypeArguments`, veya durumları için burada `x:Type` genel bir tür için bir CLR türü başvuru sağlar. Bu aracılığıyla desteklenir <xref:System.Xaml.Schema.XamlTypeTypeConverter> .NET Framework XAML hizmetlerinde tarafından tanımlanan sınıfı.  
  
 XAML öznitelik söz dizimi biçimi etkinleştirilir <xref:System.Xaml.Schema.XamlTypeTypeConverter> tipik MSIL değiştirir / açısını kullanan CLR sözdizimi kuralı türleri ve sınırlamalar genel türler için köşeli ayraçlar ve bunun yerine kısıtlaması kapsayıcısı için parantez yerini alır. Bir örnek için bkz. [x: TypeArguments yönergesi](x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Genel türler ve XAML 2009 özelliklerini  
 XAML 2009 kullanıyorsanız, CLR eşleme yerine temel türleri XAML dili ortak temelleri için elde etmek için türler, kullanabileceğiniz [XAML 2009 yerleşik türler](built-in-types-for-common-xaml-language-primitives.md) bilgi öğeleri olarak `x:TypeArguments`. Örneğin, aşağıdaki bildirebilirsiniz (önek eşlemeleri gösterilmez, ancak `x` XAML dil XAML ad alanı için XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>WPF ve diğer v3.5 çerçeveleri genel türler desteği  
 WPF, hedeflenirken özellikle XAML 2006 kullanım için [x: Class](x-class-directive.md) aynı öğede sağlanmalıdır `x:TypeArguments`, ve bu öğe bir XAML belgesi kök öğesi olması gerekir. Kök öğe en az bir tür bağımsız değişkeni ile genel tür eşlenmelidir. <xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir.  
  
 Genel türler döndüren özel biçimlendirme uzantısı tanımlama ya bir sarmalama sağlayan genel kullanımları desteklemek için olası geçici çözümleri dahil sınıf tanımının genel türünden türer, ancak kendi sınıf tanımında genel kısıtlama düzleştirir.  
  
 WPF ve hedefleme [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], XAML 2009 özelliklerini ile birlikte kullanabileceğiniz `x:TypeArguments`, ancak yalnızca gevşek XAML (biçimlendirme yapılmayan XAML). WPF ve XAML, BAML formu için biçimlendirme derlenmiş XAML şu anda desteklemediğinden XAML 2009 anahtar sözcükleri ve özellikleri.  
  
 Windows Workflow Foundation için özel iş akışlarında [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] genel XAML kullanımını desteklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:TypeArguments Yönergesi](x-typearguments-directive.md)
- [x:Class Yönergesi](x-class-directive.md)
- [XAML Dili Ortak Temelleri İçin Yerleşik Türler](built-in-types-for-common-xaml-language-primitives.md)
