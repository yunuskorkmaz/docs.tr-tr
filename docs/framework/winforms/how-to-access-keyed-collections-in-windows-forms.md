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
ms.openlocfilehash: a88e4766a1e774582bcd0356c9b6e77bc31f1960
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928522"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Anahtarlanmış Koleksiyonlara Erişim

- Tek tek koleksiyon öğelerine anahtara göre erişebilirsiniz. Bu işlevsellik, genellikle Windows Forms uygulamaları tarafından kullanılan birçok koleksiyon sınıfına eklenmiştir. Aşağıdaki listede, erişilebilir anahtarlı koleksiyonlara sahip bazı koleksiyon sınıfları gösterilmektedir:  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Bir koleksiyondaki öğeyle ilişkili anahtar genellikle öğenin adıdır. Aşağıdaki yordamlar, ortak görevleri gerçekleştirmek için koleksiyon sınıflarını nasıl kullanacağınızı gösterir.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Bir denetim koleksiyonundaki iç içe bir denetime odaklanmak ve odağı sağlamak için  
  
- Bulunacak ve odaklanmak <xref:System.Windows.Forms.Control.Focus%2A> üzere denetimin adını belirtmek için veyöntemlerinikullanın.<xref:System.Windows.Forms.Control.ControlCollection.Find%2A>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Görüntü koleksiyonundaki bir görüntüye erişmek için  
  
- Erişmek istediğiniz görüntünün adını belirtmek için özelliğinikullanın.<xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Sekme sayfasını seçili sekme olarak ayarlamak için  
  
- Seçili sekme olarak ayarlanacak sekme sayfasının <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> adını belirtmek için özelliğini özelliğiyle birlikte kullanın. <xref:System.Windows.Forms.TabControl.SelectedTab%2A>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
- [Nasıl yapılır: Windows Forms ImageList bileşeni ile görüntü ekleme veya kaldırma](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
