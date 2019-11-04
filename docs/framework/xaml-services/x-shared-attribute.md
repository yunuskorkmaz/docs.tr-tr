---
title: x:Shared Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: c820a9b1d9708e24b1460378199a6addc1e20899
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459934"
---
# <a name="xshared-attribute"></a>x:Shared Özniteliği
`false`olarak ayarlandığında, tüm istekler için aynı örneği paylaşmak yerine, öznitelikli kaynağa yönelik isteklerin her istek için yeni bir örnek oluşturması için WPF kaynak alımı davranışını değiştirir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Shared` XAML Language XAML ad alanıyla eşlenir ve .NET Framework XAML Hizmetleri ve XAML okuyucuları tarafından geçerli bir XAML dili öğesi olarak tanınır. Ancak, `x:Shared` belirtilen özellikleri yalnızca WPF uygulamaları ve WPF XAML ayrıştırıcısı için geçerlidir. WPF içinde, `x:Shared` yalnızca WPF <xref:System.Windows.ResourceDictionary>içinde bulunan bir nesneye uygulandığında öznitelik olarak faydalıdır. Diğer kullanımlar ayrıştırma özel durumları veya diğer hataları oluşturmaz, ancak hiçbir etkisi yoktur.  
  
 `x:Shared` anlamı XAML dil belirtiminde belirtilmez. .NET Framework XAML Hizmetleri üzerinde derlenenler gibi diğer XAML uygulamaları, kaynak paylaşım desteği sunmamalıdır. Bu tür XAML uygulamaları destekleyici çerçevede `x:Shared` değerleri de kullanan benzer davranışlar sağlayabilir.  
  
 WPF 'de, kaynaklar için varsayılan `x:Shared` koşulu `true`. Bu koşul, belirli bir kaynak isteğinin her zaman aynı örneği döndürdüğü anlamına gelir.  
  
 <xref:System.Windows.FrameworkElement.FindResource%2A>gibi bir kaynak API 'SI aracılığıyla döndürülen bir nesneyi değiştirme veya bir nesneyi doğrudan bir <xref:System.Windows.ResourceDictionary>içinde değiştirme, özgün kaynağı değiştirir. Bu kaynağa yapılan başvurular dinamik kaynak başvurularıyla, bu kaynağın tüketicileri değiştirilen kaynağı alır.  
  
 Kaynağa yapılan başvurular statik kaynak başvurularıyla, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işleme zamanından sonra kaynakta yapılan değişiklikler ilgisizdir. Statik ve dinamik kaynak başvuruları hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 `x:Shared="true"` açıkça belirtilmesi nadiren yapılır, çünkü zaten varsayılan değer. WPF nesne modelinde `x:Shared` için doğrudan kod eşdeğeri yoktur; yalnızca bir XAML kullanımında belirtilebilir ve .NET Framework XAML Hizmetleri ve XAML okuyucuları kullanılarak işlenirse, yükleme yolundaki bir ara XAML düğüm akışında ya da varsayılan WPF davranışına göre işlenmeli.  
  
 `x:Shared="false"` için bir senaryo, kaynak olarak bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş sınıfı tanımlarsanız ve sonra öğe kaynağını bir içerik modeline tanıtdıysanız. `x:Shared="false"`, bir öğe kaynağının aynı koleksiyonda birden çok kez tanıtılmalarını sağlar (örneğin, <xref:System.Windows.Controls.UIElementCollection>). `x:Shared="false"` olmadan bu geçersizdir çünkü koleksiyon içeriklerinin benzersizlik düzeyini zorluyor. Ancak `x:Shared="false"` davranışı aynı örneği döndürmek yerine kaynağın başka bir özdeş örneğini oluşturur.  
  
 `x:Shared="false"` için başka bir senaryo da animasyon değerleri için bir <xref:System.Windows.Freezable> kaynağı kullanıyorsanız ancak kaynağı animasyon temelinde değiştirmek istiyordur.  
  
 `false` dize işleme, büyük/küçük harfe duyarlı değildir.  
  
 WPF 'de, `x:Shared` yalnızca aşağıdaki koşullarda geçerlidir:  
  
- `x:Shared` olan öğeleri içeren <xref:System.Windows.ResourceDictionary> derlenmesi gerekir. <xref:System.Windows.ResourceDictionary> gevşek XAML içinde olamaz veya temalar için kullanılamaz.  
  
- Öğeleri içeren <xref:System.Windows.ResourceDictionary> başka bir <xref:System.Windows.ResourceDictionary>içinde iç içe olmamalıdır. Örneğin, zaten bir <xref:System.Windows.ResourceDictionary> öğesi olan <xref:System.Windows.Style> içinde olan bir <xref:System.Windows.ResourceDictionary> öğeler için `x:Shared` kullanamazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [XAML Kaynakları](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Temel Öğeler](../wpf/advanced/base-elements.md)
