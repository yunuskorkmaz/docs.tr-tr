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
ms.openlocfilehash: d51f8f5fd704b0c95b8e6f841b9b0ff8567899cb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364820"
---
# <a name="dependency-property-security"></a>Bağımlılık Özelliği Güvenliği
Bağımlılık özellikleri genellikle ortak özellikleri olarak düşünülmelidir. Doğasını [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi bir bağımlılık özelliği değer hakkında güvenlik Güvenceleri yapma yeteneğini engeller.  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Erişim ve güvenlik sarmalayıcılar ve bağımlılık özellikleri  
 Bağımlılık özellikleri "sarmalayıcı" ile birlikte bu genellikle, uygulanan [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] bir örnekten özelliğini ayarlamanın ya kolaylaştıran özellikler. Ancak sarmalayıcılar temel alınan uygulayan yalnızca gerçekten kullanışlı yöntemler <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> bağımlılık özellikleri ile etkileşim kurulurken kullanılan statik çağrıları. Bunu, başka bir yolla düşünürsek, özellikleri olarak sunulan [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] bağımlılık özelliği yerine özel bir alan tarafından yedeklenmek için özellikleri. Sarmalayıcıları için uygulanan güvenlik mekanizmaları özellik sistemi davranışı ve temel alınan bağımlılık özelliğinin erişim paralel değil. Sarmalayıcı üzerinde bir güvenlik talebi yerleştirmeyi yalnızca kolaylık yöntemi kullanımını engeller ancak çağrıları önlemez <xref:System.Windows.DependencyObject.GetValue%2A> veya <xref:System.Windows.DependencyObject.SetValue%2A>. Benzer şekilde, yerleştirme korumalı veya özel erişim düzeyi sarmalayıcıları üzerinde herhangi bir geçerli güvenlik sağlamaz.  
  
 Kendi bağımlılık özellikleri yazıyorsanız sarmalayıcıları bildirmelidir ve <xref:System.Windows.DependencyProperty> çağıranlar bu özelliği doğru erişim düzeyini hakkında bilgi (kendi deposu olması nedeniyle çağıranlar, genel üye olarak tanımlayıcı alanı bağımlılık özelliği olarak uygulanır).  
  
 Özel bağımlılık özelliği için salt okunur bağımlılık özelliği olarak özelliğinizi kaydedebilirsiniz ve bu başvuru bulundurmayan herkes tarafından ayarlanan bir özelliği önleme etkili bir yol sağlar <xref:System.Windows.DependencyPropertyKey> bu özellik için. Daha fazla bilgi için [salt okunur bağımlılık özellikleri](read-only-dependency-properties.md).  
  
> [!NOTE]
>  Bildirme bir <xref:System.Windows.DependencyProperty> tanımlayıcı alan özel olmayan Yasak ve hemen sunulan özel bir sınıf ad alanı azaltmak için kısıtlanmamışsa kullanılabilir, ancak böyle bir özellik "olarak aynı anlamda'nın private" değerlendirilmemelidir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] dil tanımları, sonraki bölümde açıklanan nedenlerle bu erişim düzeyini tanımlayın.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Özellik sistem etkilenmesi bağımlılık özellikleri  
 Genel olarak kullanışlı değildir ve bildirmek için büyük olasılıkla yanıltıcıdır, bir <xref:System.Windows.DependencyProperty> genel dışındaki herhangi bir erişim düzeyi. Bu erişim düzeyi ayarı yalnızca birisi bildiren sınıftan örneğe bir başvuru almak engeller. Çeşitli yönlerini döndürür özellik sistemi vardır, ancak bir <xref:System.Windows.DependencyProperty> belirli bir özellik, bir sınıfın bir örneği veya türetilmiş sınıf örneği üzerinde var olduğundan ve bu tanımlayıcıyı içinde hala kullanılabilir olarak tanımlama olarak bir <xref:System.Windows.DependencyObject.SetValue%2A> bile çağırın özgün statik tanımlayıcısı ortak değil bildirilirse. Ayrıca, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> sanal yöntemler değeri herhangi bir mevcut bağımlılık özelliği bilgileri alır. Ayrıca, <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> yöntemi örneği yerel olarak ayarlanmış herhangi bir özellik için bir tanımlayıcı döndürür değeri.  
  
### <a name="validation-and-security"></a>Doğrulama ve güvenlik  
 İsteğe bağlı olarak uygulayarak bir <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> ve özellik ayarlanmasını önlemek için bir istek başarısız doğrulama hatası bekleniyor yeterli güvenlik mekanizması değil. Set-değer geçersiz kılma zorlanan aracılığıyla <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> bu Arayanların uygulama etki alanı içinde çalışıyorsanız zararlı çağıranlar tarafından da bastırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
