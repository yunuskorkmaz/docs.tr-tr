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
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972360"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Nasıl yapılır: ToolStrip Denetimlerinde İki Durumlu Düğmeler Oluşturma

Bir Kullanıcı iki durumlu düğmeye tıkladığında, basık görünür ve Kullanıcı düğmeye tekrar tıklaana kadar basık görünümü korur.

## <a name="to-create-a-toggling-toolstripbutton"></a>Geçiş bir ToolStripButton oluşturmak için

- Aşağıdaki kod örneği gibi bir kod kullanın. Bu <xref:System.Windows.Forms.ToolStrip> kod, formunuzun bir denetim içerdiğini ve <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyonunun bir <xref:System.Windows.Forms.ToolStripButton> aranan `toolStripButton1`içerdiğini varsayar. Ayrıca, adlı `toolStripButton1_CheckedChanged`bir olay işleyicisine sahip olduğunuzu varsaymaktadır.

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
