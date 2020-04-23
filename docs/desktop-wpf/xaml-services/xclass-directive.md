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
ms.openlocfilehash: f589fa70c2ee1c56544fa0f0152990478aa3761f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072041"
---
# <a name="xclass-directive"></a>x:Class Yönergesi
XAML biçimlendirme derlemesini biçimlendirme ve kod arkası arasındaki kısmi sınıfları birleştirmek üzere yapılandırır. Kod kısmi sınıf Ortak Dil Belirtimi (CLS) dilinde ayrı bir kod dosyasında tanımlanır, biçimlendirme kısmi sınıf genellikle XAML derleme sırasında kod oluşturma tarafından oluşturulur.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`namespace`|İsteğe bağlı. `classname`Tarafından tanımlanan kısmi sınıfı içeren bir CLR ad alanı belirtir `namespace` Belirtilirse, nokta (.) ayrılır `namespace` `classname`ve . Bkz. Açıklamalar.|
|`classname`|Gereklidir. Yüklenen XAML'yi ve bu XAML için kod arkanızı bağlayan kısmi sınıfın CLR adını belirtir.|

## <a name="dependencies"></a>Bağımlılıklar

`x:Class`yalnızca bir XAML üretiminin kök öğesi üzerinde belirtilebilir. `x:Class`XAML üretiminde üst öğesi olan herhangi bir nesne için geçersizdir. Daha fazla bilgi için [ \[MS-XAML\] Bölüm 4.3.1.6'ya](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

## <a name="remarks"></a>Açıklamalar

Değer, `namespace` .NET programlamada yaygın bir teknik olan ad hiyerarşilerine ilgili ad alanlarını düzenlemek için ek nokta lar içerebilir. Yalnızca `x:Class` değerler dizisinin son nokta ayırmak `namespace` için yorumlanır ve `classname.` iç `x:Class` içe sınıf olamaz olarak kullanılan sınıf. İç içe sınıflara izin verilmediği için dizeleri için `x:Class` nokta anlamını belirleme belirsizdir.

Kullanan varolan programlama `x:Class`modellerinde, `x:Class` kod arkası olmayan bir XAML sayfasına sahip olmak tamamen geçerli olması anlamında isteğe bağlıdır. Ancak, bu özellik XAML kullanan çerçeveler tarafından uygulanan yapı eylemleri ile etkileşime girerek. `x:Class`yetenek, XAML tarafından belirtilen içeriğin çeşitli sınıflandırmalarının bir uygulama modelinde ve ilgili yapı eylemlerinde sahip olduğu rollerden de etkilenir. XAML'niz olay işleme öznitelik değerlerini beyan ederse veya tanımlayıcı sınıfların kod arkası sınıfında olduğu özel öğeleri `x:Class` anında kullanırsa, kod arkası için uygun sınıfa yönerge referansını (veya [x:Subclass)](xsubclass-directive.md)sağlamanız gerekir.

Yönerge değeri, `x:Class` bir sınıfın tam nitelikli adını belirten ancak herhangi bir derleme bilgisi olmayan <xref:System.Type.FullName%2A?displayProperty=nameWithType>(eşdeğeri) bir dize olmalıdır. Basit uygulamalar için, kod arkası da bu şekilde yapılandırılırsa (kod tanımı sınıf düzeyinde başlar) CLR ad alanı bilgilerini atlayabilirsiniz.

Bir sayfa veya uygulama tanımının kod arkası dosyası, derlenmiş bir uygulama üreten ve biçimlendirme derlemesini içeren projenin bir parçası olarak dahil edilmiş bir kod dosyası içinde olmalıdır. CLR sınıfları için ad kurallarına uymanız gerekir. Daha fazla bilgi için [Çerçeve Tasarım Yönergeleri'ne](../../../api/index.md)bakın. Varsayılan olarak, kod arkası sınıfı `public`olmalıdır; ancak [x:ClassModifier](xclassmodifier-directive.md)Yönergesi'ni kullanarak farklı bir erişim düzeyinde tanımlayabilirsiniz.

Özniteliğin `x:Class` bu yorumu yalnızca CLR tabanlı xaml uygulaması için, özellikle de .NET XAML Hizmetleri için geçerlidir. CLR'yi temel alamayan ve .NET XAML Hizmetleri kullanmayan diğer XAML uygulamaları, XAML biçimlendirmesini bağlamak ve çalışma zamanı kodunu desteklemek için farklı bir çözüm formülü kullanabilir. Daha fazla genel yorumları hakkında `x:Class`daha fazla bilgi için, [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

Belirli bir mimari düzeyinde,.NET `x:Class` XAML Hizmetleri'nde anlamı tanımsızdır. Bunun nedeni, .NET XAML Services'ın XAML biçimlendirme ve destek kodunun bağlı olduğu programlama modelini belirtmesidir. Yönergenin `x:Class` ek kullanımları, XAML biçimlendirmesi ve CLR tabanlı kod arkası bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçeveler tarafından uygulanabilir. Her çerçevenin, yapı ortamına dahil edilmesi gereken bazı davranışları veya belirli bileşenleri etkinleştiren kendi yapı eylemleri olabilir. Bir çerçeve içinde, yapı eylemleri de kod arkası için kullanılan belirli CLR dile bağlı olarak değişebilir.

## <a name="xclass-in-the-wpf-programming-model"></a>x:WPF Programlama Modelinde Sınıf

WPF uygulamalarında ve WPF uygulama `x:Class` modelinde, XAML dosyasının kökü olan ve derlenmektedir (XAML yapı eylemi ile `Page` bir WPF uygulama projesine dahil edilir) <xref:System.Windows.Application> veya derlenmiş bir WPF uygulamasının uygulama tanımındaki kök için herhangi bir öğe için öznitelik olarak bildirilebilir. `x:Class` Bir sayfa kökü veya uygulama kökü dışındaki bir öğede veya derlenmemiş bir WPF XAML dosyasında beyan etmek,.NET Framework 3.0 ve .NET Framework 3.5 WPF XAML derleyicisi altında derleme zamanı hatasına neden olur. WPF'de işlemenin `x:Class` diğer yönleri hakkında daha fazla bilgi için [WPF'de Kod Arkası ve XAML'ye](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)bakın.

## <a name="xclass-for-windows-workflow-foundation"></a>x:Windows İş Akışı Temeli için Sınıf
Windows İş Akışı `x:Class` Temeli için, tamamen XAML ile oluşturulmuş özel bir etkinliğin sınıfını adlandırır veya kod arkası olan bir etkinlik tasarımcısı için XAML sayfasının kısmi sınıfını adlandırır.

## <a name="silverlight-usage-notes"></a>Silverlight Kullanım Notları

`x:Class`Silverlight için ayrı ayrı belgelenmiştir. Daha fazla bilgi için [Bkz. XAML Namespace (x:) Dil Özellikleri (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Ayrıca bkz.

- [x:Subclass Yönergesi](xsubclass-directive.md)
- [WPF için XAML ve Özel Sınıflar](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier Yönergesi](xclassmodifier-directive.md)
- [WPF'den System.Xaml'e Geçirilen Türler](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
