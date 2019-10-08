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
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004817"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Nasıl yapılır: Enter Tuşuna Basıldığında Algılama
Bu örnek, <xref:System.Windows.Input.Key.Enter> tuşuna klavyede basıldığında nasıl algılanacağını göstermektedir.  
  
 Bu örnek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasından ve arka plan kod dosyasından oluşur.  
  
## <a name="example"></a>Örnek  
 Kullanıcı <xref:System.Windows.Controls.TextBox> ' deki <xref:System.Windows.Input.Key.Enter> anahtarına bastığında, metin kutusundaki giriş [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ' nin başka bir alanında görüntülenir.  
  
 Aşağıdaki XAML, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.TextBox> ' den oluşan Kullanıcı arabirimini oluşturur.  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Aşağıdaki kod arkasında <xref:System.Windows.UIElement.KeyDown> olay işleyicisi oluşturulur.  Basılan anahtar <xref:System.Windows.Input.Key.Enter> anahtarlıysa, <xref:System.Windows.Controls.TextBlock> ' de bir ileti görüntülenir.  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
