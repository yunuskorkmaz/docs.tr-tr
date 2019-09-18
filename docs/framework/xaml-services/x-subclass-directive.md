---
title: x:Subclass Yönergesi
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: f6f02998a7648693bd731d6b2afdfd4499abaa04
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053906"
---
# <a name="xsubclass-directive"></a>x:Subclass Yönergesi
Ayrıca sağlandığında XAML biçimlendirme derleme davranışını `x:Class` değiştirir. ' I temel alan `x:Class`kısmi bir sınıf oluşturmak yerine, belirtilen `x:Class` bir ara sınıf olarak oluşturulur ve ardından, sağlanmış türetilmiş sınıfınızın temel olması `x:Class`beklenir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`namespace`|İsteğe bağlı. İçeren `classname`bir clr ad alanı belirtir. Belirtilmişse, nokta (.) ve `classname`ayırır `namespace`. `namespace`|  
|`classname`|Gerekli. Yüklenen XAML 'yi ve bu XAML için arka plan kodunuzu bağlayan kısmi sınıfın CLR adını belirtir. Bkz. açıklamalar.|  
|`subclassNamespace`|İsteğe bağlı. , Her bir ad `namespace` alanı diğerini çözümleyebiliyorsanız, öğesinden farklı olabilir. İçeren `subclassName`bir clr ad alanı belirtir. Belirtilmişse, nokta (.) ve `subclassName`ayırır `subclassNamespace`. `subclassName`|  
|`subclassName`|Gerekli. Alt sınıfın CLR adını belirtir.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 [X:Class yönergesi](x-class-directive.md) aynı nesne üzerinde de sağlanmalıdır ve bu nesnenin xaml üretiminin kök öğesi olması gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Subclass`Kullanım öncelikle kısmi sınıf bildirimlerini desteklemeyen diller için tasarlanmıştır.  
  
 Olarak `x:Subclass` kullanılan sınıfı, iç içe geçmiş bir sınıf olamaz ve `x:Subclass` "bağımlılıklar" bölümünde açıklandığı gibi kök nesnesine başvurmalıdır.  
  
 Aksi takdirde, kavramsal anlamı `x:Subclass` .NET Framework xaml Hizmetleri uygulamasıyla tanımlanmamıştır. Bunun nedeni, XAML Hizmetleri davranışının XAML biçimlendirme ve yedekleme kodunun bağlı olduğu genel programlama modelini belirtmemesi .NET Framework. `x:Class` Ve ile`x:Subclass` ilgili başka kavramların uygulamaları, XAML biçimlendirme, derlenmiş biçimlendirme ve clr tabanlı arka plan kod bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçeveler tarafından gerçekleştirilir. Her çerçeve, bazı davranışlarının veya yapı ortamına dahil olması gereken belirli bileşenlerin bir kısmını etkinleştiren kendi derleme eylemlerine sahip olabilir. Bir çerçeve içinde, derleme eylemleri de arka plan kodu için kullanılan belirli CLR diline göre farklılık gösterebilir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `x:Subclass`, zaten sahip `x:Class`olan uygulama tanımındaki bir sayfa kökü <xref:System.Windows.Application> veya kök üzerinde olabilir. Bir `x:Subclass` sayfa veya uygulama kökü dışında herhangi bir öğe üzerinde bildirme ya da bunu yok `x:Class` olarak belirleme, derleme zamanı hatasına neden olur.  
  
 `x:Subclass` Senaryo için doğru şekilde çalışan türetilmiş sınıfların oluşturulması oldukça karmaşıktır. Ara dosyaları (. xaml dosya adlarını içeren adlarla biçimlendirme derlemesi tarafından, projenizin obj klasöründe oluşturulan. g dosyaları) incelemeniz gerekebilir. Bu ara dosyalar, derlenmiş uygulamadaki birleştirilmiş kısmi sınıflarda belirli programlama yapılarının kaynağını belirlemenize yardımcı olabilir.  
  
 Türetilmiş sınıftaki `internal override` olay işleyicileri, derleme sırasında ara sınıfta`Friend Overrides` oluşturulan işleyicilerle ilgili saplamaları geçersiz kılmak için (Microsoft Visual Basic) olmalıdır. Aksi halde, türetilmiş sınıf uygulamaları gizle (gölge) ara sınıf uygulaması ve ara sınıf işleyicileri çağrılmaz.  
  
 Hem hem de `x:Class` `x:Subclass`tanımladığınızda, tarafından `x:Class`başvurulan sınıf için herhangi bir uygulama sağlamanız gerekmez. Derleyicinin ara dosyalarda oluşturduğu sınıfa yönelik bir kılavuza sahip olması `x:Class` için yalnızca özniteliği aracılığıyla bir ad vermeniz gerekir (derleyici bu durumda varsayılan bir ad seçmez). `x:Class` Sınıfına bir uygulama verebilirsiniz; ancak, bu, hem hem `x:Subclass`de `x:Class` kullanımı için tipik bir senaryo değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [WPF için XAML ve Özel Sınıflar](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
