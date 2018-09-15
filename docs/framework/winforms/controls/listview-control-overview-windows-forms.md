---
title: ListView Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: ab2d0d9456f64f215ddbc0003833db1858f0ce1a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625470"
---
# <a name="listview-control-overview-windows-forms"></a>ListView Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListView> denetim simgeler ile öğeler bir listesini görüntüler. Bir liste görünümü sağ bölme Windows Explorer'ın gibi bir kullanıcı arabirimi oluşturmak için kullanabilirsiniz. Denetim dört görünüm modu vardır: LargeIcon, SmallIcon, liste ve ayrıntılar.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>ListView denetimi ile yapabilecekleriniz  
  
> [!NOTE]
>  Ek görünüm modu, kutucuk, yalnızca Windows XP ve Windows Server 2003 işletim sistemi üzerinde kullanılabilir. Daha fazla bilgi için [nasıl yapılır: Windows Forms ListView denetiminde döşeme görünümünü etkinleştirme](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 LargeIcon modu öğesi metnin yanında büyük simgeler görüntülüyor; Denetim yeterince büyük ise öğeleri birden çok sütunda görünür. Küçük simgeleri görüntüler SmallIcon modu aynı olmasıdır. Liste modu küçük simgeleri görüntüler, ancak her zaman tek bir sütunda olur. Ayrıntı Modu, birden çok sütunda öğeleri görüntüler. Ayrıntılar için bkz [nasıl yapılır: Windows Forms ListView denetimine sütunlar ekleme](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md). Görünüm modu belirlenir <xref:System.Windows.Forms.ListView.View%2A> özelliği. Görüntüleme modlarına tüm görüntü listelerinden görüntüler görüntüleyebilirsiniz. Ayrıntılar için bkz [nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 Aşağıdaki tablo bazı listeler <xref:System.Windows.Forms.ListView> üyeleri ve bunların geçerli görünümleri.  
  
|ListView üyesi|Görüntüle|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> Özelliği|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> Özelliği|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> Yöntemi|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> Özelliği|<xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> Olay|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> Yöntemi|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, veya <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> Yöntemi|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> Yöntemi|<xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> Özelliği|Dışındaki tüm görünümler <xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> Özelliği|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> Özelliği|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, veya <xref:System.Windows.Forms.View.Tile>|  
  
 Anahtar özelliği <xref:System.Windows.Forms.ListView> denetimi <xref:System.Windows.Forms.ListView.Items%2A>, denetimi tarafından görüntülenen öğeler içerir. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Özelliği şu anda denetiminde seçilen öğelerin bir koleksiyonunu içerir. Kullanıcının çeşitli öğeleri sürükleyip başka bir denetime bir zaman, örneğin, birden çok öğe seçebileceği <xref:System.Windows.Forms.ListView.MultiSelect%2A> özelliği `true`. <xref:System.Windows.Forms.ListView> Denetimi, öğelerin yanındaki onay kutularını görüntüleyebilir, varsa <xref:System.Windows.Forms.ListView.CheckBoxes%2A> özelliği `true`.  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> Özelliği belirler kullanıcı listesindeki bir öğeyi etkinleştirmek için ne tür bir eylem yapmanız gerekir: seçenekler <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, ve <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick> öğesini etkinleştirmek için tek tıklamayla etkinleştirme gerektirir. <xref:System.Windows.Forms.ItemActivation.TwoClick> etkinleştirme öğesini etkinleştirmek için çift gerektirir; tek tıklamayla öğe metin rengini değiştirir. <xref:System.Windows.Forms.ItemActivation.Standard> kullanıcının bir öğe etkinleştirmek için çift tıklayın. etkinleştirme gerektirir, ancak öğe görünüm değiştirmez.  
  
 <xref:System.Windows.Forms.ListView> Denetimi ayrıca görsel stilleri ve diğer özelliklerin gruplandırma, kutucuk görünümü ve ekleme işaretleri dahil olmak üzere Windows XP platformunda destekler. Daha fazla bilgi için [Windows XP özellikleri ve Windows Forms denetimleri](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).  
  
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
