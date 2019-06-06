---
title: x:Class Yönergesi
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: ee94d7bf52f3fb2ea534cdb2f44d0be2cc8699eb
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689405"
---
# <a name="xclass-directive"></a>x:Class Yönergesi
Kısmi sınıflar işaretleme ve arka plan kod arasında katılmak XAML biçimlendirmesi derleme yapılandırır. Kodu kısmi sınıfın içinde ayrı bir kod dosyasında tanımlanan bir [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] dilin biçimlendirme kısmi sınıf genellikle XAML derleme sırasında kod oluşturma tarafından oluşturulur ancak.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`namespace`|İsteğe bağlı. Belirtir bir [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] tarafından tanımlanan bir parçalı sınıf içeren ad alanı `classname`. Varsa `namespace` belirtilirse, nokta (.) ayıran `namespace` ve `classname`. Açıklamalara bakın.|  
|`classname`|Gerekli. Belirtir [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] yüklenen XAML ve kod arka plan için bu XAML bağlanan kısmi sınıf adı.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 `x:Class` yalnızca XAML üretim kök öğe üzerinde belirtilebilir. `x:Class` bir üst öğeye sahipse XAML üretimde herhangi bir nesne üzerinde geçerli değil. Daha fazla bilgi için [ \[MS-XAML\] bölümü 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Açıklamalar  
 `namespace` Değeri hangi .NET Framework programlamada genel teknik, ilgili ad alanları ad Hiyerarşiler düzenlemek için ek nokta içerebilir. Yalnızca son nokta dizesindeki `x:Class` değerlerini ayırmak için yorumlanır `namespace` ve `classname.` olarak kullanılan sınıf `x:Class` iç içe geçmiş sınıf olamaz. İç içe geçmiş sınıflar için nokta anlamını belirlemek için izin verilmez `x:Class` dizeleri, iç içe geçmiş sınıflar izin veriyorsa belirsiz.  
  
 Programlama modelleri kullanan mevcut `x:Class`, `x:Class` kodu arka plan olan bir XAML sayfası tamamen geçerli olduğunu anlamda isteğe bağlıdır. Ancak, söz konusu özellik XAML kullanan Framework tarafından uygulanmış olarak derleme Eylemler ile etkileşim kurar. `x:Class` özelliği de çeşitli sınıflandırmalar XAML belirtilen içeriğin bir uygulama modeline sahip ve ilgili derleme eylemleri rolleri tarafından etkilenir. Olay işleme öznitelik değerleri ya da özel öğeleri tanımlayan sınıflar, arka plan kod sınıfı nerede başlatır, XAML bildiriyorsa, sağlamanız gereken `x:Class` yönerge başvurusu (veya [x: Subclass](x-subclass-directive.md)) için arka plan kod için uygun sınıf.  
  
 Değerini `x:Class` yönergesi, bir sınıfın ancak hiçbir derleme bilgisi olmadan tam olarak nitelenmiş adını belirten bir dize olmalıdır (eşdeğer <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Basit uygulamalar için arka plan kod de (sınıf düzeyinde kod tanımı başlar) bu şekilde yapılandırılırsa CLR ad alanı bilgilerini atlayabilirsiniz.  
  
 Sayfa veya uygulama tanımı için arka plan kod dosyası, derlenen bir uygulamayı oluşturan ve biçimlendirme derleme içeren projenin bir parçası olarak dahil olan bir kod dosyası içinde olması gerekir. CLR sınıflarını için adı kurallara uymalıdır. Daha fazla bilgi için [çerçeve tasarım yönergeleri](../../standard/design-guidelines/index.md). Varsayılan olarak, arka plan kod sınıfı olarak `public`; ancak kullanarak, farklı erişim düzeyinde tanımlayabilirsiniz [x: ClassModifier yönergesi](x-classmodifier-directive.md).  
  
 Bu yorumu `x:Class` özniteliğini uygular. yalnızca bir CLR tabanlı XAML uygulaması için özellikle .NET Framework XAML hizmetlerinde için. XAML işaretleme bağlama ve çalışma zamanı koduyla yedeklemeye farklı çözüm formül CLR'de dayalı olmayan ve .NET Framework XAML hizmetlerinde kullanmayan diğer XAML uygulamaları kullanabilir. Daha fazla genel yorumlar hakkında daha fazla bilgi için `x:Class`, bkz: [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Belirli bir düzeyde mimarisinin anlamını `x:Class` .NET Framework XAML hizmetlerinde içinde tanımlanmamış. .NET Framework XAML hizmetlerinde tarafından hangi XAML işaretleme ve kod yedekleme bağlı bir programlama modeli belirtmiyor olmasıdır. Ek kullanımlarını `x:Class` yönergesi XAML işaretleme ve kod arka plan CLR tabanlı bağlanma tanımlamak için programlama modelleri veya uygulama modellerini kullanan belirli çerçevelerine uygulanmış. Her bir çerçeve davranışı ya da yapı ortamına dahil belirli bileşenlerin bazılarını etkinleştirmek, kendi derleme eylemler olabilir. Bir çerçeve içinde yapı eylemleri de arka plan kod için kullanılan belirli CLR dile bağlı olarak değişebilir.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x: Class WPF programlama modeli  
 WPF uygulamaları ve WPF uygulama modeli `x:Class` XAML dosyasının kök ve derleniyor herhangi bir öğe için bir özniteliği olarak bildirilebilir (burada XAML dahil bir WPF uygulaması projesi ile `Page` derleme eylemi), veya < C4 > <xref:System.Windows.Application>  derlenmiş bir WPF uygulamasını Uygulama tanımındaki kök. Bildirme `x:Class` sayfa kök veya uygulama kökü dışında bir öğe üzerinde veya yapılmayan bir WPF XAML dosyası, altında bir derleme zamanı hatasına neden olur. [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] ve .NET Framework 3.5 WPF XAML derleyicisi. Diğer yönleri hakkında bilgi için `x:Class` WPF'de işleme bkz [arka plan kod ve WPF XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x: Class Windows Workflow Foundation için  
 Windows Workflow Foundation için `x:Class` tamamen XAML içinde oluşan özel bir etkinlik sınıfı adları veya arka plan kod ile bir etkinlik Tasarımcısı için XAML sayfanın kısmi sınıf adları.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Class` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için [XAML Namespace (x:) Dil özellikleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Subclass Yönergesi](x-subclass-directive.md)
- [WPF için XAML ve Özel Sınıflar](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier Yönergesi](x-classmodifier-directive.md)
- [WPF'den System.Xaml'e Geçirilen Türler](types-migrated-from-wpf-to-system-xaml.md)
