---
title: 'Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: 2049638998f7a8d099e14fab9c95384a49c67833
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528296"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a><span data-ttu-id="2756f-102">Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="2756f-102">How to: Add Search Capabilities to a ListView Control</span></span>
<span data-ttu-id="2756f-103">Büyük bir liste öğelerinin görmemeleri çalışırken, bir <xref:System.Windows.Forms.ListView> denetimi istediğiniz kullanıcıya arama özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="2756f-103">Oftentimes when working with a large list of items in a <xref:System.Windows.Forms.ListView> control, you want to offer search capabilities to the user.</span></span> <span data-ttu-id="2756f-104"><xref:System.Windows.Forms.ListView> Denetim iki farklı şekilde bu özellik sunar: eşleşen metni ve arama konumu.</span><span class="sxs-lookup"><span data-stu-id="2756f-104">The <xref:System.Windows.Forms.ListView> control offers this capability in two different ways: text matching and location searching.</span></span>  
  
 <span data-ttu-id="2756f-105"><xref:System.Windows.Forms.ListView.FindItemWithText%2A> Yöntemi sağlar, üzerinde bir metin araması gerçekleştirmek bir <xref:System.Windows.Forms.ListView> ayrıntıları veya liste görünümünde, verilen arama dizesi ve isteğe bağlı bir başlangıç ve bitiş dizini.</span><span class="sxs-lookup"><span data-stu-id="2756f-105">The <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method allows you to perform a text search on a <xref:System.Windows.Forms.ListView> in list or details view, given a search string and an optional starting and ending index.</span></span> <span data-ttu-id="2756f-106">Buna karşılık, <xref:System.Windows.Forms.ListView.FindNearestItem%2A> yöntemi sağlar, bir öğeyi bulmak bir <xref:System.Windows.Forms.ListView> simgesine veya bölmesi görünümünde, bir dizi x ve y koordinatları ve aramak için bir yön verilen.</span><span class="sxs-lookup"><span data-stu-id="2756f-106">In contrast, the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method allows you to find an item in a <xref:System.Windows.Forms.ListView> in icon or tile view, given a set of x- and y-coordinates and a direction to search.</span></span>  
  
### <a name="to-find-an-item-using-text"></a><span data-ttu-id="2756f-107">Metin kullanarak bir öğeyi bulmak için</span><span class="sxs-lookup"><span data-stu-id="2756f-107">To find an item using text</span></span>  
  
1.  <span data-ttu-id="2756f-108">Oluşturma bir <xref:System.Windows.Forms.ListView> ile <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.List>ve ardından doldurmak <xref:System.Windows.Forms.ListView> öğeleriyle.</span><span class="sxs-lookup"><span data-stu-id="2756f-108">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.ListView.View%2A> property set to <xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.List>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="2756f-109">Çağrı <xref:System.Windows.Forms.ListView.FindItemWithText%2A> yöntemi, bulmak istediğiniz öğenin metnini geçirme.</span><span class="sxs-lookup"><span data-stu-id="2756f-109">Call the <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method, passing the text of the item you would like to find.</span></span>  
  
3.  <span data-ttu-id="2756f-110">Aşağıdaki kod örneğinde nasıl temel oluşturulduğunu gösteren <xref:System.Windows.Forms.ListView>öğeler ile doldurulur ve metin girişi kullanıcı bir öğeyi listede bulmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2756f-110">The following code example demonstrates how to create a basic <xref:System.Windows.Forms.ListView>, populate it with items, and use text input from the user to find an item in the list.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a><span data-ttu-id="2756f-111">X ve y koordinatları kullanarak bir öğeyi bulmak için</span><span class="sxs-lookup"><span data-stu-id="2756f-111">To find an item using x- and y-coordinates</span></span>  
  
1.  <span data-ttu-id="2756f-112">Oluşturma bir <xref:System.Windows.Forms.ListView> ile <xref:System.Windows.Forms.View> özelliğini <xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>ve ardından doldurmak <xref:System.Windows.Forms.ListView> öğeleriyle.</span><span class="sxs-lookup"><span data-stu-id="2756f-112">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.View> property set to <xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="2756f-113">Çağrı <xref:System.Windows.Forms.ListView.FindNearestItem%2A> yöntemi, istenen x ve y-koordinatları ve aramak istediğiniz yönü geçirme.</span><span class="sxs-lookup"><span data-stu-id="2756f-113">Call the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method, passing the desired x- and y-coordinates and the direction you would like to search.</span></span>  
  
3.  <span data-ttu-id="2756f-114">Aşağıdaki kod örneği, temel bir simge oluşturulmaya gösterilmiştir <xref:System.Windows.Forms.ListView>, öğeleri ve yakalama doldurmak <xref:System.Windows.Forms.Control.MouseDown> yakın öğeyi yukarı yönde bulmak için olay.</span><span class="sxs-lookup"><span data-stu-id="2756f-114">The following code example demonstrates how to create a basic icon <xref:System.Windows.Forms.ListView>, populate it with items, and capture the <xref:System.Windows.Forms.Control.MouseDown> event to find the nearest item in the up direction.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2756f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2756f-115">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [<span data-ttu-id="2756f-116">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="2756f-116">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="2756f-117">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2756f-117">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="2756f-118">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="2756f-118">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
