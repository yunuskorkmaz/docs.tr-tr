---
title: 'Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987040"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Nasıl yapılır: Varolan denetimleri farklı bir üst öğeye yeniden atama

Formunuzda bulunan denetimleri yeni bir kapsayıcı denetimine atayabilirsiniz.

1. Visual Studio 'da, <xref:System.Windows.Forms.Button> **araç kutusundan** üç denetimi form üzerine sürükleyin. Bunları birbirlerine yakın bir konuma konumlandırın, ancak hizalanmamış olarak bırakın.

2. **Araç kutusunda** <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesine tıklayın. (Simgeyi formun üzerine sürüklemeyin.)

3. Fare işaretçisini üç <xref:System.Windows.Forms.Button> denetime yakın bir şekilde taşıyın.

   İşaretçi, <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesinin eklendiği çapraz artı işaretine dönüşür.

4. Fare düğmesine tıklayın ve basılı tutun.

5. <xref:System.Windows.Forms.FlowLayoutPanel> Denetimin anahattını çizmek için fare işaretçisini sürükleyin.

6. Ana hattı üç <xref:System.Windows.Forms.Button> denetimin çevresine çizin.

7. Fare düğmesini bırakın.

   Üç <xref:System.Windows.Forms.Button> denetim artık <xref:System.Windows.Forms.FlowLayoutPanel> denetime eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Anlık görüntü çizgilerini kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
