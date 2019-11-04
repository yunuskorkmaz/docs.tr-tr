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
ms.openlocfilehash: 7312c59cdcddfdbda39a4a9f05788b6a021f9b75
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459590"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code İç XAML Türü
Bir XAML üretimi içindeki kodun yerleştirilmesine izin verir. Bu kod, XAML 'yi derlenen herhangi bir XAML işlemci uygulamasıyla veya bir çalışma zamanı tarafından yorum gibi daha sonra kullanımlar için XAML üretimde solda derlenir.  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Code` XAML yönergesi öğesi içindeki kod, hala genel XML ad alanı ve belirtilen XAML ad alanları içinde yorumlanıyor. Bu nedenle, genellikle `x:Code` için kullanılan kodu bir `CDATA` segmenti içine almanız gerekir.  
  
 XAML üretiminin tüm olası dağıtım mekanizmaları için `x:Code` izin verilmez. Belirli çerçevelerde (örneğin, WPF) kodun derlenmesi gerekir. Diğer çerçevelerde, `x:Code` kullanım genellikle izin verilmiyor olabilir.  
  
 Yönetilen `x:Code` içeriğine izin veren çerçeveler için, `x:Code` içerik için kullanılacak doğru dil derleyicisi, uygulamayı derlemek için kullanılan içerilen projenin ayarlarına ve hedeflerine göre belirlenir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF için `x:Code` içinde bildirildiği kodun çeşitli önemli sınırlamaları vardır:  
  
- `x:Code` Directive öğesi XAML üretiminin kök öğesinin hemen bir alt öğesi olmalıdır.  
  
- [X:Class yönergesinin](x-class-directive.md) üst kök öğesinde sağlanması gerekir.  
  
- `x:Code` içine yerleştirilmiş kod, derleme tarafından, bu XAML sayfası için zaten oluşturulmakta olan kısmi sınıfın kapsamı içinde olacak şekilde değerlendirilir. Bu nedenle, tanımladığınız tüm kodlar üye veya bu kısmi sınıfın değişkenleri olmalıdır.  
  
- Kısmi sınıfın içindeki bir sınıfı iç içe geçirerek dışında ek sınıflar tanımlayamazsınız (iç içe geçme izin verilir, ancak iç içe geçmiş sınıflara XAML 'de başvurulduğundan, bu normal değildir). Mevcut kısmi sınıf için kullanılan ad alanı dışındaki CLR ad alanları tanımlanamıyor veya öğesine eklenemiyor.  
  
- Kısmi sınıf CLR ad alanı dışındaki kod varlıklarına yapılan başvurular tamamen tam nitelenmiş olmalıdır. Bildirmekte olan Üyeler kısmi sınıf geçersiz kılınabilir Üyeler için geçersiz kılındığında, bu, dile özgü geçersiz kılma anahtar sözcüğü ile belirtilmelidir. `x:Code` kapsamda belirtilen Üyeler XAML dışında oluşturulan kısmi sınıfın üyeleriyle çakışıyorsa, bu şekilde derleyicinin çakışmayı bildirdiği, XAML dosyası derlenemez veya yüklenemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
