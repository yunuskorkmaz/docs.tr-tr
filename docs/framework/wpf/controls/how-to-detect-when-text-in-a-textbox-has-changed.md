---
title: 'Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000980"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama
Bu örnekte kullanılacak yollarından biri gösterilmektedir <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> bir yöntem yürütülmeye çalışıldı olay olduğunda metinde bir <xref:System.Windows.Controls.TextBox> denetim değişti.  
  
 Arka plan kod sınıfında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeren <xref:System.Windows.Controls.TextBox> değişiklikler için izlemek istediğiniz denetimi ekleme çağrılacak bir yöntem <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay harekete geçirilir.  Bu yöntem tarafından beklenenle eşleşen bir imza içermelidir <xref:System.Windows.Controls.TextChangedEventHandler> temsilci.  
  
 Olay işleyicisinde çağrılır her içeriğini <xref:System.Windows.Controls.TextBox> denetim değiştirilirse, bir kullanıcı veya program aracılığıyla.  
  
 **Not:** Bu olay tetiklenen <xref:System.Windows.Controls.TextBox> denetim oluşturulur ve başlangıçta metin ile doldurulur.  
  
## <a name="example"></a>Örnek  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlayan, <xref:System.Windows.Controls.TextBox> belirtin, kontrolünde <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay işleyicisi yöntemi adıyla eşleşen bir değere sahip bir öznitelik.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Örnek  
 Arka plan kod sınıfında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeren <xref:System.Windows.Controls.TextBox> değişiklikler için izlemek istediğiniz denetimi ekleme çağrılacak bir yöntem <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay harekete geçirilir.  Bu yöntem tarafından beklenenle eşleşen bir imza içermelidir <xref:System.Windows.Controls.TextChangedEventHandler> temsilci.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Olay işleyicisinde çağrılır her içeriğini <xref:System.Windows.Controls.TextBox> denetim değiştirilirse, bir kullanıcı veya program aracılığıyla.  
  
 **Not:** Bu olay tetiklenen <xref:System.Windows.Controls.TextBox> denetim oluşturulur ve başlangıçta metin ile doldurulur.  
  
 Açıklamalar  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
