---
title: 'Nasıl yapılır: Tasarımcı kullanarak Windows Forms Panel denetimi ile denetimleri gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 706a020bfb007250b9a1b708da25704aacd755e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601547"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak Windows Forms Panel denetimi ile denetimleri gruplandırma
Windows Forms <xref:System.Windows.Forms.Panel> denetimleri başka denetimler gruplandırmak için kullanılır. Grup denetimleri için üç neden vardır. NET kullanıcı arabirimi için ilgili form öğelerinin gruplandırma visual biridir; başka bir program, radyo düğmeleri örneğin gruplandırmadır; Tasarım zamanında bir birim olarak denetimleri taşımak için son olur.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-group-of-controls"></a>Denetimlerin bir grup oluşturmak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Panel> denetimi **Windows Forms** forma araç kutusu sekmesi.  
  
2.  Her bir panel içinde çizim paneli, diğer denetimleri ekleyin.  
  
     Bir panelinde eklemek istediğiniz mevcut denetimleri varsa, tüm denetimler seçip onları seçin panoya Kes <xref:System.Windows.Forms.Panel> denetlemek ve bunları paneline yapıştırın. Ayrıca bunları paneline sürükleyebilirsiniz.  
  
3.  (İsteğe bağlı) Bir panel için bir kenarlık eklemek istiyorsanız, kendi <xref:System.Windows.Forms.BorderStyle> özelliği. Üç seçeneğiniz vardır: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, ve <xref:System.Windows.Forms.BorderStyle.None>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Panel Denetimi](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [Panel Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [Nasıl yapılır: Bir panelin arka planını ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
