---
title: XAML'deki Genel Türler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e64224edcb49d5040332b7cef9649c98cf26798b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="generics-in-xaml"></a>XAML'deki Genel Türler
.NET Framework XAML System.Xaml içinde uygulandığı şekilde hizmetleri genel CLR Türleri kullanma için destek sağlar. Bu destek tür bağımsız değişkeni olarak genel türler kısıtlamaları belirtme ve uygun çağırarak kısıtlaması uygulayan içerir `Add` genel koleksiyon durumlarda yöntemi. Bu konuda kullanarak ve XAML'deki genel türler başvuran yönleri açıklanmaktadır.  
  
## <a name="xtypearguments"></a>x: TypeArguments  
 `x:TypeArguments` bir yönerge XAML dili tarafından tanımlanır. Genel bir tür tarafından yedeklenen bir XAML türünün bir üyesi olarak kullanıldığında `x:TypeArguments` sınırlama geçişleri genel yedekleme oluşturucuya bağımsız değişkenlerini yazın. .NET Framework XAML Hizmetleri için ilgili başvuru sözdizimi kullanımı `x:TypeArguments`sözdizimi örneklerini içerir, bkz: [x: TypeArguments yönergesi](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
 Çünkü `x:TypeArguments` bir dize alır ve türü dönüştürücü yedekleme sahip bir öznitelik olarak XAML kullanımı genellikle bildirilmedi.  
  
 XAML düğümü akışı bilgileri tarafından bildirilen `x:TypeArguments` yükseltebilmeniz <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> adresindeki bir `StartObject` düğümü akışı konumu. Dönüş değerini <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> listesidir <xref:System.Xaml.XamlType> değerleri. XAML tür genel bir tür olup olmadığını temsil eder, belirleme çağırarak yapılabilir <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>XAML'deki sözdizimi kurallar  
 XAML'de, genel bir tür her zaman kısıtlı genel gösterilmelidir; Kısıtlanmamış genel hiçbir zaman XAML tür sistemi veya bir XAML düğüm akış var ve XAML biçimlendirme gösterilemez. Genel bir iç içe geçmiş tür kısıtlaması tarafından başvurulan genel olduğu durumlarda XAML öznitelik sözdizimi içinde başvurulan `x:TypeArguments`, veya durumlarda burada `x:Type` genel bir tür için CLR türü başvuru sağlar. Bu aracılığıyla desteklendiğinden <xref:System.Xaml.Schema.XamlTypeTypeConverter> .NET Framework XAML Hizmetleri tarafından tanımlanan sınıfı.  
  
 XAML özniteliği tarafından etkin sözdizimi form <xref:System.Xaml.Schema.XamlTypeTypeConverter> tipik MSIL değiştirir / açısını kullanan CLR sözdizimi kuralı türleri ve genel türler kısıtlamaları için köşeli ayraçlar ve bunun yerine kısıtlaması kapsayıcısı için parantez değiştirir. Bir örnek için bkz: [x: TypeArguments yönergesi](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Genel türler ve XAML 2009 özellikleri  
 XAML 2009 kullanırsanız, ortak dil temelleri için XAML türlerinin edinilir türleri temel CLR eşleme yerine, kullanabileceğiniz [XAML 2009'dan yerleşik türleri](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) bilgi öğeleri olarak `x:TypeArguments`. Örneğin, aşağıdaki bildirebilirsiniz (önek eşlemeleri gösterilmez, ancak `x` XAML 2009 için XAML dili XAML ad):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>WPF ve diğer v3.5 çerçeveleri genel türler desteği  
 WPF, özellikle hedeflerken XAML 2006 kullanım için [x: Class](../../../docs/framework/xaml-services/x-class-directive.md) aynı öğede sağlanmalıdır `x:TypeArguments`, ve bu öğe bir XAML belgesinde kök öğe olmalıdır. Kök öğesi en az bir tür bağımsız değişkeni ile genel tür eşlenmelidir. Örnek <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Genel kullanımları desteklemek için olası geçici çözümler arasında genel türler döndürebilen özel biçimlendirme uzantısı tanımlama ya da bir kaydırma sağlayan sınıf tanımının genel türünden ancak kendi sınıf tanımını genel kısıtlamasında düzleştirir.  
  
 WPF ve hedefleme [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], XAML 2009 özellikleri ile birlikte kullanabileceğiniz `x:TypeArguments`, ancak yalnızca gevşek XAML (işaretleme-derlenmemiş XAML). XAML biçimlendirme derlenmiş WPF ve XAML BAML form için şu anda desteklemediği XAML 2009 anahtar sözcükleri ve özellikler.  
  
 Özel iş akışları için Windows Workflow Foundation'ın [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] genel XAML kullanımı desteklemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x:TypeArguments Yönergesi](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [x:Class Yönergesi](../../../docs/framework/xaml-services/x-class-directive.md)  
 [XAML Dili Ortak Temelleri İçin Yerleşik Türler](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
