---
title: "x:Class Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b894a56caa3644bae140e7ec37cf5b55ab093a59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xclass-directive"></a>x:Class Yönergesi
XAML biçimlendirme derleme biçimlendirmesi ve arka plan kodu arasında kısmi sınıflar katılmak için yapılandırır. Kod kısmi sınıfı ayrı kod dosyasında tanımlanan bir [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] dil biçimlendirme parçalı sınıf genellikle XAML derleme sırasında kod oluşturma tarafından oluşturulur ancak.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`namespace`|İsteğe bağlı. Belirten bir [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] tarafından tanımlanan parçalı sınıf içerir ad alanı `classname`. Varsa `namespace` belirtilirse, nokta (.) ayıran `namespace` ve `classname`. Açıklamalar bakın.|  
|`classname`|Gerekli. Belirtir [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] yüklenen XAML ve, arka plan kod bu XAML bağlayan parçalı sınıf adı.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 `x:Class`yalnızca bir XAML üretim kök öğesinde belirtilebilir. `x:Class`XAML üretimde üst öğesi olan herhangi bir nesne üzerinde geçerli değil. Daha fazla bilgi için bkz: [ \[MS XAML\] bölüm 4.3.1.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Açıklamalar  
 `namespace` Değeri, ilgili ad alanları, bir ortak bir .NET Framework programlama tekniktir adı Hiyerarşiler düzenlemek için ek noktalar içerebilir. Yalnızca son nokta bir dizesinde `x:Class` değerleri ayırmak için yorumlanır `namespace` ve `classname.` olarak kullanılan sınıf `x:Class` iç içe geçmiş sınıf olamaz. İç içe geçmiş sınıflar noktalar için anlamını belirlemek için verilmez `x:Class` dizeleri iç içe geçmiş sınıflar izin veriyorsa belirsiz.  
  
 Varolan programlama kullanmak modeli `x:Class`, `x:Class` hiçbir arka plan kodu içeren bir XAML sayfası sahip tamamen geçerli olduğunu anlamda isteğe bağlıdır. Ancak, bu yetenek XAML kullanan çerçeveleri tarafından uygulandığı gibi yapı eylemleri ile etkileşime girer. `x:Class`Yetenek XAML belirtilen içeriği çeşitli sınıflandırmaları bir uygulama modeli vardır ve ilgili eylemler yapı rolleri tarafından da etkiler. XAML olay işleme öznitelik değerleri veya özel öğeleri tanımlayan sınıflar arka plan kodu sınıfında nerede başlatır bildirirse, sağlamak zorunda `x:Class` yönerge başvurusu (veya [x: Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)) için arka plan kodu için uygun sınıf.  
  
 Değeri `x:Class` yönergesi bir sınıfın ancak derleme bilgi olmadan tam adı belirten bir dize olması gerekir (eşdeğer <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Basit uygulamalar için arka plan kodu aynı zamanda (sınıf düzeyinde kodu tanımı başlar) bu şekilde yapılandırılırsa CLR ad alanı bilgilerini atlayabilirsiniz.  
  
 Bir sayfa veya uygulama tanımı için arka plan kod dosyası, derlenen bir uygulama oluşturur ve biçimlendirme derleme ilgilidir projenin bir parçası olarak dahil olan bir kod dosya içinde olmalıdır. CLR sınıflarını adı kuralları izlemeniz gerekir. Daha fazla bilgi için bkz: [Framework tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md). Varsayılan olarak, arka plandaki kod sınıfı olmalıdır `public`; ancak, kullanarak onu farklı bir erişim düzeyinde tanımlayabilirsiniz [x: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
 Bu yorumu `x:Class` özniteliğini uygular. yalnızca bir CLR tabanlı XAML uygulama, özellikle de .NET Framework XAML Hizmetleri için. CLR üzerinde dayalı olmayan ve .NET Framework XAML hizmetlerinde kullanmayan diğer XAML uygulamaları XAML işaretleme birbirine bağlamak ve çalışma zamanı koduyla yedekleme için farklı bir çözünürlük formülü kullanabilirsiniz. Daha fazla genel yorumlarınızı hakkında daha fazla bilgi için `x:Class`, bkz: [ \[MS XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Belirli bir mimari, anlamını düzeyinde `x:Class` .NET Framework XAML hizmetlerinde tanımlanmamış. .NET Framework XAML Hizmetleri tarafından hangi XAML biçimlendirme ve kodun yedekleme bağlı programlama modeli belirtmediğinden budur. Ek kullanımlarını `x:Class` yönergesi programlama modelleri veya uygulama modelleri XAML biçimlendirme ve CLR tabanlı gerideki koddan nasıl bağlayacağınızı tanımlamak için kullanmak belirli çerçeveleri tarafından uygulanan. Her framework bazı davranışı veya yapı ortamında eklenmelidir belirli bileşenleri etkinleştirmek kendi yapı eylemleri olabilir. Bir çerçeve içinde yapı eylemleri de arka plan kod için kullanılan belirli CLR dil bağlı olarak değişebilir.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x: Class WPF programlama modeli  
 WPF uygulamaları ve WPF uygulama modeli `x:Class` XAML dosyasının kök ve derleniyor herhangi bir öğe için bir özniteliği olarak bildirilebilir (burada XAML dahil bir WPF uygulaması projesi ile `Page` derleme eylemi), veya < C4 > <xref:System.Windows.Application>  uygulama tanımında derlenmiş WPF uygulaması, kök. Bildirme `x:Class` sayfa kök veya uygulama kökü dışında bir öğe üzerinde veya değil derlenmiş bir WPF XAML dosyası, altında bir derleme zamanı hatasına neden oluyor [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] ve [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] WPF XAML derleyici. Diğer yönleri hakkında bilgi için `x:Class` WPF'de işleme, bkz: [arka plan kod ve WPF XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x: Class Windows Workflow Foundation için  
 Windows Workflow Foundation için `x:Class` tamamen XAML'de oluşan özel bir etkinlik sınıf adları veya arka plan kodu ile bir etkinlik Tasarımcısı için XAML sayfası kısmi sınıfı adları.  
  
## <a name="silverlight-usage-notes"></a>Silverlight kullanım notları  
 `x:Class`Silverlight için ayrı olarak belgelenmiştir. Daha fazla bilgi için bkz: [XAML Namespace (x:) Dil özellikleri (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x:Subclass Yönergesi](../../../docs/framework/xaml-services/x-subclass-directive.md)  
 [WPF için XAML ve Özel Sınıflar](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [x:ClassModifier Yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md)  
 [WPF'den System.Xaml'e Geçirilen Türler](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
