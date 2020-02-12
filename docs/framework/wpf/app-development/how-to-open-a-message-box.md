---
title: 'Nasıl yapılır: Ileti kutusu açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123733"
---
# <a name="how-to-open-a-message-box"></a>Nasıl yapılır: Ileti kutusu açma
Bu örnekte bir ileti kutusunun nasıl açılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 İleti kutusu, kullanıcılara bilgi görüntülemek için önceden yazılmış bir kalıcı iletişim kutusudur. <xref:System.Windows.MessageBox> sınıfının statik <xref:System.Windows.MessageBox.Show%2A> yöntemi çağırarak bir ileti kutusu açılır. <xref:System.Windows.MessageBox.Show%2A> çağrıldığında, ileti dize parametresi kullanılarak geçirilir. <xref:System.Windows.MessageBox.Show%2A> birkaç aşırı yüklemesi, bir ileti kutusunun nasıl görüneceğini yapılandırmanıza olanak tanır (bkz. <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MessageBox örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
