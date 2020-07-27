---
title: 'Nasıl yapılır: Enter Tuşuna Basıldığında Algılama'
description: Windows Presentation Foundation ' deki klavyede ENTER tuşunun ne zaman seçili olduğunu tespit edin. Bu örnek XAML ve arka plan kod dosyasından oluşur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163179"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Nasıl yapılır: Enter Tuşuna Basıldığında Algılama
Bu örnek, tuşa klavyede basıldığında nasıl algılanacağını göstermektedir <xref:System.Windows.Input.Key.Enter> .  
  
 Bu örnek, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya ve arka plan kod dosyasından oluşur.  
  
## <a name="example"></a>Örnek  
 Kullanıcı içindeki anahtara bastığında, <xref:System.Windows.Input.Key.Enter> <xref:System.Windows.Controls.TextBox> metin kutusundaki giriş ' ın başka bir alanında görüntülenir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .  
  
 Aşağıdaki XAML, bir, ve ' den oluşan Kullanıcı arabirimini oluşturur <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Aşağıdaki kod arkasında <xref:System.Windows.UIElement.KeyDown> olay işleyicisi oluşturulur.  Basılan anahtar <xref:System.Windows.Input.Key.Enter> anahtar ise, içinde bir ileti görüntülenir <xref:System.Windows.Controls.TextBlock> .  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
