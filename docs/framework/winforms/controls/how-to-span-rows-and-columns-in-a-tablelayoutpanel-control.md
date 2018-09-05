---
title: 'Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: 5363e7a7def8d2593d3ac474deb9d3d7b77d3912
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556894"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma
Denetimlerini bir <xref:System.Windows.Forms.TableLayoutPanel> denetim bitişik satır ve sütunları yayılabilir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-span-columns-and-rows"></a>Satırları ve sütunları yaymasına izin  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** sol üst hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetimi.  
  
3.  Ayarlama <xref:System.Windows.Forms.Button> denetimin **ColumnSpan** özelliğini **2**. Unutmayın <xref:System.Windows.Forms.Button> denetim birinci ve ikinci sütunların yayılır.  
  
4.  Ayarlama <xref:System.Windows.Forms.Button> denetimin **RowSpan** özelliğini **2**. Unutmayın <xref:System.Windows.Forms.Button> denetimi kapsayan ilk ve ikinci satırlar.  
  
5.  Ayarlama <xref:System.Windows.Forms.Button> denetimin **ColumnSpan** özelliğini **1**. Unutmayın <xref:System.Windows.Forms.Button> denetimi ilk sütuna taşır ve ilk ve ikinci satırlar yayılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableLayoutPanel Denetimi](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
