---
title: x:Shared Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: e1cd1d9db5c19decd840b433f986e0ba53557a8b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071376"
---
# <a name="xshared-attribute"></a>x:Shared Özniteliği

`false`Ayarlandığında, wpf kaynak alma davranışını değiştirir, böylece atfedilen kaynak istekleri tüm istekler için aynı örneği paylaşmak yerine her istek için yeni bir örnek oluşturur.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>Açıklamalar

`x:Shared`XAML dili XAML ad alanına eşlenir ve .NET XAML Hizmetleri ve XAML okuyucuları tarafından geçerli bir XAML dil öğesi olarak kabul edilir. Ancak, belirtilen yetenekleri `x:Shared` yalnızca WPF uygulamaları ve WPF XAML araparıcısı için geçerlidir. WPF'de, `x:Shared` yalnızca WPF <xref:System.Windows.ResourceDictionary>içinde bulunan bir nesneye uygulandığında öznitelik olarak kullanışlıdır. Diğer kullanımlar ayrıştırma özel durumları veya diğer hatalar atmayın, ancak hiçbir etkisi yoktur.

Anlamı XAML dil belirtiminde `x:Shared` belirtilmemiştir. .NET XAML Hizmetleri'ni temel alanlar gibi diğer XAML uygulamaları mutlaka kaynak paylaşımı desteği sağlamaz. Bu tür XAML uygulamaları, değerleri de kullanan `x:Shared` destekleyici çerçevede benzer davranışlar sağlayabilir.

WPF'de, `x:Shared` kaynakların varsayılan `true`koşulu . Bu durum, verilen herhangi bir kaynak isteğinin her zaman aynı örneği döndürdeğini anlamına gelir.

Kaynak API'si aracılığıyla döndürülen bir <xref:System.Windows.FrameworkElement.FindResource%2A>nesneyi değiştirme (örneğin, <xref:System.Windows.ResourceDictionary>bir nesneyi doğrudan içinde değiştirmek), özgün kaynağı değiştirir. Bu kaynağa yapılan başvurular dinamik kaynak başvurularıysa, bu kaynağın tüketicileri değiştirilen kaynağı alır.

Kaynağa yapılan başvurular statik kaynak başvurularıysa, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlem süresinden sonra kaynakta yapılan değişiklikler önemsizdir. Statik ve dinamik kaynak başvuruları hakkında daha fazla bilgi için Bkz. [XAML Kaynakları.](../fundamentals/xaml-resources-define.md)

Açıkça belirtme `x:Shared="true"` nadiren yapılır, çünkü bu zaten varsayılandır. WPF nesne `x:Shared` modelinde doğrudan kod eşdeğeri yoktur; yalnızca bir XAML kullanımında belirtilebilir ve .NET XAML Hizmetleri ve XAML okuyucuları kullanılarak işlenirse, varsayılan WPF davranışı veya yük yolundaki bir ara XAML düğüm akışı ile işlenmesi gerekir.

Bir veya `x:Shared="false"` <xref:System.Windows.FrameworkContentElement> türemiş <xref:System.Windows.FrameworkElement> sınıfı kaynak olarak tanımlar ve ardından öğe kaynağını bir içerik modeline tanıtırsanız, bunun için bir senaryodur. `x:Shared="false"`bir öğe kaynağının aynı koleksiyona birden çok kez tanıtılmasını sağlar <xref:System.Windows.Controls.UIElementCollection>(örneğin. Bu `x:Shared="false"` olmadan geçersizdir, çünkü koleksiyon içeriğinin benzersizliğini zorlar. Ancak, `x:Shared="false"` davranış, aynı örneği döndürmek yerine kaynağın başka bir aynı örneğini oluşturur.

Animasyon değerleri `x:Shared="false"` için bir <xref:System.Windows.Freezable> kaynak kullanmak ancak kaynağı animasyon bazında değiştirmek istiyorsanız, başka bir senaryo.

Dize kullanımı `false` büyük/küçük harf duyarlı değildir.

WPF'de, `x:Shared` yalnızca aşağıdaki koşullar altında geçerlidir:

- Bu <xref:System.Windows.ResourceDictionary> öğeleri `x:Shared` içeren derlenmiş olmalıdır. Gevşek <xref:System.Windows.ResourceDictionary> XAML içinde olamaz veya temalar için kullanılamaz.

- Öğeleri <xref:System.Windows.ResourceDictionary> içeren başka bir iç <xref:System.Windows.ResourceDictionary>içe olmamalıdır. Örneğin, zaten bir `x:Shared` <xref:System.Windows.ResourceDictionary> öğe olan <xref:System.Windows.ResourceDictionary> bir <xref:System.Windows.Style> içindeki maddeler için kullanamazsınız.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [XAML Kaynakları](../fundamentals/xaml-resources-define.md)
- [Temel Öğeler](../../framework/wpf/advanced/base-elements.md)
