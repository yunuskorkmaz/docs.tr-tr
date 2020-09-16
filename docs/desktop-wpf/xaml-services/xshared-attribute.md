---
title: x:Shared Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: d5000b51d83066ec2d529db2033d8ac54f7ad329
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557794"
---
# <a name="xshared-attribute"></a>x:Shared Özniteliği

Olarak ayarlandığında `false` , öznitelikli kaynağa yönelik isteklerin tüm istekler için aynı örneği paylaşmak yerine her istek için yeni bir örnek oluşturması IÇIN WPF kaynak alımı davranışını değiştirir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>Açıklamalar

`x:Shared` , XAML Language XAML ad alanı ile eşlenir ve .NET XAML Hizmetleri ve XAML okuyucuları tarafından geçerli bir XAML dili öğesi olarak tanınır. Bununla birlikte, belirtilen özellikleri `x:Shared` yalnızca WPF uygulamaları ve WPF XAML ayrıştırıcısı için geçerlidir. WPF içinde `x:Shared` yalnızca BIR WPF içinde bulunan bir nesneye uygulandığında öznitelik olarak faydalıdır <xref:System.Windows.ResourceDictionary> . Diğer kullanımlar ayrıştırma özel durumları veya diğer hataları oluşturmaz, ancak hiçbir etkisi yoktur.

Öğesinin anlamı `x:Shared` xaml dil belirtiminde belirtilmemiş. .NET XAML Hizmetleri üzerinde derlenenler gibi diğer XAML uygulamaları, kaynak paylaşım desteği sunmamalıdır. Bu tür XAML uygulamaları destekleyici çerçevede değerleri de kullanan benzer davranışlar sağlayabilir `x:Shared` .

WPF 'de, `x:Shared` kaynaklar için varsayılan koşul `true` . Bu koşul, belirli bir kaynak isteğinin her zaman aynı örneği döndürdüğü anlamına gelir.

Bir kaynak API 'SI aracılığıyla döndürülen <xref:System.Windows.FrameworkElement.FindResource%2A> veya bir nesneyi doğrudan bir içinde değiştiren bir nesneyi değiştirme <xref:System.Windows.ResourceDictionary> , özgün kaynağı değiştirir. Bu kaynağa yapılan başvurular dinamik kaynak başvurularıyla, bu kaynağın tüketicileri değiştirilen kaynağı alır.

Kaynağa yapılan başvurular statik kaynak başvurularıyla, işlem zamanından sonra kaynakta yapılan değişiklikler [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ilgisizdir. Statik ve dinamik kaynak başvuruları hakkında daha fazla bilgi için bkz. [xaml kaynakları](../fundamentals/xaml-resources-define.md).

Açıkça belirtilmesi `x:Shared="true"` nadiren yapılır, çünkü zaten varsayılan değer. WPF nesne modelinde doğrudan kod eşdeğeri yoktur `x:Shared` ; yalnızca BIR xaml kullanımında belirtilebilir ve .net xaml Hizmetleri ve xaml okuyucuları kullanılarak işlenirse, yükleme yolundaki bir ara xaml düğüm akışında işlenmelidir.

Bir senaryosu `x:Shared="false"` , bir <xref:System.Windows.FrameworkElement> veya türetilmiş bir <xref:System.Windows.FrameworkContentElement> sınıfı kaynak olarak tanımlarsanız ve sonra öğe kaynağını bir içerik modeline tanıtdıysanız. `x:Shared="false"` bir öğe kaynağının aynı koleksiyonda birden çok kez tanıtılmalarını sağlar (örneğin, <xref:System.Windows.Controls.UIElementCollection> ). `x:Shared="false"`Bu geçersizdir çünkü koleksiyon içeriklerinin benzersizlik düzeyini zorluyor. Ancak, bu `x:Shared="false"` davranış aynı örneği döndürmek yerine kaynağın bir özdeş örneğini oluşturur.

İçin başka bir senaryo `x:Shared="false"` da <xref:System.Windows.Freezable> animasyon değerleri için bir kaynak kullanıyorsanız ancak kaynağı animasyon temelinde değiştirmek istiyordur.

Dize işleme, `false` büyük/küçük harfe duyarlı değildir.

WPF 'de `x:Shared` yalnızca aşağıdaki koşullarda geçerlidir:

- <xref:System.Windows.ResourceDictionary>Öğesini içeren öğeleri içeren öğesi `x:Shared` derlenmesi gerekir. <xref:System.Windows.ResourceDictionary>Gevşek XAML içinde olamaz veya temalar için kullanılamaz.

- <xref:System.Windows.ResourceDictionary>Öğeleri içeren öğesi başka bir içinde iç içe olmamalıdır <xref:System.Windows.ResourceDictionary> . Örneğin, bir `x:Shared` öğesi zaten bir öğe olan içindeki öğeleri için kullanamazsınız <xref:System.Windows.ResourceDictionary> <xref:System.Windows.Style> <xref:System.Windows.ResourceDictionary> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [XAML Kaynakları](../fundamentals/xaml-resources-define.md)
- [Temel Öğeler](/dotnet/desktop/wpf/advanced/base-elements)
