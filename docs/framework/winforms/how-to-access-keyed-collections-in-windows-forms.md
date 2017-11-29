---
title: "Nasıl yapılır: Windows Forms'ta Anahtarlanmış Koleksiyonlara Erişim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2bca9b56f37c815bfa9f1520467ae0ae864c14ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Anahtarlanmış Koleksiyonlara Erişim
-   Anahtara göre tek tek koleksiyon öğeleri erişebilir. Bu işlevsellik, Windows Forms uygulamaları tarafından genellikle kullanılan birçok koleksiyon sınıfları için eklendi. Aşağıdaki listede erişilebilir anahtarlanmış koleksiyonlar sahip koleksiyon sınıfları bazıları gösterilir:  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Bir koleksiyondaki bir öğe ile ilişkilendirilen anahtar genellikle öğesi adıdır. Aşağıdaki yordamlar koleksiyon sınıfları ortak görevleri gerçekleştirmek için nasıl kullanılacağını gösterir.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Bulma ve denetim koleksiyonu içinde iç içe geçmiş denetim odağı vermek için  
  
-   Kullanım <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> ve <xref:System.Windows.Forms.Control.Focus%2A> yöntemleri bulup odaklanmak için Denetim adını belirtin.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Görüntüyü bir resim koleksiyonundaki erişmek için  
  
-   Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> özelliği erişmek istediğiniz görüntünün adını belirtin.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Sekme sayfası olarak seçilen sekmesini ayarlamak için  
  
-   Kullanım <xref:System.Windows.Forms.TabControl.SelectedTab%2A> özelliği ile birlikte <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> özelliği olarak seçilen sekmesini ayarlamak için sekme sayfası adını belirtin.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'a Başlarken](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Nasıl yapılır: Ekle veya Kaldır görüntüleri Windows Forms ImageList bileşeni](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
