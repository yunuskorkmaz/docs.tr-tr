---
title: 'Nasıl yapılır: Özel Yönlendirilmiş Olay Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401473"
---
# <a name="how-to-create-a-custom-routed-event"></a>Nasıl yapılır: Özel Yönlendirilmiş Olay Oluşturma
Olay yönlendirmeyi desteklemek için özel olaylarınızın, <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemini kullanarak kaydetmeniz gerekir. Bu örnekte, özel bir yönlendirilmiş olay oluşturmanın temelleri gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği gibi, öncelikle <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemini kullanarak bir kayıt kaydedersiniz. Kurala <xref:System.Windows.RoutedEvent> göre statik alan adı, son ek ***olay***ile bitmelidir. Bu örnekte, olayın `Tap` adı ve <xref:System.Windows.RoutingStrategy.Bubble>olay yönlendirme stratejisidir. Kayıt çağrısından sonra, olay için ortak dil çalışma zamanı (CLR) olay erişimcileri ekleme ve kaldırma sağlayabilirsiniz.  
  
 Olay bu özel örnekteki `OnTap` sanal yöntem üzerinden oluşturulsa da, olaylarınızı nasıl yükseltebileceğinizi veya olaylarınızın değişikliklere nasıl yanıt vereceğini, gereksinimlerinize bağlı olarak unutmayın.  
  
 Ayrıca bu örnek, <xref:System.Windows.Controls.Button>temel olarak bir alt sınıfının tamamını uygular; bu alt sınıf ayrı bir derleme olarak oluşturulur ve ardından ayrı [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir sayfada özel bir sınıf olarak oluşturulur. Bu, alt sınıflı denetimlerin diğer denetimlerden oluşan ağaçlara eklenebilme kavramını göstermek ve bu durumda, bu denetimlerde özel olayların herhangi bir yerel [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öğe ile aynı olay yönlendirme özelliklerine sahip olduğunu gösterir.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Tünel olayları aynı şekilde oluşturulur, ancak <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> kayıt çağrısında olarak <xref:System.Windows.RoutingStrategy.Tunnel> ayarlanır. Kurala göre, içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tünel olayları "Preview" kelimesiyle ön ek olarak uygulanır.  
  
 Kabarcıklanma olaylarının nasıl çalıştığı hakkında bir örnek görmek için bkz. [yönlendirilmiş olayı işleme](how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Girişe Genel Bakış](input-overview.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
