---
title: "x:Shared Özniteliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d6a9333b2267e82fc25b2a0ec4bf5dd14f644078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xshared-attribute"></a>x:Shared Özniteliği
Ayarlandığında `false`, böylece istekleri öznitelikli kaynak için tüm istekler için aynı örneği paylaşmak yerine her istek için yeni bir örnek oluşturmak WPF kaynak alma davranışını değiştirir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Shared`XAML dil XAML ad alanına eşlenir ve geçerli bir XAML dil öğesi .NET Framework XAML hizmetlerinde ve XAML okuyucuları tarafından tanınmıyor. Ancak, belirtilen özellikleri `x:Shared` yalnızca WPF XAML ayrıştırıcısı ve WPF uygulamalar için uygundur. WPF, `x:Shared` WPF içinde bulunan bir nesnenin uygulandığında yalnızca bir özniteliği olarak yararlıdır <xref:System.Windows.ResourceDictionary>. Diğer kullanımlar ayrıştırma özel durumları veya diğer hatalar throw değil, ancak herhangi bir etkisi yoktur.  
  
 Anlamını `x:Shared` XAML dil belirtimi belirtilmedi. .NET Framework XAML hizmetlerinde yapı olanlar gibi diğer XAML uygulamaları kaynak paylaşma destek sağlamaz. Bu tür XAML uygulamaları da kullanılan destekleyen Framework'te benzer Davranış sağlayabilir `x:Shared` değerleri.  
  
 WPF'de varsayılan `x:Shared` kaynaklar için koşul `true`. Bu koşul herhangi belirli kaynak isteği her zaman aynı örneğini döndürür anlamına gelir.  
  
 Bir kaynak API gibi döndürülen nesneyi değiştirme <xref:System.Windows.FrameworkElement.FindResource%2A>, veya bir nesne doğrudan içinde değiştirerek bir <xref:System.Windows.ResourceDictionary>, özgün kaynak değiştirir. Bu kaynak başvurular dinamik kaynak başvuruları olsaydı, o kaynak tüketicileri değiştirilen kaynak alın.  
  
 Kaynak başvuruları statik kaynak başvuruları olsaydı, sonra kaynak değişikliklerini [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işleme süresi ilgisiz. Statik dinamik kaynak başvuruları karşılaştırması hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Açıkça belirtilmesi `x:Shared="true"` , varsayılan zaten olduğundan nadiren, yapılır. Doğrudan kod için eşdeğer `x:Shared` WPF içinde nesne modeli; yalnızca bir XAML kullanımı belirtilebilir ve varsayılan WPF davranışı tarafından veya bir ara XAML düğümü akışı yükleme yolunda .NET Framework XAML Se kullanarak işlenen işlenmesi gerekir rvices ve XAML okuyucuları.  
  
 Bir senaryo için `x:Shared="false"` tanımlarsanız, olan bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş sınıf kaynak olarak ve ardından içerik modeline öğesi kaynak tanıtır. `x:Shared="false"`birden çok kez aynı koleksiyonunda sunulması öğesi kaynak sağlar (gibi bir <xref:System.Windows.Controls.UIElementCollection>). Olmadan `x:Shared="false"` koleksiyonu içeriğinin benzersizliğini zorladığından bu geçersizdir. Ancak, `x:Shared="false"` davranışı aynı örneğini döndüren yerine kaynak aynı başka bir örneğini oluşturur.  
  
 Başka bir senaryo için `x:Shared="false"` kullanıyorsanız olan bir <xref:System.Windows.Freezable> kaynak animasyon değerlerini ancak animasyon başına temelinde kaynak değiştirmek istiyorum.  
  
 Dize işlenmesini `false` büyük küçük harfe duyarlı değildir.  
  
 WPF, `x:Shared` yalnızca aşağıdaki koşullar altında geçerlidir:  
  
-   <xref:System.Windows.ResourceDictionary> Öğeleri içeren `x:Shared` derlenmiş olmalıdır. <xref:System.Windows.ResourceDictionary> Temaları kullanılan veya gevşek XAML içinde olamaz.  
  
-   <xref:System.Windows.ResourceDictionary> Öğeleri içeren içinde başka bir iç içe gerekir değil <xref:System.Windows.ResourceDictionary>. Örneğin, kullanamazsınız `x:Shared` öğe için bir <xref:System.Windows.ResourceDictionary> içinde olan bir <xref:System.Windows.Style> zaten olan bir <xref:System.Windows.ResourceDictionary> öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.ResourceDictionary>  
 [XAML kaynakları](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Temel öğeler](../../../docs/framework/wpf/advanced/base-elements.md)
