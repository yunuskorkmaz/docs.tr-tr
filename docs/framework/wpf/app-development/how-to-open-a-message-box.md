---
title: 'Nasıl yapılır: İleti kutusu açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: fa371b62c78a08e25de815fa44360230b6156008
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369610"
---
# <a name="how-to-open-a-message-box"></a>Nasıl yapılır: İleti kutusu açma
Bu örnek, bir ileti kutusu açma gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bir ileti kutusu, kullanıcıların bilgilerini görüntülemek için bir görüntülemeleri kalıcı bir iletişim kutusudur. Statik çağırarak bir ileti kutusu açıldığında <xref:System.Windows.MessageBox.Show%2A> yöntemi <xref:System.Windows.MessageBox> sınıfı. Zaman <xref:System.Windows.MessageBox.Show%2A> olan çağrılır, iletinin dize parametresi kullanılarak geçirilir. İlişkin çeşitli aşırı yükler <xref:System.Windows.MessageBox.Show%2A> ileti kutusunun nasıl görüneceğini yapılandırmanıza olanak sağlar (bkz <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [MessageBox örnek](https://go.microsoft.com/fwlink/?LinkID=160023)
