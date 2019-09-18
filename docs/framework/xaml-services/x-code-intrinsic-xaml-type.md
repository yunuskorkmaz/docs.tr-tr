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
ms.openlocfilehash: 2b7713548b6269f079ef32b5bf1fe4fa630edcc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053788"
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
 `x:Code` Xaml yönergesi öğesi içindeki kod, hala genel XML ad alanı ve belirtilen xaml ad alanları içinde yorumlanıyor. Bu nedenle, genellikle bir `x:Code` `CDATA` segmentin içinde kullanılan kodu kapsamak gereklidir.  
  
 `x:Code`XAML üretiminin tüm olası dağıtım mekanizmaları için izin verilmez. Belirli çerçevelerde (örneğin, WPF) kodun derlenmesi gerekir. Diğer çerçevelerde, `x:Code` kullanım genellikle izin verilmiyor olabilir.  
  
 Yönetilen `x:Code` içeriğe izin veren çerçeveler için içerik için `x:Code` kullanılacak doğru dil derleyicisi, uygulamayı derlemek için kullanılan içerilen projenin ayarlarına ve hedeflerine göre belirlenir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF için içinde `x:Code` bildirildiği kodun çeşitli önemli sınırlamaları vardır:  
  
- `x:Code` Directive öğesi xaml üretiminin kök öğesinin hemen bir alt öğesi olmalıdır.  
  
- [X:Class yönergesinin](x-class-directive.md) üst kök öğesinde sağlanması gerekir.  
  
- İçine `x:Code` yerleştirilmiş kod, derleme tarafından, bu XAML sayfası için zaten oluşturulmakta olan kısmi sınıfın kapsamı dahilinde olacak şekilde değerlendirilir. Bu nedenle, tanımladığınız tüm kodlar üye veya bu kısmi sınıfın değişkenleri olmalıdır.  
  
- Kısmi sınıfın içindeki bir sınıfı iç içe geçirerek dışında ek sınıflar tanımlayamazsınız (iç içe geçme izin verilir, ancak iç içe geçmiş sınıflara XAML 'de başvurulduğundan, bu normal değildir). Mevcut kısmi sınıf için kullanılan ad alanı dışındaki CLR ad alanları tanımlanamıyor veya öğesine eklenemiyor.  
  
- Kısmi sınıf CLR ad alanı dışındaki kod varlıklarına yapılan başvurular tamamen tam nitelenmiş olmalıdır. Bildirmekte olan Üyeler kısmi sınıf geçersiz kılınabilir Üyeler için geçersiz kılındığında, bu, dile özgü geçersiz kılma anahtar sözcüğü ile belirtilmelidir. `x:Code` Kapsamda belirtilen Üyeler xaml dışında oluşturulan kısmi sınıfın üyeleriyle çakışırsa, bu şekilde derleyicinin çakışmayı bildirdiği, xaml dosyası derlenemez veya yüklenemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
