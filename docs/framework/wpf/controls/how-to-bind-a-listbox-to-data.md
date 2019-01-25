---
title: 'Nasıl yapılır: Veriye ListBox Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 6d37cda057ea1e7ca6761363857a2647da37afee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650658"
---
# <a name="how-to-bind-a-listbox-to-data"></a>Nasıl yapılır: Veriye ListBox Bağlama
Bir uygulama geliştiricisi oluşturabilirsiniz <xref:System.Windows.Controls.ListBox> her içeriğini belirtmeden denetimleri <xref:System.Windows.Controls.ListBoxItem> ayrı olarak. Veri bağlama, tek tek öğelerine veri bağlamak için kullanabilirsiniz.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.ListBox> , doldurur <xref:System.Windows.Controls.ListBoxItem> adlı bir veri kaynağına veri bağlama göre öğeleri *renkleri*. Bu durumda kullanmak için gerekli değil <xref:System.Windows.Controls.ListBoxItem> her öğenin içeriğini belirtmek için etiketler.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [Denetimler](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
