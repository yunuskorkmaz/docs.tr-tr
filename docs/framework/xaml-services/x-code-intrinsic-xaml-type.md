---
title: "x:Code İç XAML Türü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d39249a5d1c0e230d21e6d889b92d0b57c98e2ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code İç XAML Türü
XAML üretim içindeki kod yerleşimini sağlar. Bu tür kodu ya da XAML ya da bir çalışma zamanı tarafından tercüme gibi sonraki kullanımlar için XAML üretimde sol derler herhangi bir XAML işlemci uygulaması tarafından derlenebilir.  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 İçindeki kod `x:Code` genel XML ad alanı içinde yorumlanan hala ve sağlanan XAML ad uzayları XAML yönerge öğesi değil. Bu nedenle, için kullanılan kod içine genellikle gerekli `x:Code` içinde bir `CDATA` kesimi.  
  
 `x:Code`XAML üretim tüm olası dağıtım mekanizmaları izin verilmez. Belirli çerçeveleri (örneğin, WPF) derlenmiş kod gerekir. Diğer çerçeveler içinde `x:Code` kullanım genellikle izin verilmiyor.  
  
 Yönetilen izin çerçeveler için `x:Code` içerik, kullanılmak üzere doğru dil derleyici `x:Code` içerik ayarları ve uygulama derlemek için kullanılan içeren proje hedefleri tarafından belirlenir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Kod bildirilen içinde `x:Code` WPF birkaç önemli sınırlamalara sahiptir:  
  
-   `x:Code` Yönerge öğesi XAML üretim kök öğesinin hemen alt öğesi olması gerekir.  
  
-   [x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md) üst kök öğesinde sağlanmalıdır.  
  
-   Kod içinde yerleştirilen `x:Code` bu XAML sayfası için zaten oluşturuldu parçalı sınıf kapsamında olması için derleme tarafından kabul edilir. Bu nedenle tanımladığınız tüm kod üyeleri veya kısmi o sınıfın değişkenleri olmalıdır.  
  
-   Bir sınıf parçalı sınıf içinde iç içe geçme tarafından dışında ek sınıfları tanımlayamazsınız (iç içe geçme izin verilir, ancak iç içe geçmiş sınıflar XAML'de başvurduğundan tipik değil). CLR ad alanları için varolan sınıfa kullanılan ad alanı dışında tanımlanmış veya eklenmiştir.  
  
-   Kodu varlıkları parçalı sınıf CLR ad alanı dışında başvurular tümü tam olarak nitelenmiş olmalıdır. Bildirilen üyeleri geçersiz kılmalar kısmi sınıfı geçersiz kılınabilir üyeleri varsa, bu dile özgü geçersiz kılma anahtar sözcüğü ile belirtilmelidir. Bildirilen üyeleri varsa `x:Code` kapsam çakışan XAML dışında oluşturulan kısmi sınıfının üyeleriyle, bir şekilde derleyici çakışma raporları XAML dosyası derleme yüklemek veya olamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x:Class Yönergesi](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Arka Plan Kod ve WPF İçindeki XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
