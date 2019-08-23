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
ms.openlocfilehash: 7b7eac942a7e857ad731c0f77389e84aee287c08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952159"
---
# <a name="listview-control-overview-windows-forms"></a>ListView Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListView> denetim, simgeleri olan öğelerin bir listesini görüntüler. Windows Gezgini 'nin sağ bölmesi gibi bir kullanıcı arabirimi oluşturmak için bir liste görünümü kullanabilirsiniz. Denetimde dört görünüm modu vardır: LargeIcon, Smallıon, List ve details.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>ListView denetimiyle yapabilecekleriniz  
  
> [!NOTE]
> Ek bir görünüm modu, kutucuk yalnızca Windows XP ve Windows Server 2003 işletim sisteminde kullanılabilir. Daha fazla bilgi için [nasıl yapılır: Windows Forms ListView denetiminde](how-to-enable-tile-view-in-a-windows-forms-listview-control.md)kutucuk görünümünü etkinleştirin.  
  
 LargeIcon modu, öğe metninin yanında büyük simgeler görüntüler; Denetim yeterince büyükse öğeler birden çok sütunda görüntülenir. Smallıon modu, küçük simgeleri görüntülediği durumlar dışında aynıdır. Liste modu küçük simgeleri görüntüler, ancak her zaman tek bir sütunda bulunur. Ayrıntılar modu, öğeleri birden çok sütunda görüntüler. Ayrıntılar için bkz [. nasıl yapılır: Windows Forms ListView denetimine](how-to-add-columns-to-the-windows-forms-listview-control.md)sütun ekleyin. Görünüm modu, <xref:System.Windows.Forms.ListView.View%2A> özelliği tarafından belirlenir. Tüm görünüm modları görüntü listelerinden görüntüleri görüntüleyebilir. Ayrıntılar için bkz [. nasıl yapılır: Windows Forms ListView denetimi](how-to-display-icons-for-the-windows-forms-listview-control.md)için simgeler görüntüleyin.  
  
 Aşağıdaki tabloda bazı <xref:System.Windows.Forms.ListView> Üyeler ve bunların geçerli oldukları görünümler listelenmiştir.  
  
|ListView üyesi|Görüntüle|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A>özelliði|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A>özelliði|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>yöntemidir|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A>özelliði|<xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem>olay|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A>yöntemidir|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, veya<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A>yöntemidir|<xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A>yöntemidir|<xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A>özelliði|Dışındaki tüm görünümler<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A>özelliði|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A>özelliði|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, veya<xref:System.Windows.Forms.View.Tile>|  
  
 Denetimin anahtar özelliği <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.ListView.Items%2A>, denetim tarafından görünen öğeleri içeren. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Özelliği, denetimde seçili olan öğelerin bir koleksiyonunu içerir. Kullanıcı birden çok öğe seçebilir, örneğin, bir seferde birkaç öğeyi aynı anda başka bir denetime <xref:System.Windows.Forms.ListView.MultiSelect%2A> sürükleyip bırakmak için, özelliği olarak `true`ayarlanmışsa. <xref:System.Windows.Forms.ListView.CheckBoxes%2A> <xref:System.Windows.Forms.ListView> Özellik olarak`true`ayarlandıysa, denetimin öğelerin yanındaki onay kutularını gösterebilir.  
  
 Özelliği, kullanıcının listedeki bir öğeyi etkinleştirmek için yapması gereken eylem türünü belirler: <xref:System.Windows.Forms.ItemActivation.Standard>Seçenekler <xref:System.Windows.Forms.ItemActivation.OneClick>, ve <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ListView.Activation%2A> <xref:System.Windows.Forms.ItemActivation.OneClick>etkinleştirme, öğeyi etkinleştirmek için tek bir tıklama gerektirir. <xref:System.Windows.Forms.ItemActivation.TwoClick>etkinleştirme için kullanıcının öğeyi etkinleştirmek üzere çift tıklamak gerekir; tek bir tıklama öğesi metin rengini değiştirir. <xref:System.Windows.Forms.ItemActivation.Standard>etkinleştirme için kullanıcının bir öğeyi etkinleştirmek üzere çift tıklamak gerekir, ancak öğe görünümü değiştirmez.  
  
 <xref:System.Windows.Forms.ListView> Denetim Ayrıca, Windows XP platformunda gruplandırma, kutucuk görünümü ve ekleme işaretleri dahil olmak üzere görsel stilleri ve diğer özellikleri de destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- [ListView Denetimi](listview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle öğe ekleme ve kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimine sütun ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle alt öğeleri sütunlarda görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimindeki bir öğeyi seçin](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimindeki öğeleri gruplandırma](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetiminde ekleme Işareti görüntüleme](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Nasıl yapılır: ListView Denetimine arama yetenekleri ekleme](how-to-add-search-capabilities-to-a-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Nasıl yapılır: Windows Forms ile çok Bölbir Kullanıcı arabirimi oluşturma](how-to-create-a-multipane-user-interface-with-windows-forms.md)
