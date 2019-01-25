---
title: "Nasıl yapılır: Koleksiyonları Windows Forms'ta anahtarlanmış erişim"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 0071e3cc3ae2576bed8a7111fc2a120ea3a113c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676321"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="b2756-102">Nasıl yapılır: Koleksiyonları Windows Forms'ta anahtarlanmış erişim</span><span class="sxs-lookup"><span data-stu-id="b2756-102">How to: Access Keyed Collections in Windows Forms</span></span>
-   <span data-ttu-id="b2756-103">Anahtara göre tek tek koleksiyon öğelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2756-103">You can access individual collection items by key.</span></span> <span data-ttu-id="b2756-104">Bu işlev, genellikle Windows Forms uygulamaları tarafından kullanılan birçok koleksiyon sınıfları için eklendi.</span><span class="sxs-lookup"><span data-stu-id="b2756-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="b2756-105">Aşağıdaki listede sahip erişilebilir anahtarlanmış koleksiyonlar koleksiyon sınıfları bazıları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b2756-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="b2756-106">Bir koleksiyondaki bir öğe ile ilişkili anahtar genellikle öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="b2756-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="b2756-107">Aşağıdaki yordamlar koleksiyon sınıfları ortak görevleri gerçekleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2756-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="b2756-108">Bulmak ve bir denetim koleksiyonu içindeki iç içe geçmiş bir denetime odaklanmak için</span><span class="sxs-lookup"><span data-stu-id="b2756-108">To find and give focus to a nested control in a control collection</span></span>  
  
-   <span data-ttu-id="b2756-109">Kullanım <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> ve <xref:System.Windows.Forms.Control.Focus%2A> bulup odaklanmak için denetimin adını belirtmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b2756-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="b2756-110">Görüntü koleksiyonu görüntüdeki erişmek için</span><span class="sxs-lookup"><span data-stu-id="b2756-110">To access an image in an image collection</span></span>  
  
-   <span data-ttu-id="b2756-111">Kullanım <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> özelliği erişmek istediğiniz görüntünün adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b2756-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="b2756-112">Bir sekme sayfası seçili sekme ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b2756-112">To set a tab page as the selected tab</span></span>  
  
-   <span data-ttu-id="b2756-113">Kullanım <xref:System.Windows.Forms.TabControl.SelectedTab%2A> özelliği ile birlikte <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> özelliği seçili sekme ayarlamak için sekmesinde sayfanın adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b2756-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b2756-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2756-114">See also</span></span>
- [<span data-ttu-id="b2756-115">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="b2756-115">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
- [<span data-ttu-id="b2756-116">Nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri eklemek veya kaldırmak</span><span class="sxs-lookup"><span data-stu-id="b2756-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
