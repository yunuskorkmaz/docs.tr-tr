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
ms.openlocfilehash: a3850875c8ca747f8709b55f8fe721d25be24304
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776694"
---
# <a name="how-to-create-a-custom-routed-event"></a>Nasıl yapılır: Özel Yönlendirilmiş Olay Oluşturma
Olay yönlendirme desteklemek özel etkinliği için kaydetmeniz gerekir. bir <xref:System.Windows.RoutedEvent> kullanarak <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemi. Bu örnekte, özel gönderilmiş olay oluşturma hakkındaki temel bilgileri gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği gibi önce kaydetmeniz bir <xref:System.Windows.RoutedEvent> kullanarak <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemi. Kural olarak, <xref:System.Windows.RoutedEvent> statik alan adı soneki ile bitmelidir ***olay***. Bu örnekte, olay adıdır `Tap` ve olay yönlendirme stratejisidir <xref:System.Windows.RoutingStrategy.Bubble>. Kayıt çağrısından sonra ekleme ve kaldırma sağlayabilirsiniz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olayı için olay erişimcileri.  
  
 Aracılığıyla olayı olsa bile unutmayın `OnTap` söz konusu örnekte, nasıl etkinliğiniz yükseltmeniz veya olayınızın değişiklikleri nasıl yanıt verdiği sanal yöntem gereksinimlerinize bağlıdır.  
  
 Ayrıca bu örnek temel bir tüm öğesinin uyguladığını unutmayın <xref:System.Windows.Controls.Button>; o alt sınıf ayrı bir derlemeyi ve ardından özel bir sınıf ayrı olarak örneği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfası. Altsınıflanmış denetimler denetimden oluşan ağaçlara eklenebilir ve bu durumda, aynı olay yönlendirme özelliklerini bu denetimlerinde özel olaylar herhangi bir yerel sahip konsepti açıklamak amacıyla budur [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öğesi.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Tünel olayları oluşturulur aynı şekilde ancak ile <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> kümesine <xref:System.Windows.RoutingStrategy.Tunnel> kayıt çağrısında. Kural gereği, olayları tünel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "Preview" sözcüğü öneki.  
  
 Nasıl tırmanma olayları iş bir örneğini görmek için bkz: [bir yönlendirilmiş olayı işleme](how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Girişe Genel Bakış](input-overview.md)
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
