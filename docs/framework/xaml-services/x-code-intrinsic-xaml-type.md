---
title: x:Code İç XAML Türü
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 7bb78b05be7b3edc4471bc276010eabd92a07a14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145242"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code İç XAML Türü
Kod içinde bir XAML üretim yerleşimi sağlar. Bu tür kod ya da XAML veya bir çalışma zamanı tarafından yorumu gibi sonraki kullanımlar için XAML üretimde sol derleyen herhangi XAML işlemci uygulamasında tarafından derlenebilir.  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 İçindeki kod `x:Code` XAML yönerge öğesi olduğundan hala genel XML ad alanı içinde yorumlanan ve sağlanan XAML ad alanları. Bu nedenle, genellikle için kullanılan kod içine alın gerekmez, `x:Code` içinde bir `CDATA` kesimi.  
  
 `x:Code` XAML üretim tüm olası dağıtım mekanizmaları için izin verilmez. Belirli çerçeveleri (örneğin, WPF) kod olarak derlenmelidir. Diğer çerçeveleri de `x:Code` kullanım genellikle izin verilmiyor.  
  
 Yönetilen izin çerçeveler için `x:Code` içerik, kullanılacak doğru dil derleyicisi `x:Code` içeriği, ayarları ve uygulama derlemek için kullanılan içeren projenin hedefleri tarafından belirlenir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Bildirilen kod içinde `x:Code` WPF birkaç önemli sınırlamaları vardır:  
  
-   `x:Code` Yönerge öğesi, XAML üretim kök öğesinin ilk alt öğesi olmalıdır.  
  
-   [x: Class yönergesi](x-class-directive.md) üst kök öğe üzerinde sağlanmalıdır.  
  
-   Kod içinde yerleştirilen `x:Code` için bu XAML sayfası oluşturulmakta olan kısmi sınıf kapsamında olmasını derleme tarafından kabul edilir. Bu nedenle tanımladığınız tüm kodları üyeleri veya kısmi söz konusu sınıfın değişkenleri olmalıdır.  
  
-   ' Den başka bir sınıf kısmi sınıf içinde iç içe tarafından ek sınıfları tanımlanamaz (iç içe geçme izin verilir, ancak iç içe geçmiş sınıflar XAML içinde başvurulduğundan, tipik değildir). CLR ad var olan kısmi sınıf için kullanılan ad alanı dışında tanımlanan veya eklenmiştir.  
  
-   Kısmi sınıf CLR ad alanı dışında kod varlıklara başvurular tüm tam olarak nitelenmiş olmalıdır. Bildirilen üyeleri geçersiz kılmalar için geçersiz kılınabilir kısmi sınıf üyeleri, bu dile özgü geçersiz kılma anahtar sözcüğü ile belirtilmelidir. Üyeleri bildirilmişlerse `x:Code` kapsam çakışan XAML dışında oluşturulan bir kısmi sınıf üyelerine, şekilde derleyici çakışma raporları XAML dosyası derleme yüklemek veya.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
