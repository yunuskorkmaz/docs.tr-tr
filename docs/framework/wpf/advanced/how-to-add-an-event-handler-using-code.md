---
title: 'Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 017b32dc07f62cc4553a84f7b91687fb34a53c65
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937466"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme
Bu örnek, kod kullanarak bir öğeye bir olay işleyicisinin nasıl ekleneceğini gösterir.  
  
 Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeye bir olay işleyicisi eklemek istiyorsanız ve öğesini içeren biçimlendirme sayfası zaten yüklüyse, kodu kullanarak işleyiciyi eklemeniz gerekir. Alternatif olarak, kod kullanarak bir uygulama için öğe ağacını oluşturuyorsanız ve kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]herhangi bir öğe bildirmiyorsanız, oluşturulan öğe ağacına olay işleyicileri eklemek için belirli yöntemleri çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, içinde <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]başlangıçta tanımlanan varolan bir sayfaya yeni bir ekler. Arka plan kod dosyası bir olay işleyicisi yöntemi uygular ve sonra bu yöntemi ' de <xref:System.Windows.Controls.Button>yeni bir olay işleyicisi olarak ekler.  
  
 C# Örnek, bir olaya `+=` bir işleyici atamak için işlecini kullanır. Bu, ortak dil çalışma zamanı (CLR) olay işleme modelinde bir işleyici atamak için kullanılan işleçtir. Microsoft Visual Basic, olay işleyicilerini ekleme yöntemi olarak bu işleci desteklemez. Bunun yerine iki teknikten birini gerektirir:  
  
- Olay işleyicisi uygulamasına başvurmak için `AddressOf` yönteminibirişleçlebirliktekullanın.<xref:System.Windows.UIElement.AddHandler%2A>  
  
- `Handles` Anahtar sözcüğünü olay işleyicisi tanımının bir parçası olarak kullanın. Bu teknik burada gösterilmez; bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> İlk ayrıştırılmış [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfada bir olay işleyicisi eklemek çok basittir. Olay işleyicisini eklemek istediğiniz nesne öğesi içinde, işlemek istediğiniz olayın adıyla eşleşen bir öznitelik ekleyin. Sonra bu özniteliğin değerini, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfanın arka plan kod dosyasında tanımladığınız olay işleyicisi yönteminin adı olarak belirtin. Daha fazla bilgi için bkz. [xaml 'ye Genel Bakış (WPF)](xaml-overview-wpf.md) veya [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nasıl Yapılır Konuları](events-how-to-topics.md)
