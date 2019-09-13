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
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="5569c-102">Nasıl yapılır: Windows Forms'ta Anahtarlanmış Koleksiyonlara Erişim</span><span class="sxs-lookup"><span data-stu-id="5569c-102">How to: Access Keyed Collections in Windows Forms</span></span>

- <span data-ttu-id="5569c-103">Tek tek koleksiyon öğelerine anahtara göre erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5569c-103">You can access individual collection items by key.</span></span> <span data-ttu-id="5569c-104">Bu işlevsellik, genellikle Windows Forms uygulamaları tarafından kullanılan birçok koleksiyon sınıfına eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5569c-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="5569c-105">Aşağıdaki listede, erişilebilir anahtarlı koleksiyonlara sahip bazı koleksiyon sınıfları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5569c-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="5569c-106">Bir koleksiyondaki öğeyle ilişkili anahtar genellikle öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="5569c-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="5569c-107">Aşağıdaki yordamlar, ortak görevleri gerçekleştirmek için koleksiyon sınıflarını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5569c-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="5569c-108">Bir denetim koleksiyonundaki iç içe bir denetime odaklanmak ve odağı sağlamak için</span><span class="sxs-lookup"><span data-stu-id="5569c-108">To find and give focus to a nested control in a control collection</span></span>  
  
- <span data-ttu-id="5569c-109">Bulunacak ve odaklanmak <xref:System.Windows.Forms.Control.Focus%2A> üzere denetimin adını belirtmek için veyöntemlerinikullanın.<xref:System.Windows.Forms.Control.ControlCollection.Find%2A></span><span class="sxs-lookup"><span data-stu-id="5569c-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="5569c-110">Görüntü koleksiyonundaki bir görüntüye erişmek için</span><span class="sxs-lookup"><span data-stu-id="5569c-110">To access an image in an image collection</span></span>  
  
- <span data-ttu-id="5569c-111">Erişmek istediğiniz görüntünün adını belirtmek için özelliğinikullanın.<xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A></span><span class="sxs-lookup"><span data-stu-id="5569c-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="5569c-112">Sekme sayfasını seçili sekme olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5569c-112">To set a tab page as the selected tab</span></span>  
  
- <span data-ttu-id="5569c-113">Seçili sekme olarak ayarlanacak sekme sayfasının <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> adını belirtmek için özelliğini özelliğiyle birlikte kullanın. <xref:System.Windows.Forms.TabControl.SelectedTab%2A></span><span class="sxs-lookup"><span data-stu-id="5569c-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5569c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5569c-114">See also</span></span>

- [<span data-ttu-id="5569c-115">Windows Forms'a Başlarken</span><span class="sxs-lookup"><span data-stu-id="5569c-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="5569c-116">Nasıl yapılır: Windows Forms ImageList bileşeni ile görüntü ekleme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="5569c-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
