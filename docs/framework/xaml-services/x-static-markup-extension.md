---
title: x:Static İşaretleme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 980bf6a1bdb19afd5c8d3c798d31037ab8cd7086
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xstatic-markup-extension"></a>x:Static İşaretleme Uzantısı
Tanımlanan herhangi bir statik değer tarafından kod varlığa başvuruda bulunan bir [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– uyumlu yolu. Başvurulan statik özellik XAML'de özelliğinin değeri sağlamak için kullanılabilir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`prefix`|İsteğe bağlı. Eşlenen, varsayılan olmayan XAML ad alanına başvuruyor öneki. `prefix` Varsayılan XAML ad alanından gelen statik özellikler nadiren aldığından açıkça kullanımı gösterilmiştir. Açıklamalar bakın.|  
|`typeName`|Gerekli. İstenen statik üyenin tanımlayan tür adı.|  
|`staticMemberName`|Gerekli. İstenen statik değere üyesi (sabit bir değer, bir statik özellik, bir alan veya bir numaralandırma değeri) adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Başvurulan kod varlık aşağıdakilerden biri olması gerekir:  
  
-   Bir sabiti  
  
-   Bir statik özellik  
  
-   Bir alan  
  
-   Bir numaralandırma değeri  
  
 XAML biçimlendirme derlenirken biçimlendirme veya bir XAML yükleme zamanı ayrıştırma özel durumu ise herhangi diğer kod varlığı, statik olmayan bir özellik gibi belirten bir derleme zamanı hatasına neden olur.  
  
 Yapabileceğiniz `x:Static` statik alanları veya geçerli XAML belgenin; varsayılan XAML ad uzayı bulunmayan özellikleri başvurular ancak, bu önek eşleştirme gerektirir. XAML ad uzayları neredeyse her zaman XAML belgenin kök öğesinin tanımlanır.  
  
 Varsayılan XAML şema içeriği ile çalışırken statik özellikleri için arama işlemleri .NET Framework XAML hizmetlerinde ve XAML okuyucuları ve XAML yazarlar tarafından gerçekleştirilebilir. Bu XAML şema içeriği CLR yansıma Nesne grafiği oluşturması için gerekli statik değerlerini sağlamak için kullanabilirsiniz. `typeName` Belirttiğiniz gerçekte bir XAML türü adı, bir CLR türü adı değil, bunlar varsayılan XAML şema içeriği kullanırken ya da tüm mevcut CLR tabanlı XAML-uygulama çerçeveleri kullanırken temelde aynı adı olmasına rağmen.  
  
 Yaptığınızda dikkatli `x:Static` doğrudan bir özelliğin değerini türünde olmayan başvuruları. XAML biçimlendirme uzantısı değerlerinden sağlanan sırası işleme çağrılamadı ek değeri dönüştürme. Bu durum geçerlidir olsa bile, `x:Static` başvuru bir metin dizesi oluşturur ve bu belirli üye veya herhangi bir üye değeri dönüş türü değeri dönüştürme metin dizesine genellikle dayalı öznitelik değerleri için oluşur.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `x:Static` kimlik dizesi olarak atandığı <xref:System.Windows.Markup.StaticExtension.Member%2A> temel değer <xref:System.Windows.Markup.StaticExtension> uzantısı sınıfı.  
  
 Teknik olarak mümkün başka iki XAML kullanımı vardır. Ancak, gereksiz yere ayrıntılı olduğundan bu kullanımları daha az yaygın olan:  
  
 **Nesne öğesi sözdizimi:** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName` `" .../>`  
  
 **Başlatma dizesinin açık üye özelliğiyle öznitelik sözdizimi:** `<` `object` `` `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName` `}" .../>`  
  
 .NET Framework XAML hizmetlerinde uygulamasında bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.StaticExtension> sınıfı.  
  
 `x:Static` bir biçimlendirme uzantısıdır. XAML Kullanımdaki tüm biçimlendirme uzantıları `{` ve `}` olarak XAML işlemci tanıdığı biçimlendirme uzantısı bir değer girmelisiniz kuralı kendi öznitelik sözdiziminde karakterler. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [işaretleme uzantılarına genel bakış XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF programlama için kullandığınız varsayılan XAML ad uzayı pek çok yararlı statik özellikleri içermiyor ve yararlı statik özelliklerinin çoğu sahip gerek kalmadan kullanım kolaylaştırmak tür dönüştürücüleri gibi destek `{x:Static}` . Statik özellikler için aşağıdakilerden biri doğruysa bir XAML ad alanı için bir önek eşlemeniz gerekir:  
  
-   WPF içinde var, ancak WPF için varsayılan XAML ad uzayı parçası olmayan bir tür başvurma ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). Kullanmak için oldukça yaygın bir senaryo budur `x:Static`. Örneğin, kullanabileceğinize bir `x:Static` başvuru için XAML ad alanı eşlemesi ile <xref:System> statik özelliklerini başvurmak için CLR ad alanı ve mscorlib derlemesi <xref:System.Environment> sınıfı.  
  
-   Bir tür özel derlemesinden başvuruda bulunuyor.  
  
-   Ancak bu tür WPF varsayılan XAML ad uzayı parçası olarak eşlenmedi CLR ad alanı içinde değil bir WPF derlemesinde varolan bir türü başvuruda bulunuyor. Eşleme CLR ad alanlarının varsayılan XAML ad uzayı WPF için çeşitli WPF derlemelerde tanımları tarafından gerçekleştirilen (bu kavram hakkında daha fazla bilgi için bkz: [XAML ad uzayları ve WPF XAML için Namespace eşleme](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). CLR ad alanları olmayan eşlenen çoğunlukla XAML için genellikle gibi amaçlanmamıştır sınıf tanımları CLR ad oluşuyorsa varolabilir <xref:System.Windows.Threading>.  
  
 Önekleri ve XAML ad uzayları WPF için nasıl kullanılacağı hakkında daha fazla bilgi için bkz: [XAML ad uzayları ve WPF XAML Namespace eşleme](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x:Type İşaretleme Uzantısı](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [WPF'den System.Xaml'e Geçirilen Türler](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
