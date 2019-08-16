---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: cadfa715b140c63b216ec0ca2e6d6a6589ae3458
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040381"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma
Windows Forms <xref:System.Windows.Forms.Panel> denetimleri, diğer denetimleri gruplandırmak için kullanılır. Denetimleri gruplandırmak için üç neden vardır. Bunlardan biri, açık bir kullanıcı arabirimi için ilgili form öğelerinin görsel gruplandırmasıdır; diğer bir seçenek de, örneğin radyo düğmelerinin programlama açısından gruplandırmasıdır; Son, denetimleri tasarım zamanında bir birim olarak taşımak içindir.

## <a name="to-create-a-group-of-controls"></a>Bir Grup denetim oluşturmak için

1. Araç kutusunun <xref:System.Windows.Forms.Panel> **Windows Forms** sekmesinden bir denetimi form üzerine sürükleyin.

2. Panelin içinde her biri çizerek panele başka denetimler ekleyin.

     Bir panele eklemek istediğiniz mevcut denetimleriniz varsa, tüm denetimleri seçebilir, panoya kesebilir, <xref:System.Windows.Forms.Panel> denetimi seçebilir ve sonra panele yapıştırabilirsiniz. Ayrıca bunları panele sürükleyebilirsiniz.

3. Seçim Bir panele kenarlık eklemek istiyorsanız, <xref:System.Windows.Forms.BorderStyle> özelliğini ayarlayın. Üç seçenek vardır: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, ve <xref:System.Windows.Forms.BorderStyle.None>.

## <a name="see-also"></a>Ayrıca bkz.

- [Panel Denetimi](panel-control-windows-forms.md)
- [Panel Denetimine Genel Bakış](panel-control-overview-windows-forms.md)
- [Nasıl yapılır: Panelin arka planını ayarlama](how-to-set-the-background-of-a-windows-forms-panel.md)
