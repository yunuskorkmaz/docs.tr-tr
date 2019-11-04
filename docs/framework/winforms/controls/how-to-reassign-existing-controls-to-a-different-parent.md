---
title: 'Nasıl yapılır: Mevcut Denetimleri Farklı bir Üst Öğeye Yeniden Atama'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459201"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Nasıl yapılır: mevcut denetimleri farklı bir üst öğeye yeniden atama

Formunuzda bulunan denetimleri yeni bir kapsayıcı denetimine atayabilirsiniz.

1. Visual Studio 'da, **araç kutusundan** üç <xref:System.Windows.Forms.Button> denetimini form üzerine sürükleyin. Bunları birbirlerine yakın bir konuma konumlandırın, ancak hizalanmamış olarak bırakın.

2. **Araç kutusunda**<xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesine tıklayın. (Simgeyi formun üzerine sürüklemeyin.)

3. Fare işaretçisini üç <xref:System.Windows.Forms.Button> denetimine yakın bir şekilde taşıyın.

   İşaretçi, eklenen <xref:System.Windows.Forms.FlowLayoutPanel> denetim simgesiyle çapraz artı işaretine dönüşür.

4. Fare düğmesine tıklayın ve basılı tutun.

5. <xref:System.Windows.Forms.FlowLayoutPanel> denetiminin anahattını çizmek için fare işaretçisini sürükleyin.

6. Ana hattı üç <xref:System.Windows.Forms.Button> denetiminin çevresine çizin.

7. Fare düğmesini bırakın.

   Üç <xref:System.Windows.Forms.Button> denetimi artık <xref:System.Windows.Forms.FlowLayoutPanel> denetimine eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
