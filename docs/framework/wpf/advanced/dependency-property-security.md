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
ms.openlocfilehash: 825b2a3dc79300f0cc26514398b8de0abee64fd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540510"
---
# <a name="dependency-property-security"></a>Bağımlılık Özelliği Güvenliği
Bağımlılık özellikleri genellikle ortak özellikler olarak düşünülmelidir. Doğası [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özelliği sistemin bir bağımlılık özelliği değerini hakkında güvenlik garantisi yapma olanağı engeller.  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Erişim ve güvenliği sarmalayıcıları ve bağımlılık özellikleri  
 Genellikle, bağımlılık özellikleri "sarmalayıcı" ile birlikte uygulanan [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] bir örnekten özelliği alma veya kolaylaştıran özellikler. Ancak sarmalayıcıları arka plandaki uygulamak gerçekten yalnızca kullanışlı yöntemler <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> bağımlılık özellikleri ile kullanılırken kullanılan statik çağrıları. Bunu başka bir yolla düşünürsek, özellikleri olarak sunulan [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] bağımlılık özelliği yerine özel bir alana göre yedeklenmek için özellikler. Sarmalayıcılar uygulanan güvenlik mekanizmaları özelliği sistem davranışının ve erişimin temel alınan bağımlılık özelliği paralel değil. Sarmalayıcı üzerinde güvenlik talebi yerleştirme yalnızca kolaylık metodunun kullanımını engeller ancak çağrıları önlemez <xref:System.Windows.DependencyObject.GetValue%2A> veya <xref:System.Windows.DependencyObject.SetValue%2A>. Benzer şekilde, yerleştirme korumalı veya özel erişim düzeyi sarmalayıcılar üzerinde etkili bir güvenlik sağlamaz.  
  
 Kendi bağımlılık özellikleri yazıyorsanız, sarmalayıcıları bildirmeniz gerekir ve <xref:System.Windows.DependencyProperty> tanımlayıcı alanı public üyeler, böylece çağıranlar bu özelliğin doğru erişim düzeyi hakkında bilgi (kendi deposu olması nedeniyle çağıranlar bağımlılık özelliği olarak uygulanan).  
  
 Özel bağımlılık özelliği için özelliğinizi salt okunur bağımlılık özelliği olarak kaydedebilirsiniz ve bu başvuru tutmaz herkes tarafından ayarlanan bir özelliği önleme etkili bir yol sağlar <xref:System.Windows.DependencyPropertyKey> bu özellik için. Daha fazla bilgi için bkz: [salt okunur bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
> [!NOTE]
>  Bildirme bir <xref:System.Windows.DependencyProperty> tanımlayıcı alanı private değil Yasak ve özel bir sınıf hemen sunulan ad alanı azaltmaya yardımcı olmak için alanlara kullanılabilir, ancak böyle bir özellik "aynı herkese açık özel" düşünülmemelidir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] dil tanımları sonraki bölümde anlatılan sebeplerden dolayı bu erişim düzeyini tanımlayın.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Özellik sistem etkilenmesi bağımlılık özellikleri  
 Genelde kullanışlı değildir ve bildirmek için büyük olasılıkla yanıltıcıdır, bir <xref:System.Windows.DependencyProperty> gibi herhangi bir erişim düzeyi ortak dışında. Bu erişim düzeyi ayarı yalnızca birisi örneğine başvuru bildiren sınıfından almak engeller. Döndürülecek özellik sisteminin çeşitli yönleri ancak bir <xref:System.Windows.DependencyProperty> sınıfının bir örneği veya türetilmiş sınıf örneği var ve bu tanımlayıcı içinde hala kullanılabilir olarak belirli bir özellik tanımlama yolu olarak bir <xref:System.Windows.DependencyObject.SetValue%2A> bile çağırın özgün statik tanımlayıcı özel bildirilirse. Ayrıca, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> sanal yöntemler değer değiştiren herhangi varolan bağımlılık özelliği bilgileri alırsınız. Ayrıca, <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> yöntemi örneği yerel olarak ayarlanmış herhangi bir özellik için tanımlayıcılar döndürür değeri.  
  
### <a name="validation-and-security"></a>Doğrulama ve güvenlik  
 İstek uygulama bir <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> ve bir özellik ayarlanmasını önlemek için isteğe bağlı hatasında doğrulama hatası bekleniyor yeterli güvenlik mekanizması değil. Set-değer geçersiz kılma zorlanmış aracılığıyla <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> bu Arayanların uygulama etki alanı içinde çalışıyorsanız da zararlı çağıranlar tarafından atlanması.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
