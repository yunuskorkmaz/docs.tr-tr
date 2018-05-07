---
title: 'Nasıl yapılır: Bağımlılık Özelliği Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: b0c5b33d841f43249f9559bd31f1ef8fe66ff05e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği Uygulama
Bu örnek nasıl yedekleneceği gösterir bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özelliği ile bir <xref:System.Windows.DependencyProperty> alan, bu nedenle bir bağımlılık özelliği tanımlama. Ne zaman kendi özelliklerinizi tanımlayın ve bunları pek çok görünüşünün desteklemek için istediğiniz [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] işlevselliği, stiller, veri bağlama, devralma, animasyon ve varsayılan değerleri dahil olmak üzere bir bağımlılık özelliği olarak uygulamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Bağımlılık özelliği ilk kaydeder çağırarak aşağıdaki örnek <xref:System.Windows.DependencyProperty.Register%2A> yöntemi. Adı depolamak için kullandığınız ve bağımlılık özelliği özelliklerini olmalıdır tanımlayıcı alanı adını <xref:System.Windows.DependencyProperty.Name%2A> bağımlılık özelliği için bir parçası olarak seçtiğiniz <xref:System.Windows.DependencyProperty.Register%2A> dizesiyle eklenmiş çağrı `Property`. Örneğin, bir bağımlılık özelliği ile kaydederseniz bir <xref:System.Windows.DependencyProperty.Name%2A> , `Location`, bağımlılık özelliği için tanımladığınız tanımlayıcı alanı adlandırılmalıdır `LocationProperty`.  
  
 Bu örnekte, bir bağımlılık özelliğinin adı ve kendi [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] erişen `State`; tanımlayıcı alanı `StateProperty`; özellik türü <xref:System.Boolean>; ve bağımlılık özelliği kaydeder tür `MyStateControl`.  
  
 Bu adlandırma deseni izlemenizi başarısız olursa, tasarımcılar özelliğinizi doğru şekilde rapor edemeyebilir ve özellik sistem stil uygulamasının belirli yönlerini beklendiği gibi davranabilir değil.  
  
 Bağımlılık özelliği için varsayılan meta verileri de belirtebilirsiniz. Bu örnek varsayılan değerini kaydeder `State` bağımlılık özellik `false`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Hakkında daha fazla bilgi ve yalnızca yedekleme aksine, bir bağımlılık özelliği uygulamak neden bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özel bir alanla özelliğine bakın [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
