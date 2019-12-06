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
ms.openlocfilehash: d6baa6d8eb3a6d3520fb1549e2182f27ca52c36a
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837252"
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
|`namespace`|İsteğe bağlı. `classname`tarafından tanımlanan kısmi sınıfı içeren bir CLR ad alanı belirtir. `namespace` belirtilirse, nokta (.) `namespace` ve `classname`ayırır. Bkz. açıklamalar.|  
|`classname`|Gerekli. Yüklenen XAML 'yi ve bu XAML için arka plan kodunuzu bağlayan kısmi sınıfın CLR adını belirtir.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 `x:Class`, yalnızca bir XAML üretiminin kök öğesinde belirtilebilir. `x:Class`, XAML üretiminde üst öğesi olan herhangi bir nesne üzerinde geçersizdir. Daha fazla bilgi için bkz. [\[MS-XAML\] Bölüm 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Açıklamalar  
 `namespace` değeri, ilgili ad alanlarını, .NET Framework programlamada ortak bir teknik olan ad Hiyerarşileriyle düzenlemek için ek noktalar içerebilir. Yalnızca bir `x:Class` değerleri dizesindeki son nokta ayrı `namespace` olarak yorumlanır ve `x:Class` olarak kullanılan sınıf `classname.`, iç içe bir sınıf olamaz. İç içe geçmiş sınıflara izin veriliyorsa `x:Class` dizeleri için noktaların anlamını belirlemek belirsiz olduğundan iç içe sınıflara izin verilmez.  
  
 `x:Class`kullanan mevcut programlama modellerinde, `x:Class`, tamamen arka plan kodu olmayan bir XAML sayfasına sahip olmak için isteğe bağlıdır. Ancak, bu özellik XAML kullanan çerçeveler tarafından uygulanan yapı eylemleriyle etkileşime girer. `x:Class` özelliği, XAML tarafından belirtilen içeriklerin çeşitli sınıflandırmalarının bir uygulama modelinde ve ilgili derleme eylemlerindeki rollerle de etkilenir. XAML 'niz olay işleme öznitelik değerleri bildiriyorsa veya tanımlama sınıflarının arka plan kod sınıfında olduğu özel öğeleri örnekliyorsa, arka plan kodu için uygun sınıfa `x:Class` yönerge başvurusunu (veya [X:alt sınıfı](x-subclass-directive.md)) sağlamanız gerekir.  
  
 `x:Class` yönergesinin değeri, bir sınıfın tam adını belirten bir dize olmalıdır, ancak hiçbir derleme bilgisi (<xref:System.Type.FullName%2A?displayProperty=nameWithType>eşdeğerdir). Basit uygulamalar için, arka plan kod bu şekilde de (kod tanımı sınıf düzeyinde başlar) de yapılandırılmış olması halinde CLR ad alanı bilgilerini atlayabilirsiniz.  
  
 Bir sayfa veya uygulama tanımının arka plan kod dosyası, derlenmiş bir uygulama üreten ve biçimlendirme derlemesini içeren projenin bir parçası olarak dahil olan bir kod dosyası içinde olmalıdır. CLR sınıfları için ad kurallarını izlemeniz gerekir. Daha fazla bilgi için bkz. [Framework tasarım yönergeleri](../../standard/design-guidelines/index.md). Varsayılan olarak, arka plan kod sınıfı `public`olmalıdır; Ancak, [X:ClassModifier yönergesini](x-classmodifier-directive.md)kullanarak farklı bir erişim düzeyinde tanımlayabilirsiniz.  
  
 `x:Class` özniteliğinin bu yorumu yalnızca bir CLR tabanlı XAML uygulamasına uygulanır, özel XAML Hizmetleri .NET Framework. CLR tabanlı olmayan ve .NET Framework XAML Hizmetleri kullanmayan diğer XAML uygulamaları, XAML işaretlemesini bağlamak ve çalışma zamanı kodunu yedeklemek için farklı bir çözüm formülü kullanabilir. `x:Class`genel yorumlamalar hakkında daha fazla bilgi için bkz. [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 Belirli bir mimari düzeyinde `x:Class` anlamı .NET Framework XAML hizmetlerinde tanımsızdır. Bunun nedeni, XAML hizmetlerinin XAML biçimlendirme ve yedekleme kodunun bağlı olduğu programlama modelini belirtmemesi .NET Framework. `x:Class` yönergesinin ek kullanımları, XAML biçimlendirme ve CLR tabanlı arka plan kodu bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçeveler tarafından uygulanabilir. Her çerçeve, yapı ortamına dahil olması gereken bazı davranışı veya belirli bileşenleri etkinleştiren kendi derleme eylemlerine sahip olabilir. Bir çerçeve içinde, derleme eylemleri de arka plan kodu için kullanılan belirli CLR diline bağlı olarak farklılık gösterebilir.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>WPF programlama modelinde x:Class  
 WPF uygulamalarında ve WPF uygulama modelinde `x:Class`, XAML dosyasının kökü olan ve derlenebilecek (XAML 'in `Page` derleme eylemiyle bir WPF uygulama projesine dahil edildiği) veya derlenen bir WPF uygulamasının uygulama tanımındaki <xref:System.Windows.Application> kökünün bir özniteliği olarak bildirilemez. Sayfa kökü veya uygulama kökü dışında bir öğede veya derlenmeyen bir WPF XAML dosyasında `x:Class` bildirme, .NET Framework 3,0 ve .NET Framework 3,5 WPF XAML derleyicisi altında derleme zamanı hatasına neden olur. WPF 'de `x:Class` işlemenin diğer yönleri hakkında daha fazla bilgi için bkz. [WPF Içinde arka plan kod ve xaml](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>Windows Workflow Foundation için x:Class  
 Windows Workflow Foundation için `x:Class`, tamamen XAML 'de oluşturulan özel bir etkinliğin sınıfını adlandırır veya arka plan kodu içeren bir etkinlik tasarımcısının XAML sayfasının kısmi sınıfını adlandırır.  
  
## <a name="silverlight-usage-notes"></a>Silverlight Kullanım Notları  
 `x:Class` Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz. [xaml ad alanı (x:) Dil özellikleri (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Subclass Yönergesi](x-subclass-directive.md)
- [WPF için XAML ve Özel Sınıflar](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier Yönergesi](x-classmodifier-directive.md)
- [WPF'den System.Xaml'e Geçirilen Türler](types-migrated-from-wpf-to-system-xaml.md)
