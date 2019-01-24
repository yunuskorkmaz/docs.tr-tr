---
title: 'Nasıl yapılır: (Visual Basic) formun istemci alanını yazdırma'
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: 2c808b480c38fc34006dcdf5832a814dfef1c62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505633"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a>Nasıl yapılır: (Visual Basic) formun istemci alanını yazdırma
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen kullanmadan bir form görüntüsü hızla yazdırmanızı sağlar bir <xref:System.Drawing.Printing.PrintDocument> bileşeni. Aşağıdaki yordam, yalnızca bir başlık çubuğu, kenarlıklar ve kaydırma çubukları olmadan bir formun istemci alanını yazdırma gösterilmektedir.  
  
 PowerPack denetimleri artık Visual Studio'ya dahil, ancak bunları indirebilirsiniz [İndirme Merkezi](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-client-area-of-a-form"></a>Formun istemci alanını yazdırma  
  
1.  İçinde **araç kutusu**, tıklayın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen, bileşen tepsisine eklenir.  
  
2.  İçinde **özellikleri** penceresinde <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğini <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` için olay işleyicisi bir **yazdırma**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  Bazı işletim sistemleri, metin veya grafikleri tarafından çizilen <xref:System.Drawing.Graphics> yöntemleri yazdırma doğru. Bu durumda, uyumlu yazdırma yöntemi kullanın: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>
- [PrintForm Bileşeni](../../../visual-basic/developing-apps/printing/printform-component.md)
- [Nasıl yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
- [Nasıl yapılır: Kaydırılabilir Form Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
