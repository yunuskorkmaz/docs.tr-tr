---
title: "ListView Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b79fecb0a537f4c568b4a57e9ce2bfab8d8e1005
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="listview-control-overview-windows-forms"></a>ListView Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListView> denetim simgeler ile öğeler listesini görüntüler. Sağ bölmede Windows Explorer gibi bir kullanıcı arabirimi oluşturmak için bir liste görünümü kullanabilirsiniz. Denetim dört görünüm modu vardır: LargeIcon, SmallIcon, liste ve ayrıntıları.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>ListView denetimi ile yapabilecekleriniz  
  
> [!NOTE]
>  Bir ek görünüm modu kutucuğu, yalnızca Windows XP ve Windows Server 2003 işletim sistemi üzerinde kullanılabilir. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ListView denetiminde döşeme görünümünü etkinleştirme](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 LargeIcon modunda öğe metnin yanında büyük simgeler görüntüler; Denetim büyüklükte ise öğeleri birden çok sütun görünür. Küçük simgeler görüntüler dışında SmallIcon modunda aynıdır. Listesi modu küçük simgeler görüntüler, ancak her zaman tek bir sütunda olur. Ayrıntı Modu öğeleri birden çok sütun görüntüler. Ayrıntılar için bkz [nasıl yapılır: Windows Forms ListView denetimine Sütun Ekle](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md). Görünüm modu belirlenir <xref:System.Windows.Forms.ListView.View%2A> özelliği. Tüm görünüm modlarını görüntü listelerinden görüntüler görüntüleyebilirsiniz. Ayrıntılar için bkz [nasıl yapılır: Windows Forms ListView denetimi için ekran simgelerinin](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 Aşağıdaki tabloda bazı listeler <xref:System.Windows.Forms.ListView> üyeleri ve bunların geçerli görünümleri.  
  
|ListView üye|Görüntüle|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A>özelliği|<xref:System.Windows.Forms.View.SmallIcon>veya<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A>özelliği|<xref:System.Windows.Forms.View.SmallIcon>veya<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>yöntemi|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A>özelliği|<xref:System.Windows.Forms.View.Details>veya<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem>Olay|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A>yöntemi|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, veya<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A>yöntemi|<xref:System.Windows.Forms.View.SmallIcon>veya<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A>yöntemi|<xref:System.Windows.Forms.View.Details>veya<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A>özelliği|Dışındaki tüm görünümleri<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A>özelliği|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A>özelliği|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, veya<xref:System.Windows.Forms.View.Tile>|  
  
 Anahtar özelliği <xref:System.Windows.Forms.ListView> denetimi <xref:System.Windows.Forms.ListView.Items%2A>, denetimi tarafından görüntülenen öğeler içerir. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Özelliği şu anda denetim içinde seçilen öğeleri koleksiyonu içerir. Kullanıcı sürükleyip birden çok öğe aynı anda başka bir denetime, örneğin birden çok öğe seçebilirsiniz <xref:System.Windows.Forms.ListView.MultiSelect%2A> özelliği ayarlanmış `true`. <xref:System.Windows.Forms.ListView> Denetim, öğeleri yanındaki onay kutularını görüntüleyebilir, varsa <xref:System.Windows.Forms.ListView.CheckBoxes%2A> özelliği ayarlanmış `true`.  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> Özelliği, ne tür eylemi kullanıcı listesindeki bir öğeyi etkinleştirmek için gerçekleştirmeniz gereken belirler: seçenekler <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, ve <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick>etkinleştirme öğesini etkinleştirmek için tek bir tıklamayla gerektirir. <xref:System.Windows.Forms.ItemActivation.TwoClick>etkinleştirme öğesini etkinleştirmek için çift tıklayın kullanıcının gerektiren; tek bir tıklamayla öğesi metnin rengini değiştirir. <xref:System.Windows.Forms.ItemActivation.Standard>etkinleştirme öğeyi etkinleştirmek için çift tıklayın kullanıcının gerektiren, ancak öğe görünümünü değiştirmez.  
  
 <xref:System.Windows.Forms.ListView> Denetimi de görsel stiller ve kullanılabilen diğer özellikler gruplandırma, döşeme görünümünü ve ekleme işaretleri dahil olmak üzere Windows XP platformunda destekler. Daha fazla bilgi için bkz: [Windows XP özellikleri ve Windows Forms denetimleri](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 [Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Nasıl yapılır: Windows Forms ile Çok Bölmeli Kullanıcı Arabirimi Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
