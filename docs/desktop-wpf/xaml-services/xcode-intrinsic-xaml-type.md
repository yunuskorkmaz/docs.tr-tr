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
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071558"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code İç XAML Türü
Kodun XAML üretimi ne rendesi içine yerleştirilmesine izin verir. Bu tür kod, XAML'yi derleyen herhangi bir XAML işlemci uygulaması tarafından derlenebilir veya daha sonraki kullanımlar için XAML üretiminde bırakılabilir.

## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>Açıklamalar

`x:Code` XAML yönerge öğesi içindeki kod, yine de genel XML ad alanı ve sağlanan XAML ad alanları içinde yorumlanır. Bu nedenle, genellikle bir `x:Code` `CDATA` segment içinde kullanılan kodu içine almak için gereklidir.

`x:Code`bir XAML üretiminin olası tüm dağıtım mekanizmaları için izin verilmez. Belirli çerçevelerde (örneğin WPF) kod derlenmelidir. Diğer çerçevelerde, `x:Code` kullanıma genellikle izin verilemeyebilir.

Yönetilen `x:Code` içeriğe izin veren çerçeveler için, içerik `x:Code` için kullanılacak doğru dil derleyicisi, uygulamayı derlemek için kullanılan içeren projenin ayarları ve hedefleri tarafından belirlenir.

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

WPF `x:Code` için bildirilen kodun birkaç önemli sınırlaması vardır:

- Yönerge öğesi XAML `x:Code` üretiminin kök elemanının hemen bir alt öğesi olmalıdır.

- [x:Sınıf Yönergesi](xclass-directive.md) ana kök öğesi üzerinde sağlanmalıdır.

- İçe `x:Code` yerleştirilen kod, o XAML sayfası için zaten oluşturulmakta olan kısmi sınıfın kapsamı içinde olmak üzere derleme ile işlem göreceksiniz. Bu nedenle tanımladığınız tüm kod, o kısmi sınıfın üyeleri veya değişkenleri olmalıdır.

- Kısmi sınıfın içinde bir sınıf iç içe geçme dışında ek sınıflar tanımlayamazsınız (iç içe geçmeizin verilir, ancak iç içe geçen sınıflar XAML'de başvurulamadığından tipik değildir). Varolan kısmi sınıf için kullanılan ad alanı dışındaki CLR ad alanları tanımlanamaz veya eklenemez.

- Kısmi sınıf CLR ad alanı dışındaki kod varlıklarına yapılan başvuruların tümü tam olarak nitelikli olmalıdır. Bildirilen üyeler kısmi sınıf geçersiz kılınan üyelere geçersiz kılınmışsa, bunun dile özgü geçersiz kılma anahtar sözcüğüyle belirtilmesi gerekir. `x:Code` Kapsamda bildirilen üyeler XAML dışında oluşturulan kısmi sınıfın üyeleriyle, derleyiciçleçliği bildirebilecek şekilde çakışacak şekilde çakışırsa, XAML dosyası derleyemez veya yüklenemez.

## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](xclass-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
