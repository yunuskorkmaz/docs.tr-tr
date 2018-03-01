---
title: "Nasıl Yapılır: PrintForm Bileşenini Kullanarak Form Yazdırma (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5edad4f04b98dcf0dfa328f111db5dcb423036e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a>Nasıl Yapılır: PrintForm Bileşenini Kullanarak Form Yazdırma (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen sağlar, ekranda kullanmadan göründüğü gibi hızlı bir form görüntüsü yazdırmak bir <xref:System.Drawing.Printing.PrintDocument> bileşeni. Aşağıdaki yordamlar, bir yazıcı, Baskı Önizleme penceresinden ve kapsüllenmiş PostScript'i dosya form yazdırma gösterilmektedir.  
  
 PowerPack denetimleri artık Visual Studio'ya dahil olan, ancak bunları indirebilirsiniz [Yükleme Merkezi'nden](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-a-form-to-the-default-printer"></a>Varsayılan yazıcı için bir form yazdırma  
  
1.  İçinde **araç**, tıklatın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen için bileşen Tepsisi eklenir.  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğine <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` olay işleyicisi için bir **yazdırma**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a>Baskı Önizleme penceresinde bir form görüntülemek için  
  
1.  İçinde **araç**, tıklatın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen için bileşen Tepsisi eklenir.  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğine <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.  
  
3.  Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` olay işleyicisi için bir **yazdırma**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a>Bir dosya için bir form yazdırma  
  
1.  İçinde **araç**, tıklatın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen için bileşen Tepsisi eklenir.  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğine <xref:System.Drawing.Printing.PrintAction.PrintToFile>.  
  
3.  İsteğe bağlı olarak, seçin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> özelliği ve türü tam yolunu ve dosya için hedef dosya adı.  
  
     Bu adımı atlarsanız, kullanıcı çalışma zamanında için bir dosya adı istenir.  
  
4.  Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` olay işleyicisi için bir **yazdırma**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [Nasıl yapılır: formun istemci alanını yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Nasıl yapılır: formun istemci alanlarını ve yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Nasıl yapılır: kaydırılabilir Form yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [PrintForm bileşeni](../../../visual-basic/developing-apps/printing/printform-component.md)
