---
title: 'Nasıl yapılır: anahtarlı koleksiyonlara erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 717ba9cc8605da08701de1bd13d6bc6da1c9b758
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739618"
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
  
- Bulunacak ve odağa verilecek denetimin adını belirtmek için <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> ve <xref:System.Windows.Forms.Control.Focus%2A> yöntemlerini kullanın.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Görüntü koleksiyonundaki bir görüntüye erişmek için  
  
- Erişmek istediğiniz görüntünün adını belirtmek için <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> özelliğini kullanın.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Sekme sayfasını seçili sekme olarak ayarlamak için  
  
- Seçilen sekme olarak ayarlanacak sekme sayfasının adını belirtmek için, <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> özelliğiyle birlikte <xref:System.Windows.Forms.TabControl.SelectedTab%2A> özelliğini kullanın.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
- [Nasıl yapılır: Windows Forms ImageList Bileşeni ile Görüntü Ekleme veya Kaldırma](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
