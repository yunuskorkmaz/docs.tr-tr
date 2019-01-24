---
title: x:Shared Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: 1c718522a20fb2047ebf500adbf4044265e3af3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542268"
---
# <a name="xshared-attribute"></a>x:Shared Özniteliği
Ayarlandığında `false`, böylece tüm istekler için aynı örneğini paylaşmak yerine, her istek için yeni bir örneği oluşturma isteği öznitelikli kaynağı için WPF kaynak alma davranışını değiştirir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Shared` XAML dil XAML ad alanına eşlenen ve geçerli bir XAML dil öğesi .NET Framework XAML hizmetlerinde ve kendi XAML okuyucular tarafından değerlendirilmiştir. Ancak, belirtilen yeteneklerini `x:Shared` yalnızca ve WPF XAML ayrıştırıcı WPF uygulamaları için uygundur. WPF, `x:Shared` WPF içinde var olan bir nesneye uygulanan yalnızca bir özniteliği olarak kullanışlıdır <xref:System.Windows.ResourceDictionary>. Diğer kullanımları ayrıştırma özel durumlar veya diğer hatalar oluşturması beklenmiyor ancak bunlar herhangi bir etkisi yoktur.  
  
 Anlamını `x:Shared` XAML dil belirtimi belirtilmedi. .NET Framework XAML hizmetlerinde yapı olanlar gibi diğer XAML uygulamaları kaynak paylaşma desteği sağlamaz. Bu tür XAML uygulamaları da kullanılan destekleyici Framework benzer bir davranış sağlayabilir `x:Shared` değerleri.  
  
 WPF, varsayılan `x:Shared` kaynaklar için koşul `true`. Bu durum, belirtilen kaynak isteği gönderirken her zaman aynı örneğini döndürür anlamına gelir.  
  
 Bir kaynağı API gibi döndürülen bir nesne değiştirme <xref:System.Windows.FrameworkElement.FindResource%2A>, veya bir nesne doğrudan içinde değiştirerek bir <xref:System.Windows.ResourceDictionary>, özgün kaynak değiştirir. Referansları bu kaynağa dinamik kaynak başvurularını varsa, bu kaynağa tüketicilerinin değiştirilen kaynak alın.  
  
 Kaynak başvurularını statik kaynak başvurularını olsaydı, sonra kaynak değişikliklerini [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ilgisiz işleme süresi. Statik ve dinamik kaynak başvuruları hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Açıkça belirtilmesi `x:Shared="true"` , zaten varsayılan olduğundan nadiren, gerçekleştirilir. Doğrudan kod için eşdeğer `x:Shared` WPF içinde nesne modeli; yalnızca bir XAML kullanımı belirtilebilir ve varsayılan WPF davranış veya yükleme yolundaki Ara bir XAML düğüm akış kullanarak .NET Framework XAML Se işlediğinde işlenmesi gerekir rvices ve kendi XAML okuyucular.  
  
 Bir senaryo için `x:Shared="false"` tanımlarsınız, bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş bir sınıf kaynak olarak ve size bir içerik modeline öğesi kaynak tanıtır. `x:Shared="false"` birden çok kez aynı koleksiyonda tanıtılmak üzere bir öğe kaynak sağlar (gibi bir <xref:System.Windows.Controls.UIElementCollection>). Olmadan `x:Shared="false"` koleksiyonun içeriğini benzersizlik zorladığından bu geçersizdir. Ancak, `x:Shared="false"` davranışı aynı örneğini döndürmek yerine kaynak aynı başka bir örneğini oluşturur.  
  
 Başka bir senaryo için `x:Shared="false"` kullanıyorsanız olduğu bir <xref:System.Windows.Freezable> animasyon değerlerini ancak kaynak animasyon başına temelinde değiştirmek istediğiniz kaynak.  
  
 Dize işleme `false` büyük/küçük harfe duyarlı değildir.  
  
 WPF, `x:Shared` yalnızca aşağıdaki koşullarda geçerli olur:  
  
-   <xref:System.Windows.ResourceDictionary> İle öğeleri içeren `x:Shared` derlenmelidir. <xref:System.Windows.ResourceDictionary> Gevşek XAML içinde olamaz ya da temaları için kullanılır.  
  
-   <xref:System.Windows.ResourceDictionary> Öğelerini içeren başka içinde iç içe olmamalıdır değil <xref:System.Windows.ResourceDictionary>. Örneğin, kullanamazsınız `x:Shared` öğeleri için bir <xref:System.Windows.ResourceDictionary> içinde olan bir <xref:System.Windows.Style> zaten olan bir <xref:System.Windows.ResourceDictionary> öğesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.ResourceDictionary>
- [XAML Kaynakları](../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Temel Öğeler](../../../docs/framework/wpf/advanced/base-elements.md)
