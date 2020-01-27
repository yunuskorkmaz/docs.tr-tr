---
title: ListView Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: 9308ff6646704d16b32669827a1f26bebf6958d8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745160"
---
# <a name="listview-control-overview-windows-forms"></a>ListView Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListView> denetim, simgeleri olan öğelerin bir listesini görüntüler. Windows Gezgini 'nin sağ bölmesi gibi bir kullanıcı arabirimi oluşturmak için bir liste görünümü kullanabilirsiniz. Denetimde dört görünüm modu vardır: LargeIcon, Smallıon, List ve details.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>ListView denetimiyle yapabilecekleriniz  
  
> [!NOTE]
> Ek bir görünüm modu, kutucuk yalnızca Windows XP ve Windows Server 2003 işletim sisteminde kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms ListView denetiminde kutucuk görünümünü etkinleştirme](how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 LargeIcon modu, öğe metninin yanında büyük simgeler görüntüler; Denetim yeterince büyükse öğeler birden çok sütunda görüntülenir. Smallıon modu, küçük simgeleri görüntülediği durumlar dışında aynıdır. Liste modu küçük simgeleri görüntüler, ancak her zaman tek bir sütunda bulunur. Ayrıntılar modu, öğeleri birden çok sütunda görüntüler. Ayrıntılar için bkz. [nasıl yapılır: sütunları Windows Forms ListView denetimine ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md). Görünüm modu <xref:System.Windows.Forms.ListView.View%2A> özelliği tarafından belirlenir. Tüm görünüm modları görüntü listelerinden görüntüleri görüntüleyebilir. Ayrıntılar için bkz. [nasıl yapılır: Windows Forms ListView denetimi Için simgeler görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 Aşağıdaki tabloda <xref:System.Windows.Forms.ListView> üyelerinden bazıları ve bunların geçerli oldukları görünümler listelenmiştir.  
  
|ListView üyesi|Görünüm|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> özelliği|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> özelliği|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> yöntemi|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> özelliği|<xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> olayı|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> yöntemi|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>veya <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> yöntemi|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> yöntemi|<xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> özelliği|<xref:System.Windows.Forms.View.List> dışındaki tüm görünümler|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> özelliği|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> özelliği|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>veya <xref:System.Windows.Forms.View.Tile>|  
  
 <xref:System.Windows.Forms.ListView> denetiminin anahtar özelliği, denetim tarafından görünen öğeleri içeren <xref:System.Windows.Forms.ListView.Items%2A>. <xref:System.Windows.Forms.ListView.SelectedItems%2A> özelliği, denetimde seçili olan öğelerin bir koleksiyonunu içerir. Kullanıcı birden çok öğe seçebilir, örneğin, <xref:System.Windows.Forms.ListView.MultiSelect%2A> özelliği `true`olarak ayarlanırsa, birkaç öğeyi bir seferde başka bir denetime sürükleyip bırakabilirsiniz. <xref:System.Windows.Forms.ListView.CheckBoxes%2A> özelliği `true`olarak ayarlandıysa <xref:System.Windows.Forms.ListView> denetim öğelerin yanındaki onay kutularını gösterebilir.  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> özelliği, kullanıcının listedeki bir öğeyi etkinleştirmek için yapması gereken eylem türünü belirler: seçenekler <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>ve <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick> etkinleştirme, öğeyi etkinleştirmek için tek bir tıklama gerektirir. <xref:System.Windows.Forms.ItemActivation.TwoClick> etkinleştirme için kullanıcının öğeyi etkinleştirmek üzere çift tıklamak gerekir; tek bir tıklama öğesi metin rengini değiştirir. <xref:System.Windows.Forms.ItemActivation.Standard> etkinleştirme, kullanıcının bir öğeyi etkinleştirmek için çift tıklamak istiyor ancak öğe görünümü değiştirmez.  
  
 <xref:System.Windows.Forms.ListView> denetim, Windows XP platformunda gruplandırma, kutucuk görünümü ve ekleme işaretleri de dahil olmak üzere görsel stilleri ve diğer özellikleri de destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- [ListView Denetimi](listview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme](how-to-add-search-capabilities-to-a-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Nasıl yapılır: Windows Forms ile Çok Bölmeli Kullanıcı Arabirimi Oluşturma](how-to-create-a-multipane-user-interface-with-windows-forms.md)
