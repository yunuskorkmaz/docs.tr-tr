---
title: Tasarımcıyı kullanarak panel denetimiyle grup denetimleri
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745645"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Panel Denetimi ile Denetimleri Gruplandırma
Windows Forms <xref:System.Windows.Forms.Panel> denetimleri diğer denetimleri gruplandırmak için kullanılır. Denetimleri gruplandırmak için üç neden vardır. Bunlardan biri, açık bir kullanıcı arabirimi için ilgili form öğelerinin görsel gruplandırmasıdır; diğer bir seçenek de, örneğin radyo düğmelerinin programlama açısından gruplandırmasıdır; Son, denetimleri tasarım zamanında bir birim olarak taşımak içindir.

## <a name="to-create-a-group-of-controls"></a>Bir Grup denetim oluşturmak için

1. Araç kutusunun **Windows Forms** sekmesinden bir <xref:System.Windows.Forms.Panel> denetimini form üzerine sürükleyin.

2. Panelin içinde her biri çizerek panele başka denetimler ekleyin.

     Bir panele eklemek istediğiniz mevcut denetimleriniz varsa, tüm denetimleri seçebilir, pano 'ya kesebilir, <xref:System.Windows.Forms.Panel> denetimini seçebilir ve sonra bunları panele yapıştırabilirsiniz. Ayrıca bunları panele sürükleyebilirsiniz.

3. Seçim Bir panele kenarlık eklemek istiyorsanız, <xref:System.Windows.Forms.BorderStyle> özelliğini ayarlayın. Üç seçenek vardır: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>ve <xref:System.Windows.Forms.BorderStyle.None>.

## <a name="see-also"></a>Ayrıca bkz.

- [Panel Denetimi](panel-control-windows-forms.md)
- [Panel Denetimine Genel Bakış](panel-control-overview-windows-forms.md)
- [Nasıl yapılır: Bir Panelin Arka Planını Ayarlama](how-to-set-the-background-of-a-windows-forms-panel.md)
