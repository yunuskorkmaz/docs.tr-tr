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
ms.openlocfilehash: 457b8cf5c68096b20df7fe39f1cc3f40358f34d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460431"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme
Bu örnek, kod kullanarak bir öğeye bir olay işleyicisinin nasıl ekleneceğini gösterir.  
  
 Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğesine bir olay işleyicisi eklemek istiyorsanız ve öğesini içeren biçimlendirme sayfası zaten yüklüyse, kodu kullanarak işleyiciyi eklemeniz gerekir. Alternatif olarak, kod kullanarak bir uygulama için öğe ağacını oluşturuyorsanız ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak herhangi bir öğe bildirmiyorsanız, oluşturulan öğe ağacına olay işleyicileri eklemek için belirli yöntemleri çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ilk olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]tanımlanmış varolan bir sayfaya yeni bir <xref:System.Windows.Controls.Button> ekler. Arka plan kod dosyası bir olay işleyicisi yöntemi uygular ve sonra bu yöntemi <xref:System.Windows.Controls.Button>yeni bir olay işleyicisi olarak ekler.  
  
 Örnek C# , bir olaya bir işleyici atamak için `+=` işlecini kullanır. Bu, ortak dil çalışma zamanı (CLR) olay işleme modelinde bir işleyici atamak için kullanılan işleçtir. Microsoft Visual Basic, olay işleyicilerini ekleme yöntemi olarak bu işleci desteklemez. Bunun yerine iki teknikten birini gerektirir:  
  
- Olay işleyicisi uygulamasına başvurmak için <xref:System.Windows.UIElement.AddHandler%2A> yöntemini bir `AddressOf` işleciyle birlikte kullanın.  
  
- `Handles` anahtar sözcüğünü olay işleyicisi tanımının bir parçası olarak kullanın. Bu teknik burada gösterilmez; bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> İlk ayrıştırılmış [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasında bir olay işleyicisi eklemek çok basittir. Olay işleyicisini eklemek istediğiniz nesne öğesi içinde, işlemek istediğiniz olayın adıyla eşleşen bir öznitelik ekleyin. Daha sonra bu özniteliğin değerini, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasının arka plan kod dosyasında tanımladığınız olay işleyicisi yönteminin adı olarak belirtin. Daha fazla bilgi için bkz. [xaml 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) veya [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nasıl Yapılır Konuları](events-how-to-topics.md)
