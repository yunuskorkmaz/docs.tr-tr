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
ms.openlocfilehash: 4e8344ebcb0406a7da29787c5a4377760f55597e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499138"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme
Bu örnek kod kullanarak bir öğe için bir olay işleyicisi eklemek nasıl gösterir.  
  
 Bir olay işleyicisi eklemek istiyorsanız bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğesi ve öğeyi içeren biçimlendirme sayfası zaten yüklendi, kod kullanarak işleyicisi eklemeniz gerekir. Alternatif olarak, uygulamanın tamamen kodla ve kullanarak herhangi bir öğeyi bildirmeyerek öğe ağacında oluşturmakta olduğunuz varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], oluşturulmuş öğe ağacına olay işleyicileri eklemek için özel bir yöntem çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Controls.Button> başlangıçta tanımlanan varolan sayfasına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Arka plan kod dosyasında olay işleyicisi yöntemi uygular ve sonra bu yöntem yeni bir olay işleyicisi ekler <xref:System.Windows.Controls.Button>.  
  
 C# Örnekte `+=` bir olaya bir işleyici atamak için işleç. Bu işleyici atamak için kullanılan, aynı işlecidir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olay işleme modeli. Microsoft Visual Basic, olay işleyicileri ekleme bir yol bu işleci desteklemez. Bunun yerine iki tekniklerden birini gerektirir:  
  
-   Kullanım <xref:System.Windows.UIElement.AddHandler%2A> yöntemi ile birlikte bir `AddressOf` olay işleyicisinin uygulaması başvurmak için işleci.  
  
-   Kullanım `Handles` olay işleyici tanımının bir parçası olarak anahtar sözcüğü. Bu teknik burada gösterilmez; bkz: [Visual Basic ve WPF olay işleme](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  Olay işleyici başlangıçta ayrıştırılmış ekleme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası çok basittir. Olay işleyicisi eklemek istediğiniz nesne öğesi içinde kullanmak istediğiniz olay adıyla eşleşen bir öznitelik ekleyin. Bu özniteliğin değeri arka plan kod dosyasında tanımlanan olay işleyicisi yönteminin adı belirtmezseniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası. Daha fazla bilgi için [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) veya [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
