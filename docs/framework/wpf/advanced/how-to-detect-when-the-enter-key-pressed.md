---
title: 'Nasıl yapılır: Enter Tuşuna Basıldığında Algılama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: 1de11cd30d1990dcd2bc927a69b60c66c721addb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
