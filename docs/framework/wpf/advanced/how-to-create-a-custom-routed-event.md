---
title: "Nasıl yapılır: Özel Gönderilmiş Olay Oluşturma"
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
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e901242b265e0012f9ad65d9eaab89b1b63b40ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-routed-event"></a>Nasıl yapılır: Özel Gönderilmiş Olay Oluşturma
Olay yönlendirme desteklemek kendi özel olayınız için kaydetmeniz gerekir. bir <xref:System.Windows.RoutedEvent> kullanarak <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemi. Bu örnek özel yönlendirilmiş olay oluşturma temelleri gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği gibi önce kaydetmeniz bir <xref:System.Windows.RoutedEvent> kullanarak <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemi. Kural tarafından <xref:System.Windows.RoutedEvent> statik alan adı son eki ile bitmelidir ***olay***. Bu örnekte, olay adıdır `Tap` ve olayın yönlendirme stratejisi <xref:System.Windows.RoutingStrategy.Bubble>. Kayıt çağrısından sonra Ekle ve Kaldır sağlayabilirsiniz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olayı için olay erişimcileri.  
  
 Aracılığıyla olayı olsa bile unutmayın `OnTap` söz konusu örnekte, nasıl olayınızın yükseltmek veya olayınızın değişiklikleri nasıl yanıt verdiği sanal yöntemi gereksinimlerinize göre değişir.  
  
 Ayrıca bu örnek temel olarak, tüm bir alt uyguladığını unutmayın <xref:System.Windows.Controls.Button>; o alt sınıf ayrı bir derleme yerleşik ve özel bir sınıf ayrı olarak örneği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfası. Altsınıflanmış denetimler diğer denetimlerden oluşan ağaçlara eklenebilir ve bu durumda, çok aynı olay Yönlendirme yetenekleri bu denetimlerinde özel olaylar olarak herhangi bir yerel sahip kavramı göstermeye budur [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öğesi.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Tünel olayları oluşturulur aynı yolla ancak ile <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> kümesine <xref:System.Windows.RoutingStrategy.Tunnel> kayıt çağrısında. Kurala göre olaylar tünel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "Önizleme" sözcüğüyle öneki.  
  
 Nasıl kabarcıklanma olayları çalışma örneği görmek için bkz: [yönlendirilmiş olayını işle](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Giriş genel bakış](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Denetim genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
