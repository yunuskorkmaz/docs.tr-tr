---
title: Tasarımcıyı kullanarak bir panelin arka planını ayarlama
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731926"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Nasıl yapılır: tasarımcı kullanarak Windows Forms panelinin arka planını ayarlama

Bir Windows Forms <xref:System.Windows.Forms.Panel> denetimi hem arka plan rengini hem de arka plan görüntüsünü görüntüleyebilir. <xref:System.Windows.Forms.Control.BackColor%2A> özelliği, panelde bulunan ve Etiketler ve radyo düğmeleri gibi denetimlerin arka plan rengini ayarlar. <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmamışsa, <xref:System.Windows.Forms.Control.BackColor%2A> seçimi paneli dolduracaktır. <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlandıysa, görüntü, panelde bulunan denetimlerin arkasında görüntülenir.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.Panel> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Visual Studio 'da böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

## <a name="set-the-background-in-the-windows-forms-designer"></a>Windows Form Tasarımcısı arka planı ayarlama

1. Projeyi Visual Studio 'da açın ve <xref:System.Windows.Forms.Panel> denetimini seçin.

2. **Özellikler** penceresinde, üç sekmeye sahip bir pencere göstermek için <xref:System.Windows.Forms.Control.BackColor%2A> özelliğinin yanındaki ok düğmesine tıklayın.

3. Renk paletini göstermek için **özel** sekmesini seçin.

4. Renkler için önceden tanımlanmış adların listesini göstermek üzere **Web** veya **sistem** sekmesini seçin ve ardından bir renk seçin.

5. **Özellikler** penceresinde, <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğinin yanındaki ok düğmesine tıklayın.

6. **Aç** iletişim kutusunda, göstermek istediğiniz dosyayı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel Denetimi](panel-control-windows-forms.md)
- [Panel Denetimine Genel Bakış](panel-control-overview-windows-forms.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma](group-controls-with-wf-panel-control-using-the-designer.md)
