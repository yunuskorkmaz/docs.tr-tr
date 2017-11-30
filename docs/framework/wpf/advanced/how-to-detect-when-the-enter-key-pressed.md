---
title: "Nasıl yapılır: Enter Tuşuna Basıldığında Algılama"
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
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8311083b4b82d4ab4827e8d0a2cf958c67347014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Nasıl yapılır: Enter Tuşuna Basıldığında Algılama
Bu örnek nasıl algılanacağını gösterir <xref:System.Windows.Input.Key.Enter> tuşa klavyede.  
  
 Bu örnek oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.  
  
## <a name="example"></a>Örnek  
 Kullanıcı bastığında <xref:System.Windows.Input.Key.Enter> anahtarını <xref:System.Windows.Controls.TextBox>, başka bir bölümünde metin kutusundaki giriş görünür [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşan kullanıcı arabirimi oluşturan bir <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>ve bir <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Aşağıdaki arka plan kodu oluşturur <xref:System.Windows.UIElement.KeyDown> olay işleyicisi.  Basıldığında anahtarı ise <xref:System.Windows.Input.Key.Enter> anahtar, bir ileti görüntülenir <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş genel bakış](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
