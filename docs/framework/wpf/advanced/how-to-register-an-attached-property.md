---
title: "Nasıl yapılır: Ekli Özelliği Kaydetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37c727eee7b56473808fec06ea42044fc742f7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-an-attached-property"></a>Nasıl yapılır: Ekli Özelliği Kaydetme
Bu örnek, iliştirilmiş bir özellik kaydetmek ve böylece özelliği hem de kullanabilirsiniz ortak erişimciler sağlamak gösterilmiştir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod. Ekli özellikler tarafından tanımlanan bir sözdizimi kavramıdır olan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. İçin çoğu iliştirilmiş özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türleri bağımlılık özellikleri olarak da uygulanır. Bağımlılık özellikleri herhangi kullanabilirsiniz <xref:System.Windows.DependencyObject> türleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iliştirilmiş bir özellik kullanarak bağımlılık özelliği olarak kaydettirmek gösterilmiştir <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi. Sağlayıcı sınıf özelliği başka bir sınıf üzerinde kullanıldığında, o sınıfın meta verileri geçersiz kılmadıkça uygulanabilir özellik için varsayılan meta veri sağlama seçeneği vardır. Bu örnekte, varsayılan değeri `IsBubbleSource` özelliği ayarlanmış `false`.  
  
 Sağlayıcı sınıfı (bağımlılık özelliği olarak kaydedilmemiş olsa bile) iliştirilmiş bir özellik için statik alma ve adlandırma kuralını uyguladığınızdan set erişimcileri sağlamalıdır `Set` *[AttachedPropertyName]* ve `Get` *[AttachedPropertyName]*. Bu erişimciler gereklidir şekilde hareket [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu bir öznitelik olarak özellik algılayabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve uygun türleri çözümleyin.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.DependencyProperty>  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
