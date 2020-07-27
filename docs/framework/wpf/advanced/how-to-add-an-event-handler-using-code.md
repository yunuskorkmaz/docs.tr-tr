---
title: 'Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme'
description: Bu örneği, XAML kullanarak bildirmek yerine kodu kullanarak Windows Presentation Foundation bir öğeye olay işleyicisi ekleme hakkında bilgi almak için kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166372"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme
Bu örnek, kod kullanarak bir öğeye bir olay işleyicisinin nasıl ekleneceğini gösterir.  
  
 Bir öğeye bir olay işleyicisi eklemek istiyorsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve öğesini içeren biçimlendirme sayfası zaten yüklüyse, kodu kullanarak işleyiciyi eklemeniz gerekir. Alternatif olarak, kod kullanarak bir uygulama için öğe ağacını oluşturuyorsanız ve kullanarak herhangi bir öğe bildirmiyorsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , oluşturulan öğe ağacına olay işleyicileri eklemek için belirli yöntemleri çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Button> içinde başlangıçta tanımlanan varolan bir sayfaya yeni bir ekler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Arka plan kod dosyası bir olay işleyicisi yöntemi uygular ve sonra bu yöntemi ' de yeni bir olay işleyicisi olarak ekler <xref:System.Windows.Controls.Button> .  
  
 C# örneği bir `+=` olaya işleyici atamak için işlecini kullanır. Bu, ortak dil çalışma zamanı (CLR) olay işleme modelinde bir işleyici atamak için kullanılan işleçtir. Microsoft Visual Basic, olay işleyicilerini ekleme yöntemi olarak bu işleci desteklemez. Bunun yerine iki teknikten birini gerektirir:  
  
- <xref:System.Windows.UIElement.AddHandler%2A> `AddressOf` Olay işleyicisi uygulamasına başvurmak için yöntemini bir işleçle birlikte kullanın.  
  
- `Handles`Anahtar sözcüğünü olay işleyicisi tanımının bir parçası olarak kullanın. Bu teknik burada gösterilmez; bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> İlk ayrıştırılmış sayfada bir olay işleyicisi eklemek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çok basittir. Olay işleyicisini eklemek istediğiniz nesne öğesi içinde, işlemek istediğiniz olayın adıyla eşleşen bir öznitelik ekleyin. Sonra bu özniteliğin değerini, sayfanın arka plan kod dosyasında tanımladığınız olay işleyicisi yönteminin adı olarak belirtin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Daha fazla bilgi için bkz. [xaml 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) veya [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nasıl Yapılır Konuları](events-how-to-topics.md)
