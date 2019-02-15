---
title: 'Nasıl yapılır: Tasarımcı kullanarak Windows Forms ListView denetimi içinde öğeleri gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 964f2130c650d486bf8a20af96b74122b1450e05
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304433"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak Windows Forms ListView denetimi içinde öğeleri gruplandırma
Gruplandırma özelliğini de <xref:System.Windows.Forms.ListView> gruplarında öğe ilgili kümeleri görüntülemek, denetim olanağı sağlar. Bu grupları ekranda grup başlıklarını içeren yatay grup üstbilgileri tarafından ayrılır. Kullanabileceğiniz <xref:System.Windows.Forms.ListView> öğeleri alfabetik olarak tarih veya diğer bir mantıksal gruplama gruplandırarak büyük listeler daha kolay gezinme olmak için grupları. Aşağıdaki resimde, bazı gruplandırılmış öğeler gösterilir.  
  
 ![ListView grupları](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.ListView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
 Gruplandırma etkinleştirmek için önce bir veya daha fazla oluşturmalısınız <xref:System.Windows.Forms.ListViewGroup> Tasarımcısı'nda veya programlama yoluyla nesneleri. Bir grubu oluşturulduktan sonra öğeleri atayabilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi. Önceki işletim sistemlerinde herhangi bir kod gruplarına ilgili hiçbir etkisi yoktur ve grupları görüntülenmez. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Ekleme veya tasarımcıda grupları kaldırma  
  
1.  İçinde **özellikleri** penceresinde tıklayın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesinin yanındaki <xref:System.Windows.Forms.ListView.Groups%2A> özelliği.  
  
     **ListViewGroup Koleksiyonu Düzenleyicisi** görünür.  
  
2.  Bir grup eklemek için tıklatın **Ekle** düğmesi. Ardından, yeni grup özellikleri gibi ayarlayabilirsiniz <xref:System.Windows.Forms.ListViewGroup.Header%2A> ve <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> özellikleri. Bir grubu kaldırmak için onu seçin ve **Kaldır** düğmesi.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Öğeleri Tasarımcısı'nda gruplara atamak için  
  
1.  İçinde **özellikleri** penceresinde tıklayın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesinin yanındaki <xref:System.Windows.Forms.ListView.Items%2A> özelliği.  
  
     **ListViewItem Koleksiyonu Düzenleyicisi** görünür.  
  
2.  Yeni bir öğe eklemek için tıklatın **Ekle** düğmesi. Yeni öğenin özelliklerini aşağıdaki gibi ayarlayabilirsiniz <xref:System.Windows.Forms.ListViewItem.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri.  
  
3.  Seçin <xref:System.Windows.Forms.ListViewItem.Group%2A> özelliği ve aşağı açılan listeden bir grubu seçin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
