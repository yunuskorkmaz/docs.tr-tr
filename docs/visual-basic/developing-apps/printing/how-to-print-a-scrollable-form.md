---
title: 'Nasıl Yapılır: Kaydırılabilir Form Yazdırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: 4a509b7c48f2bff705bc95e58fb88252cb8ca4b9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486626"
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a>Nasıl Yapılır: Kaydırılabilir Form Yazdırma (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen kullanmadan bir form görüntüsü hızla yazdırmanızı sağlar bir <xref:System.Drawing.Printing.PrintDocument> bileşeni. Varsayılan olarak, yalnızca şu anda görünür bölüme biçiminde yazdırılır. Kullanıcı formu çalışma zamanında yeniden boyutlandırılmış, görüntü beklendiği gibi yazdırabilir değil. Formu yeniden boyutlandırıldı bile aşağıdaki yordamı kaydırılabilir form, tam istemci alanını yazdırma nasıl gösterir.  
  
 PowerPack denetimleri artık Visual Studio'ya dahil, ancak bunları indirebilirsiniz [İndirme Merkezi](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a>Kaydırılabilir form tam istemci alanını yazdırma  
  
1.  İçinde **araç kutusu**, tıklayın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşeni bileşen tepsisine eklenir.  
  
2.  İçinde **özellikleri** penceresinde <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğini <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` için olay işleyicisi bir **yazdırma**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  Bazı işletim sistemleri, metin veya grafikleri tarafından çizilen <xref:System.Drawing.Graphics> yöntemleri yazdırma doğru. Bu durumda, yazdırmak mümkün olmayacaktır `Scrollable` parametresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [PrintForm Bileşeni](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Nasıl Yapılır: Formun İstemci Alanını Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Nasıl Yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
