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
ms.openlocfilehash: 8ceed741e72dae46f7f791b7564b7f5c38f82bc2
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664633"
---
# <a name="listview-control-overview-windows-forms"></a>ListView Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListView> denetim simgeler ile öğeler bir listesini görüntüler. Bir liste görünümü sağ bölme Windows Explorer'ın gibi bir kullanıcı arabirimi oluşturmak için kullanabilirsiniz. Denetim dört görünüm modu vardır: LargeIcon, SmallIcon, liste ve ayrıntılar.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>ListView denetimi ile yapabilecekleriniz  
  
> [!NOTE]
>  Ek görünüm modu, kutucuk, yalnızca Windows XP ve Windows Server 2003 işletim sistemi üzerinde kullanılabilir. Daha fazla bilgi için [nasıl yapılır: Döşeme görünümünü etkinleştirme bir Windows Forms ListView denetiminde](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 LargeIcon modu öğesi metnin yanında büyük simgeler görüntülüyor; Denetim yeterince büyük ise öğeleri birden çok sütunda görünür. Küçük simgeleri görüntüler SmallIcon modu aynı olmasıdır. Liste modu küçük simgeleri görüntüler, ancak her zaman tek bir sütunda olur. Ayrıntı Modu, birden çok sütunda öğeleri görüntüler. Ayrıntılar için bkz [nasıl yapılır: Sütunları Windows Forms ListView denetiminde ekleme](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md). Görünüm modu belirlenir <xref:System.Windows.Forms.ListView.View%2A> özelliği. Görüntüleme modlarına tüm görüntü listelerinden görüntüler görüntüleyebilirsiniz. Ayrıntılar için bkz [nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
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
  
 <xref:System.Windows.Forms.ListView> Denetimi ayrıca görsel stilleri ve diğer özelliklerin gruplandırma, kutucuk görünümü ve ekleme işaretleri dahil olmak üzere Windows XP platformunda destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ListView>
- [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetiminde bir öğe seçin](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir Windows Forms ListView denetimi içinde öğeleri gruplandırma](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir Windows Forms ListView denetiminde ekleme işareti görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir ListView denetimine arama yetenekleri ekleme](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Nasıl yapılır: Windows Forms ile çok bölmeli kullanıcı arabirimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
