---
title: Bağımlılık Özelliği Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: d9dd9306980b80f7845c10e8c0ccb59f29821245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940835"
---
# <a name="dependency-property-security"></a>Bağımlılık Özelliği Güvenliği
Bağımlılık özellikleri genellikle genel özellikler olarak düşünülmelidir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Özellik sisteminin doğası, bağımlılık özelliği değeri hakkında güvenlik garantisi yapma imkanını önler.  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Sarmalayıcılar ve bağımlılık özelliklerinin erişimi ve güvenliği  
 Genellikle bağımlılık özellikleri, özelliği bir örnekten almayı veya ayarlamayı kolaylaştıran "sarmalayıcı" ortak dil çalışma zamanı (CLR) özellikleriyle birlikte uygulanır. Ancak sarmalayıcılar, bağımlılık özellikleriyle etkileşim kurarken kullanılan temel <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> statik çağrıları uygulayan oldukça kolay yöntemlerdir. Bunu başka bir şekilde düşünürken özellikler, özel bir alan yerine bir bağımlılık özelliği tarafından desteklenen ortak dil çalışma zamanı (CLR) özellikleri olarak gösterilir. Sarmalayıcılarla uygulanan güvenlik mekanizmaları, temel bağımlılık özelliğine özellik sistemi davranışını ve erişimini paralel değildir. Sarmalayıcı üzerine bir güvenlik talebi koymak yalnızca kolaylık yönteminin kullanımını engeller, ancak <xref:System.Windows.DependencyObject.GetValue%2A> veya <xref:System.Windows.DependencyObject.SetValue%2A>çağrılarını engellemez. Benzer şekilde, sarmalayıcıda korumalı veya özel erişim düzeyinin yerleştirilmesi, etkin bir güvenlik sağlamaz.  
  
 Kendi bağımlılık özelliklerinizi yazıyorsanız, çağıranların, bu özelliğin gerçek erişim düzeyiyle ilgili bir yanılma bilgisi alması için sarmalayıcıları ve <xref:System.Windows.DependencyProperty> tanımlayıcı alanını Genel Üyeler olarak bildirmeniz gerekir. bağımlılık özelliği olarak uygulandı).  
  
 Özel bir bağımlılık özelliği için, özelliği salt okunurdur ve bu özellik <xref:System.Windows.DependencyPropertyKey> için bir başvuru içermeyen herkes tarafından ayarlanmış bir özelliği engellemek için etkili bir yöntem sağlar. Daha fazla bilgi için bkz. [salt okuma bağımlılığı özellikleri](read-only-dependency-properties.md).  
  
> [!NOTE]
> Bir <xref:System.Windows.DependencyProperty> tanımlayıcı alanın özel olarak bildirilmesi yasak değildir ve bir özel sınıfın hemen sunulma ad alanını azaltmaya yardımcı olmak için çalıp kullanılabilir, ancak bu tür bir özelliğin ortak dille aynı anlamda "özel" olarak değerlendirilmemesi gerekir çalışma zamanı (CLR) dil tanımları, sonraki bölümde açıklanan nedenlerle bu erişim düzeyini tanımlar.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Bağımlılık özelliklerinin özellik sistemi pozlaması  
 Genellikle yararlı değildir ve ortak dışında bir <xref:System.Windows.DependencyProperty> erişim düzeyi bildirmek için potansiyel olarak yanıltıcı olur. Bu erişim düzeyi ayarı yalnızca birisinin bildirim sınıfından örneğe başvuru almasını engeller. Ancak, belirli bir özelliği bir sınıf örneği veya türetilmiş sınıf örneği üzerinde <xref:System.Windows.DependencyProperty> olduğu gibi tanımlayan bir yöntem olarak, özellik sisteminin birkaç yönü vardır ve bu tanımlayıcı yine de bir <xref:System.Windows.DependencyObject.SetValue%2A> çağrıda kullanılabilir özgün statik tanımlayıcı, ortak olarak bildirilirse. Ayrıca, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> sanal yöntemler değeri değiştiren mevcut herhangi bir bağımlılık özelliği hakkında bilgi alır. Ayrıca, <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> yöntemi yerel olarak ayarlanmış bir değere sahip örnekleri üzerinde herhangi bir özellik için tanımlayıcılar döndürür.  
  
### <a name="validation-and-security"></a>Doğrulama ve güvenlik  
 Bir özelliğin ayarlanmasının önleneceği bir istek hata üzerinde bir <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> istek uygulama ve doğrulama hatası bekleniyor, yeterli bir güvenlik mekanizması değildir. İle uygulama etki alanında bu çağıranlar <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> çalışıyorsa, ' ın aracılığıyla zorunlu kılınan küme değeri, kötü amaçlı arayanlar tarafından da gizlenebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
