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
ms.openlocfilehash: 8a14b00fe762d325028072cd0ea3eecf9b9206e3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423992"
---
# <a name="xstatic-markup-extension"></a>x:Static İşaretleme Uzantısı
Tanımlanan herhangi bir statik değere göre kod varlığa başvuran bir [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– uyumlu şekilde. Başvurulan statik özelliği, XAML içinde bir özelliğinin değeri sağlamak için kullanılabilir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
| | |  
|-|-|  
|`prefix`|İsteğe bağlı. Eşlenmiş, varsayılan olmayan bir XAML ad alanına başvuruda önek. `prefix` açıkça varsayılan XAML ad alanından gelen statik özellikler nadiren aldığından kullanımı gösterilmektedir. Açıklamalara bakın.|  
|`typeName`|Gerekli. İstenen statik üyeyi tanımlayan türü adı.|  
|`staticMemberName`|Gerekli. (Bir sabit, statik bir özellik, alan veya bir sabit listesi değeri) istenen statik değere üyesinin adı.|  
  
## <a name="remarks"></a>Açıklamalar  

Başvurulan kod varlık aşağıdakilerden biri olmalıdır:  
  
-   Bir sabiti  
-   Statik bir özellik  
-   Bir alan  
-   Bir sabit listesi değeri

XAML biçimlendirme veya bir XAML yükleme zamanı ayrıştırma özel durumu ise başka kod bir varlık, statik olmayan bir özellik gibi belirten bir derleme zamanı hatasına neden olur.  

Yapabileceğiniz `x:Static` başvurularını statik alanlar veya geçerli XAML belgesinin; varsayılan XAML ad alanı olmayan özellikler ancak bu bir ön ek eşleştirmesi gerektirir. XAML ad alanları, neredeyse her zaman XAML belgesinin kök öğesinde tanımlanır.  

Varsayılan XAML şema içeriği ile çalışırken statik özellikler için arama işlemleri, .NET Framework XAML hizmetlerinde ve XAML okuyucular ve XAML yazarları tarafından gerçekleştirilebilir. Bu XAML şema içeriği CLR yansıma, gerekli statik değerler için Nesne grafiği oluşturmayı sağlamak için kullanabilirsiniz. `typeName` Belirtmeniz aslında bir XAML türü adı, bir CLR türü adı değil, bunlar aslında aynı ada varsayılan XAML şema içeriği kullanırken ya da tüm var olan CLR tabanlı XAML-uygulama çerçeveleri kullanırken olmasına rağmen.  

Yaptığınız kullanırken dikkatli `x:Static` doğrudan bir özelliğin değerinin türü olmayan başvurular. XAML içinde dizisi, bir işaretleme uzantısı değerlerinden sağlanan işleme çağrılamadı ek değer dönüştürme. Bu doğru olsa bile, `x:Static` başvuru bir metin dizesi oluşturur ve bu belirli üye veya dönüş türünün hiçbir üyesi değerler için genellikle metin dizesine dayalı öznitelik değerleri için bir değer dönüştürme gerçekleşir.  

Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `x:Static` tanımlayıcı dizesi olarak atandığı <xref:System.Windows.Markup.StaticExtension.Member%2A> temel değer <xref:System.Windows.Markup.StaticExtension> uzantısı sınıfı.  

Teknik olarak mümkün olan diğer iki XAML kullanımları vardır. Ancak, bu kullanımları gereksiz yere ayrıntılıdır oldukları için daha az yaygın olan:  

1.  Nesne öğesi sözdizimi.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2.  Başlatma dizesi için açık bir üye özelliği ile söz dizimi özniteliği.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

.NET Framework XAML hizmetlerinde uygulamasında, bu işaretleme uzantısının işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.StaticExtension> sınıfı.  

`x:Static` bir işaretleme uzantısıdır. XAML kullanım içindeki tüm biçimlendirme uzantıları `{` ve `}` karakter kendi öznitelik sözdizimi kuralı tarafından bir XAML işlemcisinin bir işaretleme uzantısı bir değer belirtmeniz gerekir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [genel XAML işaretleme uzantılarına](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF programlama için kullandığınız varsayılan XAML ad alanı birçok yararlı statik özellikleri içermiyor ve kullanışlı statik özelliklerin çoğu sahip gerek kalmadan, kullanımı kolaylaştırmak tür dönüştürücüleri gibi desteği `{x:Static}` . Statik özellikler için aşağıdakilerden biri doğruysa bir XAML ad alanı için bir önek eşlemeniz gerekir:  
  
-   WPF içinde var, ancak WPF için varsayılan XAML ad alanı bir parçası olmayan bir türe başvuruyor ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). Bunu kullanmak için oldukça sık karşılaşılan bir senaryodur `x:Static`. Örneğin, kullanabilirsiniz bir `x:Static` bir XAML ad alanı eşlemesi ile başvuru <xref:System> statik özelliklerini başvurmak için CLR ad alanı ve mscorlib derlemesi <xref:System.Environment> sınıfı.  
  
-   Özel bir derlemeden bir tür başvuruyor.  
  
-   Varsayılan WPF XAML ad alanı bir parçası olarak eşlenmedi CLR ad alanı içinde türüdür, ancak bir WPF derlemede mevcut bir türe başvuruyor. CLR ad alanları için WPF eşleme varsayılan XAML ad alanına çeşitli WPF derlemeleri tanımlarında tarafından gerçekleştirilen (Bu kavramı hakkında daha fazla bilgi için bkz: [XAML ad alanları ve WPF XAML için Namespace eşlemesi](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). XAML için genellikle gibi amaçlanmayan çoğunlukla sınıf tanımları, CLR ad uzayı oluşturuluyorsa olmayan eşlenen bir CLR ad alanları varolabilir <xref:System.Windows.Threading>.  
  
 WPF için ön ekleri ve XAML ad alanları kullanma hakkında daha fazla bilgi için bkz. [XAML ad alanları ve WPF XAML Namespace eşleme](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x:Type İşaretleme Uzantısı](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [WPF'den System.Xaml'e Geçirilen Türler](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
