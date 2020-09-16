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
ms.openlocfilehash: 8f7ca5fdb170411aba24d34b8bf4d6c4f5776cc4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555152"
---
# <a name="xclass-directive"></a>x:Class Yönergesi
Biçimlendirme ve arka plan kodu arasında kısmi sınıflara katılması için XAML biçimlendirme derlemesini yapılandırır. Kod kısmi sınıfı, ortak dil belirtimi (CLS) dilindeki ayrı bir kod dosyasında tanımlanır, ancak biçimlendirme kısmi sınıfı genellikle XAML derlemesi sırasında kod oluşturma tarafından oluşturulur.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`namespace`|İsteğe bağlı. Tarafından tanımlanan kısmi sınıfı içeren bir CLR ad alanı belirtir `classname` . `namespace`Belirtilmişse, nokta (.) `namespace` ve ayırır `classname` . Bkz. açıklamalar.|
|`classname`|Gereklidir. Yüklenen XAML 'yi ve bu XAML için arka plan kodunuzu bağlayan kısmi sınıfın CLR adını belirtir.|

## <a name="dependencies"></a>Bağımlılıklar

`x:Class` yalnızca bir XAML üretiminin kök öğesinde belirtilebilir. `x:Class` , XAML üretiminde üst öğesi olan herhangi bir nesne üzerinde geçersizdir. Daha fazla bilgi için bkz. [ \[ MS-xaml \] section 4.3.1.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Açıklamalar

`namespace`Bu değer, .NET programlamada yaygın bir tekniktir, ilgili ad alanlarını ad Hiyerarşileriyle düzenlemek için ek noktalar içerebilir. Yalnızca bir değer dizesindeki son nokta ayrı olarak `x:Class` yorumlanır `namespace` ve `classname.` olarak kullanılan sınıf, `x:Class` iç içe geçmiş bir sınıf olamaz. İç içe geçmiş sınıflara izin veriliyorsa dizeler için noktaların anlamını belirlemek belirsiz olduğu için iç içe geçmiş sınıflara izin verilmez `x:Class` .

Kullanan mevcut programlama modellerinde `x:Class` , `x:Class` arka plan kodu olmayan xaml sayfasına sahip olmak için tamamen geçerli olduğunu anlamak için isteğe bağlıdır. Ancak, bu özellik XAML kullanan çerçeveler tarafından uygulanan yapı eylemleriyle etkileşime girer. `x:Class` özelliği Ayrıca XAML tarafından belirtilen içeriğin çeşitli sınıflandırmalarının bir uygulama modelinde ve ilgili derleme eylemlerindeki rollerle etkilenir. XAML 'niz olay işleme öznitelik değerleri bildiriyorsa veya tanımlama sınıflarının arka plan kod sınıfında olduğu özel öğeleri örnekliyorsa, `x:Class` arka plan kodu için uygun sınıfa yönerge başvurusunu (veya [x:alt sınıfı](xsubclass-directive.md)) sağlamanız gerekir.

Yönergesinin değeri, `x:Class` bir sınıfın tam adını belirten bir dize olmalıdır, ancak hiçbir derleme bilgisi (ile eşdeğerdir <xref:System.Type.FullName%2A?displayProperty=nameWithType> ). Basit uygulamalar için, arka plan kod bu şekilde de (kod tanımı sınıf düzeyinde başlar) de yapılandırılmış olması halinde CLR ad alanı bilgilerini atlayabilirsiniz.

Bir sayfa veya uygulama tanımının arka plan kod dosyası, derlenmiş bir uygulama üreten ve biçimlendirme derlemesini içeren projenin bir parçası olarak dahil olan bir kod dosyası içinde olmalıdır. CLR sınıfları için ad kurallarını izlemeniz gerekir. Daha fazla bilgi için bkz. [Framework tasarım yönergeleri](../../../api/index.md). Varsayılan olarak, arka plan kod sınıfı olmalıdır `public` ; ancak, [X:ClassModifier yönergesini](xclassmodifier-directive.md)kullanarak farklı bir erişim düzeyinde tanımlayabilirsiniz.

Bu `x:Class` özniteliğin yorumu yalnızca .net xaml HIZMETLERINDE clr tabanlı xaml uygulamaları için geçerlidir. CLR tabanlı olmayan ve .NET XAML Hizmetleri kullanmayan diğer XAML uygulamaları, XAML işaretlemesini bağlamak ve çalışma zamanı kodunu yedeklemek için farklı bir çözüm formülü kullanabilir. Daha genel yorumlamalar hakkında daha fazla bilgi için `x:Class` bkz. [ \[ MS-xaml \] ](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

Belirli bir mimari düzeyinde, `x:Class` .NET XAML hizmetlerinde anlamı tanımsızdır. Bunun nedeni, .NET XAML Hizmetleri tarafından XAML işaretleme ve yedekleme kodunun bağlı olduğu programlama modelini belirtmemelidir. Yönergesinin ek kullanımları, `x:Class` XAML biçimlendirme ve clr tabanlı arka plan kodu bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçeveler tarafından uygulanabilir. Her çerçeve, yapı ortamına dahil olması gereken bazı davranışı veya belirli bileşenleri etkinleştiren kendi derleme eylemlerine sahip olabilir. Bir çerçeve içinde, derleme eylemleri de arka plan kodu için kullanılan belirli CLR diline bağlı olarak farklılık gösterebilir.

## <a name="xclass-in-the-wpf-programming-model"></a>WPF programlama modelinde x:Class

WPF uygulamalarında ve WPF uygulama modelinde, `x:Class` BIR xaml dosyasının kökü olan ve derlenebilecek (XAML, derleme eylemiyle BIR WPF uygulaması projesine dahil edilen `Page` ) veya <xref:System.Windows.Application> derlenmiş bir WPF uygulamasının uygulama tanımındaki kök için bir öznitelik olarak bildirilemez. `x:Class`Sayfa kökü veya uygulama kökü dışında bir öğe üzerinde veya derlenmemiş BIR WPF xaml dosyasında bildirilmek için, .NET Framework 3,0 ve .NET Framework 3,5 WPF XAML derleyicisi altında derleme zamanı hatasına neden olur. WPF 'de işlemenin diğer yönleri hakkında daha fazla bilgi için `x:Class` bkz. [WPF Içinde arka plan kod ve xaml](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf).

## <a name="xclass-for-windows-workflow-foundation"></a>Windows Workflow Foundation için x:Class
Windows Workflow Foundation için, `x:Class` tamamen XAML 'de oluşturulan özel bir etkinliğin sınıfını adlandırır veya arka plan kod içeren bir etkinlik TASARıMCıSıNıN xaml sayfasının kısmi sınıfını adlandırır.

## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları

`x:Class` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz. [xaml ad alanı (x:) Dil özellikleri (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Ayrıca bkz.

- [x:Subclass Yönergesi](xsubclass-directive.md)
- [WPF için XAML ve Özel Sınıflar](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [x:ClassModifier Yönergesi](xclassmodifier-directive.md)
- [WPF'den System.Xaml'e Geçirilen Türler](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
