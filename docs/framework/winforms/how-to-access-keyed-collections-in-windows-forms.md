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
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="629db-102">Nasıl yapılır: Windows Forms'ta Anahtarlanmış Koleksiyonlara Erişim</span><span class="sxs-lookup"><span data-stu-id="629db-102">How to: Access Keyed Collections in Windows Forms</span></span>

- <span data-ttu-id="629db-103">Tek tek koleksiyon öğelerine anahtara göre erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="629db-103">You can access individual collection items by key.</span></span> <span data-ttu-id="629db-104">Bu işlevsellik, genellikle Windows Forms uygulamaları tarafından kullanılan birçok koleksiyon sınıfına eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="629db-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="629db-105">Aşağıdaki listede, erişilebilir anahtarlı koleksiyonlara sahip bazı koleksiyon sınıfları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="629db-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="629db-106">Bir koleksiyondaki öğeyle ilişkili anahtar genellikle öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="629db-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="629db-107">Aşağıdaki yordamlar, ortak görevleri gerçekleştirmek için koleksiyon sınıflarını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="629db-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="629db-108">Bir denetim koleksiyonundaki iç içe bir denetime odaklanmak ve odağı sağlamak için</span><span class="sxs-lookup"><span data-stu-id="629db-108">To find and give focus to a nested control in a control collection</span></span>  
  
- <span data-ttu-id="629db-109">Bulunacak ve odağa verilecek denetimin adını belirtmek için <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> ve <xref:System.Windows.Forms.Control.Focus%2A> yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="629db-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="629db-110">Görüntü koleksiyonundaki bir görüntüye erişmek için</span><span class="sxs-lookup"><span data-stu-id="629db-110">To access an image in an image collection</span></span>  
  
- <span data-ttu-id="629db-111">Erişmek istediğiniz görüntünün adını belirtmek için <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="629db-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="629db-112">Sekme sayfasını seçili sekme olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="629db-112">To set a tab page as the selected tab</span></span>  
  
- <span data-ttu-id="629db-113">Seçilen sekme olarak ayarlanacak sekme sayfasının adını belirtmek için, <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> özelliğiyle birlikte <xref:System.Windows.Forms.TabControl.SelectedTab%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="629db-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="629db-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="629db-114">See also</span></span>

- [<span data-ttu-id="629db-115">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="629db-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="629db-116">Nasıl yapılır: Windows Forms ImageList Bileşeni ile Görüntü Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="629db-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
