---
title: 'Nasıl Yapılır: Kaydırılabilir Form Yazdırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: d43c2e0e564f6f0c37831cd3105a16c4bc4aaea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a>Nasıl Yapılır: Kaydırılabilir Form Yazdırma (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen sağlar, hızlı bir form görüntüsü kullanmadan yazdırmak bir <xref:System.Drawing.Printing.PrintDocument> bileşeni. Varsayılan olarak, yalnızca form görüntülenmekte kısmını yazdırılır; Kullanıcı formu çalışma zamanında yeniden boyutlandırılabilir değilse, görüntüyü tasarlandığı gibi yazdırabilir değil. Formu yeniden boyutlandırılmış bile, aşağıdaki yordamı kaydırılabilir form tam istemci alanını yazdırma gösterilmektedir.  
  
 PowerPack denetimleri artık Visual Studio'ya dahil olan, ancak bunları indirebilirsiniz [Yükleme Merkezi'nden](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a>Kaydırılabilir form tam istemci alanını yazdırma  
  
1.  İçinde **araç**, tıklatın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen için bileşen Tepsisi eklenir.  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğine <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` olay işleyicisi için bir **yazdırma**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  Bazı işletim sistemleri, metin veya tarafından çizilmiş grafik <xref:System.Drawing.Graphics> yöntemleri yazdırma doğru. Bu durumda, yazdırmak mümkün olmaz `Scrollable` parametresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [PrintForm Bileşeni](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Nasıl Yapılır: Formun İstemci Alanını Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Nasıl Yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
