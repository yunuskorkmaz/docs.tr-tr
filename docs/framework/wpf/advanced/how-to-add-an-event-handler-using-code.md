---
title: "Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme"
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
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 348136a1feaf6e0a0824cf183a2eeec4e10b77fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-event-handler-using-code"></a>Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme
Bu örnek kod kullanarak bir öğe olarak olay işleyicisi ekleme gösterir.  
  
 Bir olay işleyicisi eklemek istiyorsanız bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğesi ve öğeyi içeren biçimlendirme sayfası zaten yüklü, kod kullanarak işleyici eklemeniz gerekir. Alternatif olarak, tamamen kod kullanarak ve kullanarak herhangi bir öğeyi bildirme olmayan bir uygulama için öğe ağacı oluşturmakta olduğunuz varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], olay işleyicilerini yapılandırılmış öğe ağacına eklemek için belirli yöntemleri çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Controls.Button> başlangıçta tanımlanan varolan sayfasına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Bir arka plan kod dosyasına bir olay işleyicisi yöntemi uygular ve daha sonra bu yöntem yeni bir olay işleyicisi ekler <xref:System.Windows.Controls.Button>.  
  
 [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] Örnek kullanır `+=` bir olay için bir işleyici atamak için işleci. Bu işleyici atamak için kullanılan, aynı işlecidir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olay işleme modeli. [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]olay işleyicileri ekleme yolu bu işleci desteklemez. Bunun yerine iki teknikleri birini gerektirir:  
  
-   Kullanım <xref:System.Windows.UIElement.AddHandler%2A> yöntemi ile birlikte bir `AddressOf` olay işleyicisi uygulamasına başvurmak için işleci.  
  
-   Kullanım `Handles` anahtar sözcüğü olay işleyici tanımının bir parçası olarak. Bu teknik burada gösterilmiyor; bkz: [Visual Basic ve WPF olay işleme](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  Olay işleyici başlangıçta ayrıştırılmış ekleme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasıdır çok daha kolaydır. Olay işleyicisi eklemek istediğiniz nesne öğesi içinde ele almak istediğiniz olay adıyla eşleşen bir öznitelik ekleyin. Arka plan kodu dosyasında tanımlanan olay işleyicisi yönteminin adı olarak bu özniteliğin değerini belirtin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası. Daha fazla bilgi için bkz: [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) veya [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
