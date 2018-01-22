---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimindeki Öğeleri Gruplandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5e86ecdad66c9e58d691b18126c1fbf782e3130
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimindeki Öğeleri Gruplandırma
Gruplandırma özelliğini de <xref:System.Windows.Forms.ListView> denetimi ilgili öğeleri kümesi gruplarında görüntülemenize olanak sağlar. Bu gruplar ekranda grup başlıklarını içeren yatay grup üstbilgileri tarafından ayrılır. Kullanabileceğiniz <xref:System.Windows.Forms.ListView> öğeleri alfabetik olarak tarihe ya da diğer bir mantıksal gruplandırma göre gruplandırarak büyük listelerini daha kolay gezinme olmak için grupları. Aşağıdaki resimde gruplandırılmış bazı öğeler gösterilir.  
  
 ![ListView grupları](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ListView> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
 Gruplandırma etkinleştirmek için önce bir veya daha fazla oluşturmalısınız <xref:System.Windows.Forms.ListViewGroup> nesneleri Tasarımcısı'nda veya program aracılığıyla. Bir grubu oluşturulduktan sonra öğeleri atayabilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView>gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi. Önceki işletim sistemlerinde gruplarına ilgili herhangi bir kod hiçbir etkisi olmaz ve grupları görüntülenmez. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Eklemek veya Tasarımcısı'nda grupları kaldırmak için  
  
1.  İçinde **özellikleri** penceresinde tıklatın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesine <xref:System.Windows.Forms.ListView.Groups%2A> özelliği.  
  
     **ListViewGroup Koleksiyonu Düzenleyicisi** görüntülenir.  
  
2.  Bir grup eklemek için tıklatın **Ekle** düğmesi. Yeni grubu özelliklerini gibi daha sonra ayarlamak <xref:System.Windows.Forms.ListViewGroup.Header%2A> ve <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> özellikleri. Bir grubu kaldırmak için onu seçin ve tıklatın **kaldırmak** düğmesi.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Tasarımcıda gruplarına öğeleri atamak için  
  
1.  İçinde **özellikleri** penceresinde tıklatın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesine <xref:System.Windows.Forms.ListView.Items%2A> özelliği.  
  
     **ListViewItem Koleksiyonu Düzenleyicisi** görüntülenir.  
  
2.  Yeni bir öğe eklemek için tıklatın **Ekle** düğmesi. Yeni öğe özelliklerini gibi daha sonra ayarlamak <xref:System.Windows.Forms.ListViewItem.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri.  
  
3.  Seçin <xref:System.Windows.Forms.ListViewItem.Group%2A> özelliği ve aşağı açılan listeden bir grup seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Windows XP özellikleri ve Windows Forms denetimleri](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
