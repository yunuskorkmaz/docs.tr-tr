---
title: 'Nasıl yapılır: ToolStrip Denetimlerinde İki Durumlu Düğmeler Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: e688e9a220e6c82caa2d107589b5ca9a1e59e72b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052168"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Nasıl yapılır: ToolStrip Denetimlerinde İki Durumlu Düğmeler Oluşturma
Bir kullanıcı bir iki durumlu düğmeyi tıkladığında basık görünür ve kullanıcı yeniden düğmesine tıklayana kadar basık görünümü korur.  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>Toggling ToolStripButton oluşturmak için  
  
- Aşağıdaki kod örneği gibi bir kod kullanın. Bu kod, formunuzu içerdiğini varsaymaktadır bir <xref:System.Windows.Forms.ToolStrip> denetimi ve kendi <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyonu içeren bir <xref:System.Windows.Forms.ToolStripButton> adlı `toolStripButton1`. Ayrıca, adlı bir olay işleyicisi sahibi olduğunuzu varsayar `toolStripButton1_CheckedChanged`.  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripButton>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
