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
ms.openlocfilehash: f5640b348ccd68819052f58756489489371862d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186391"
---
# <a name="dependency-property-security"></a>Bağımlılık Özelliği Güvenliği
Bağımlılık özellikleri genellikle ortak özellikler olarak kabul edilmelidir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Özellik sisteminin doğası, bağımlılık özelliği değeri hakkında güvenlik garantileri yapma yeteneğini engeller.  

<a name="AccessSecurity"></a>
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Sarmalayıcılara ve Bağımlılık Özelliklerine Erişim ve Güvenlik  
 Genellikle, bağımlılık özellikleri, özelliği bir örnekten almayı veya ayarlamayı basitleştiren "sarmalayıcı" ortak dil çalışma zamanı (CLR) özellikleriyle birlikte uygulanır. Ama sarmalayıcılar gerçekten bağımlılık özellikleri ile <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> etkileşimde kullanılan temel ve statik çağrıları uygulamak sadece kolaylık yöntemleridir. Başka bir şekilde düşününce, özellikler, özel bir alan yerine bir bağımlılık özelliği tarafından desteklenen ortak dil çalışma zamanı (CLR) özellikleri olarak ortaya çıkar. Sarmalayıcılara uygulanan güvenlik mekanizmaları, özellik sistemi davranışı ve temel bağımlılık özelliğine erişime paralel değildir. Sarıcıya güvenlik talebi yerleştirmek yalnızca kolaylık yönteminin kullanımını engelleyecek, ancak <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>.'a yapılan aramaları engellemeyececektir. Benzer şekilde, korumalı veya özel erişim düzeyinin sarmalayıcılara yerleştirilmesi de etkili bir güvenlik sağlamaz.  
  
 Kendi bağımlılık özelliklerinizi yazıyorsanız, arayanların söz özelliğinin <xref:System.Windows.DependencyProperty> gerçek erişim düzeyi hakkında yanıltıcı bilgi almaması için (deposunun bağımlılık özelliği olarak uygulanması nedeniyle) sarmalayıcıları ve tanımlayıcı alanını ortak üye olarak bildirmelisiniz.  
  
 Özel bağımlılık özelliği için, mülkünüzü salt okunur bağımlılık özelliği olarak kaydedebilirsiniz ve bu <xref:System.Windows.DependencyPropertyKey> özellik, bu özellik için başvuruda olmayan herkes tarafından ayarlanan bir özelliği önlemek için etkili bir yol sağlar. Daha fazla bilgi için [bkz.](read-only-dependency-properties.md)  
  
> [!NOTE]
> Tanımlayıcı alanını <xref:System.Windows.DependencyProperty> özel olarak bildirmek yasak değildir ve özel bir sınıfın hemen açıkta kalan ad alanını azaltmaya yardımcı olmak için düşünülebilir, ancak böyle bir özellik, ortak dil çalışma zamanı (CLR) dil tanımlarının bir sonraki bölümde açıklanan nedenlerle bu erişim düzeyini tanımladığı şekilde "özel" olarak kabul edilmemelidir.  
  
<a name="PropertySystemExposure"></a>
## <a name="property-system-exposure-of-dependency-properties"></a>Bağımlılık Özelliklerinin Özellik Sistemi Pozlaması  
 Genel olarak yararlı değildir ve genel erişim düzeyi dışında <xref:System.Windows.DependencyProperty> herhangi bir erişim düzeyi olarak beyan etmek potansiyel olarak yanıltıcıdır. Bu erişim düzeyi ayarı yalnızca bir kişinin bildirim sınıfından örneğin referansını alabilmesini engeller. Ancak özellik sisteminin belirli bir özelliği bir <xref:System.Windows.DependencyProperty> sınıf veya türetilmiş sınıf örneğinde var olduğu gibi tanımlama aracı olarak döndürecek çeşitli yönleri vardır ve <xref:System.Windows.DependencyObject.SetValue%2A> bu tanımlayıcı, özgün statik tanımlayıcı halka açık olmayan olarak beyan edilebilse bile bir çağrıda yine de kullanılabilir. Ayrıca, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> sanal yöntemler değeri değiştirilen varolan bağımlılık özelliğinin bilgilerini alır. Buna ek <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> olarak, yöntem yerel olarak ayarlanmış bir değere sahip örneklerdeki herhangi bir özellik için tanımlayıcılar döndürür.  
  
### <a name="validation-and-security"></a>Doğrulama ve Güvenlik  
 Bir isteğin a'ya <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> uygulanması ve bir özelliğin ayarlanmasını engelleyen bir isteğ inemesi üzerine doğrulama hatası nın bekleyebilirsiniz yeterli bir güvenlik mekanizması değildir. Bu <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> arayanlar uygulama etki alanı içinde çalışıyorsa, kötü amaçlı arayanlar tarafından zorlanan ayar değeri geçersiz liği de bastırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
