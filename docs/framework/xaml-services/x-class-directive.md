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
ms.openlocfilehash: 563802be655e0cb66c9a2735a64da9d7723c2a43
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401517"
---
# <a name="xclass-directive"></a>x:Class Yönergesi
Biçimlendirme ve arka plan kodu arasında kısmi sınıflara katılması için XAML biçimlendirme derlemesini yapılandırır. Kod kısmi sınıfı, ortak dil belirtimi (CLS) dilindeki ayrı bir kod dosyasında tanımlanır, ancak biçimlendirme kısmi sınıfı genellikle XAML derlemesi sırasında kod oluşturma tarafından oluşturulur.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`namespace`|İsteğe bağlı. Tarafından `classname`tanımlanan kısmi sınıfı içeren bir clr ad alanı belirtir. Belirtilmişse, nokta (.) ve `classname`ayırır `namespace`. `namespace` Bkz. açıklamalar.|  
|`classname`|Gerekli. Yüklenen XAML 'yi ve bu XAML için arka plan kodunuzu bağlayan kısmi sınıfın CLR adını belirtir.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 `x:Class`yalnızca bir XAML üretiminin kök öğesinde belirtilebilir. `x:Class`, XAML üretiminde üst öğesi olan herhangi bir nesne üzerinde geçersizdir. Daha fazla bilgi için bkz [ \[. MS-\] xaml Section 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Açıklamalar  
 Bu `namespace` değer, .NET Framework programlamada ortak bir tekniktir, ilgili ad alanlarını ad Hiyerarşileriyle düzenlemek için ek noktalar içerebilir. Yalnızca bir `x:Class` değer dizesindeki son nokta ayrı `namespace` olarak yorumlanır ve `classname.` olarak `x:Class` kullanılan sınıf, iç içe geçmiş bir sınıf olamaz. İç içe geçmiş sınıflara izin veriliyorsa dizeler için noktaların anlamını belirlemek belirsiz `x:Class` olduğu için iç içe geçmiş sınıflara izin verilmez.  
  
 Kullanan mevcut programlama modellerinde `x:Class`, `x:Class` arka plan kodu olmayan xaml sayfasına sahip olmak için tamamen geçerli olduğunu anlamak için isteğe bağlıdır. Ancak, bu özellik XAML kullanan çerçeveler tarafından uygulanan yapı eylemleriyle etkileşime girer. `x:Class`özelliği Ayrıca XAML tarafından belirtilen içeriğin çeşitli sınıflandırmalarının bir uygulama modelinde ve ilgili derleme eylemlerindeki rollerle etkilenir. XAML 'niz olay işleme öznitelik değerleri bildiriyorsa veya tanımlama sınıflarının arka plan kod sınıfında olduğu özel öğeleri örnekliyorsa, için uygun sınıfa `x:Class` yönerge başvurusunu (veya [x:alt sınıfı](x-subclass-directive.md)) sağlamanız gerekir arka plan kodu.  
  
 `x:Class` Yönergesinin değeri, bir sınıfın tam adını belirten bir dize olmalıdır, <xref:System.Type.FullName%2A?displayProperty=nameWithType>ancak hiçbir derleme bilgisi (ile eşdeğerdir). Basit uygulamalar için, arka plan kod bu şekilde de (kod tanımı sınıf düzeyinde başlar) de yapılandırılmış olması halinde CLR ad alanı bilgilerini atlayabilirsiniz.  
  
 Bir sayfa veya uygulama tanımının arka plan kod dosyası, derlenmiş bir uygulama üreten ve biçimlendirme derlemesini içeren projenin bir parçası olarak dahil olan bir kod dosyası içinde olmalıdır. CLR sınıfları için ad kurallarını izlemeniz gerekir. Daha fazla bilgi için bkz. [Framework tasarım yönergeleri](../../standard/design-guidelines/index.md). Varsayılan olarak, arka plan kod sınıfı `public`olmalıdır; ancak, [x:ClassModifier yönergesini](x-classmodifier-directive.md)kullanarak farklı bir erişim düzeyinde tanımlayabilirsiniz.  
  
 Bu `x:Class` özniteliğin yorumu yalnızca CLR tabanlı xaml uygulamasına uygulanır, özellikle .NET Framework xaml Hizmetleri için geçerlidir. CLR tabanlı olmayan ve .NET Framework XAML Hizmetleri kullanmayan diğer XAML uygulamaları, XAML işaretlemesini bağlamak ve çalışma zamanı kodunu yedeklemek için farklı bir çözüm formülü kullanabilir. Daha genel yorumlamalar `x:Class`hakkında daha fazla bilgi için bkz [ \[. ms-xaml\]](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Belirli bir mimari düzeyinde, ' nin `x:Class` anlamı .NET Framework XAML hizmetlerinde tanımsızdır. Bunun nedeni, XAML hizmetlerinin XAML biçimlendirme ve yedekleme kodunun bağlı olduğu programlama modelini belirtmemesi .NET Framework. Yönergesinin ek kullanımları, `x:Class` XAML biçimlendirme ve clr tabanlı arka plan kodu bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçeveler tarafından uygulanabilir. Her çerçeve, yapı ortamına dahil olması gereken bazı davranışı veya belirli bileşenleri etkinleştiren kendi derleme eylemlerine sahip olabilir. Bir çerçeve içinde, derleme eylemleri de arka plan kodu için kullanılan belirli CLR diline bağlı olarak farklılık gösterebilir.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>WPF programlama modelinde x:Class  
 WPF uygulamalarında ve WPF uygulama modelinde, `x:Class` bir xaml dosyasının kökü olan ve Derlenmekte olan (XAML, `Page` derleme eylemiyle bir WPF uygulama projesine dahil edilen) veya < <xref:System.Windows.Application> DERLENMIŞ bir WPF uygulamasının uygulama tanımında C4 > root. Sayfa kökü veya uygulama kökü dışında bir öğe üzerindeveyaderlenmemişbirWPFxamldosyasındabildirilmekiçin,.NETFramework3,0ve.NETFramework3,5WPFXAMLderleyicisialtındaderlemezamanıhatasınanedenolur.`x:Class` WPF 'de `x:Class` işlemenin diğer yönleri hakkında daha fazla bilgi için bkz. [WPF içinde arka plan kod ve xaml](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>Windows Workflow Foundation için x:Class  
 Windows Workflow Foundation için, `x:Class` tamamen XAML 'de oluşturulan özel bir etkinliğin sınıfını adlandırır veya arka plan kod içeren bir etkinlik tasarımcısının xaml sayfasının kısmi sınıfını adlandırır.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Class`Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz [. xaml ad alanı (x:) Dil özellikleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Subclass Yönergesi](x-subclass-directive.md)
- [WPF için XAML ve Özel Sınıflar](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier Yönergesi](x-classmodifier-directive.md)
- [WPF'den System.Xaml'e Geçirilen Türler](types-migrated-from-wpf-to-system-xaml.md)
