---
title: "Nasıl yapılır: Windows Forms'ta Anahtarlanmış Koleksiyonlara Erişim"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 47bd0ff4eb649b4b32113a984f4aa99cd4afc0f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665273"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Anahtarlanmış Koleksiyonlara Erişim
- Anahtara göre tek tek koleksiyon öğelerine erişebilirsiniz. Bu işlev, genellikle Windows Forms uygulamaları tarafından kullanılan birçok koleksiyon sınıfları için eklendi. Aşağıdaki listede sahip erişilebilir anahtarlanmış koleksiyonlar koleksiyon sınıfları bazıları gösterilmektedir:  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Bir koleksiyondaki bir öğe ile ilişkili anahtar genellikle öğenin adıdır. Aşağıdaki yordamlar koleksiyon sınıfları ortak görevleri gerçekleştirmek için nasıl kullanılacağını gösterir.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Bulmak ve bir denetim koleksiyonu içindeki iç içe geçmiş bir denetime odaklanmak için  
  
- Kullanım <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> ve <xref:System.Windows.Forms.Control.Focus%2A> bulup odaklanmak için denetimin adını belirtmek için yöntemleri.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Görüntü koleksiyonu görüntüdeki erişmek için  
  
- Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> özelliği erişmek istediğiniz görüntünün adını belirtin.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Bir sekme sayfası seçili sekme ayarlamak için  
  
- Kullanım <xref:System.Windows.Forms.TabControl.SelectedTab%2A> özelliği ile birlikte <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> özelliği seçili sekme ayarlamak için sekmesinde sayfanın adını belirtin.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
- [Nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri eklemek veya kaldırmak](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
