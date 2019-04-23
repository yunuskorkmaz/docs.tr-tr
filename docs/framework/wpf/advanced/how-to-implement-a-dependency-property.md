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
ms.openlocfilehash: e2f18cb3941be2ebf4315a844c05b91ff49c6aa2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223807"
---
# <a name="how-to-implement-a-dependency-property"></a>Nasıl yapılır: Bağımlılık Özelliği Uygulama
Bu örnek nasıl yedekleneceği gösterir bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özelliğiyle bir <xref:System.Windows.DependencyProperty> alan, bu nedenle bir bağımlılık özelliği tanımlama. Ne zaman kendi özelliklerini tanımlayın ve bunların birçok yönden desteklemek için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stilleri, veri bağlama, devralma, animasyon ve varsayılan değerleri dahil işlevleri, bir bağımlılık özelliği olarak uygulamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Bağımlılık özelliği ilk kaydeder çağırarak aşağıdaki örnekte <xref:System.Windows.DependencyProperty.Register%2A> yöntemi. Adı depolamak için kullandığınız ve bağımlılık özelliği özelliklerini olmalıdır tanımlayıcı alanı adını <xref:System.Windows.DependencyProperty.Name%2A> parçası olarak bağımlılık özelliği için seçtiğiniz <xref:System.Windows.DependencyProperty.Register%2A> çağrı, eklenen dizesiyle `Property`. Örneğin, bir bağımlılık özelliği ile kaydederseniz bir <xref:System.Windows.DependencyProperty.Name%2A> , `Location`, bağımlılık özelliği için tanımladığınız tanımlayıcı alanı adlandırılmalıdır `LocationProperty`.  
  
 Bu örnekte, bağımlılık özelliği adı ve kendi [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] erişimcisi `State`; tanımlayıcı alanı `StateProperty`; özellik türü <xref:System.Boolean>; ve bağımlılık özelliği kaydeden türü `MyStateControl`.  
  
 Şu adlandırma desenini izler yapamazsanız, tasarımcılar, özelliği doğru şekilde rapor edemeyebilir ve bazı yönlerini özelliği sistem stil uygulama beklendiği gibi çalışmayabilir.  
  
 Bağımlılık özelliği için varsayılan meta verileri de belirtebilirsiniz. Bu örnekte varsayılan değerini kaydeder `State` bağımlılık özellik `false`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Hakkında daha fazla bilgi ve neden yalnızca yedekleme aksine, bir bağımlılık özelliği uygulama için bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özel bir alan özelliğine bakın [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Nasıl Yapılır Konuları](properties-how-to-topics.md)
