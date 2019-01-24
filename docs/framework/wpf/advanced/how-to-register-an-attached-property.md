---
title: 'Nasıl yapılır: Ekli Özelliği Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: 71b516a1d181c409fef397b7c959860d47d05b37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608566"
---
# <a name="how-to-register-an-attached-property"></a>Nasıl yapılır: Ekli Özelliği Kaydetme
Bu örnekte, ekli özelliği kaydetme ve böylece özelliği hem de kullanabilirsiniz, ortak erişimciler sağlamak gösterilmektedir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod. Ekli özellikler tarafından tanımlanan bir söz dizimi kavram olan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Çoğu iliştirilmiş özellik için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türleri de bağımlılık özellikleri uygulanır. Bağımlılık özellikleri kullanabilirsiniz herhangi <xref:System.Windows.DependencyObject> türleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneği kullanarak, bir bağımlılık özelliği ekli özelliği kaydetme işlemi gösterilmektedir <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi. Sağlayıcı sınıfı özelliği başka bir sınıf üzerinde kullanıldığında, bu sınıfın meta veriler geçersiz kılmadıkça geçerli özelliği için varsayılan meta veri sağlama seçeneği vardır. Bu örnekte, varsayılan değerini `IsBubbleSource` özelliği `false`.  
  
 Ekli özelliği (bir bağımlılık özelliği olarak kaydedilmemiş olsa bile) için sağlayıcı sınıfı statik get ve set erişimcileri, adlandırma kuralını uyguladığınızdan sağlamalıdır `Set` *[AttachedPropertyName]* ve `Get` *[AttachedPropertyName]*. Bunlar gerekli şekilde acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu özniteliği olarak özelliği algılayabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve uygun türleri çözümlemek.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.DependencyProperty>
- [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
