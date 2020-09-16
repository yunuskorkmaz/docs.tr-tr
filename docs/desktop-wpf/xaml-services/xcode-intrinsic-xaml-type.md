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
ms.openlocfilehash: ea7bc17cba19137b4e4ca2d8cddb32e6630887c9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544849"
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

`x:Code`Xaml yönergesi öğesi içindeki kod, hala genel XML ad alanı ve BELIRTILEN xaml ad alanları içinde yorumlanıyor. Bu nedenle, genellikle bir segmentin içinde kullanılan kodu kapsamak gereklidir `x:Code` `CDATA` .

`x:Code` XAML üretiminin tüm olası dağıtım mekanizmaları için izin verilmez. Belirli çerçevelerde (örneğin, WPF) kodun derlenmesi gerekir. Diğer çerçevelerde, `x:Code` kullanım genellikle izin verilmiyor olabilir.

Yönetilen içeriğe izin veren çerçeveler için `x:Code` içerik için kullanılacak doğru dil derleyicisi, `x:Code` uygulamayı derlemek için kullanılan içerilen projenin ayarlarına ve hedeflerine göre belirlenir.

## <a name="wpf-usage-notes"></a>WPF kullanım notları

WPF için içinde bildirildiği kodun `x:Code` çeşitli önemli sınırlamaları vardır:

- `x:Code`Directive Öğesı xaml üretiminin kök öğesinin hemen bir alt öğesi olmalıdır.

- [X:Class yönergesinin](xclass-directive.md) üst kök öğesinde sağlanması gerekir.

- İçine yerleştirilmiş kod, `x:Code` derleme tarafından, bu XAML sayfası için zaten oluşturulmakta olan kısmi sınıfın kapsamı dahilinde olacak şekilde değerlendirilir. Bu nedenle, tanımladığınız tüm kodlar üye veya bu kısmi sınıfın değişkenleri olmalıdır.

- Kısmi sınıfın içindeki bir sınıfı iç içe geçirerek dışında ek sınıflar tanımlayamazsınız (iç içe geçme izin verilir, ancak iç içe geçmiş sınıflara XAML 'de başvurulduğundan, bu normal değildir). Mevcut kısmi sınıf için kullanılan ad alanı dışındaki CLR ad alanları tanımlanamıyor veya öğesine eklenemiyor.

- Kısmi sınıf CLR ad alanı dışındaki kod varlıklarına yapılan başvurular tamamen tam nitelenmiş olmalıdır. Bildirmekte olan Üyeler kısmi sınıf geçersiz kılınabilir Üyeler için geçersiz kılındığında, bu, dile özgü geçersiz kılma anahtar sözcüğü ile belirtilmelidir. Kapsamda belirtilen Üyeler `x:Code` xaml dışında oluşturulan kısmi sınıfın üyeleriyle çakışırsa, bu şekilde derleyicinin çakışmayı bildirdiği, xaml dosyası derlenemez veya yüklenemez.

## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](xclass-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
