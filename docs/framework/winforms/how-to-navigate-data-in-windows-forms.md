---
title: "Nasıl yapılır: Windows Formlarında Verilerde Gezinme"
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
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d99d794164307cb22c5dfc89d6c9c227aa457a59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="0b14e-102">Nasıl yapılır: Windows Formlarında Verilerde Gezinme</span><span class="sxs-lookup"><span data-stu-id="0b14e-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="0b14e-103">Bir Windows uygulamasında bağlamak için bir veri kaynağındaki kayıtlarını gezinmek için en kolay yolu olan bir <xref:System.Windows.Forms.BindingSource> veri kaynağı ve ardından bağlama denetimlerine bileşen <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="0b14e-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="0b14e-104">Sonra yerleşik gezinti yöntemi kullanabileceğinizi <xref:System.Windows.Forms.BindingSource> böyle bir <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> ve <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b14e-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="0b14e-105">Bu yöntemleri kullanarak ayarlamak <xref:System.Windows.Forms.BindingSource.Position%2A> ve <xref:System.Windows.Forms.BindingSource.Current%2A> özelliklerini <xref:System.Windows.Forms.BindingSource> uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="0b14e-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="0b14e-106">Ayrıca bir öğeyi bulur ve ayarlayarak geçerli öğesi olarak ayarla <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0b14e-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="0b14e-107">Bir veri kaynağı konumu artırmak için</span><span class="sxs-lookup"><span data-stu-id="0b14e-107">To increment the position in a data source</span></span>  
  
1.  <span data-ttu-id="0b14e-108">Ayarlama <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği <xref:System.Windows.Forms.BindingSource> ilişkili verilerinizin kayıt konumuna gidin.</span><span class="sxs-lookup"><span data-stu-id="0b14e-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="0b14e-109">Aşağıdaki örnek kullanarak gösterilmektedir <xref:System.Windows.Forms.BindingSource.MoveNext%2A> yöntemi <xref:System.Windows.Forms.BindingSource> artırmak <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği zaman `nextButton` tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="0b14e-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="0b14e-110"><xref:System.Windows.Forms.BindingSource> İle ilişkili `Customers` tablo bir veri kümesinin `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="0b14e-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b14e-111">Ayarı <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği ilk veya son kaydı dışında bir değere neden olmaz hata olarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] konumu liste sınırları dışında bir değere ayarlamak izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0b14e-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="0b14e-112">Uygulamanızda ilk veya son kaydı ilerlemiş olup olmadığını bilmek önemlidir, veri öğesi sayısı aşacak olup olmadığını sınamak için mantık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0b14e-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="0b14e-113">Başlangıç ve bitiş geçirilen olup olmadığını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="0b14e-113">To check whether you have passed the end or beginning</span></span>  
  
1.  <span data-ttu-id="0b14e-114">İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.BindingSource.PositionChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="0b14e-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="0b14e-115">İşleyicisinde önerilen konum değerini gerçek veri öğesi sayısı aştı olup olmadığını sınayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b14e-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="0b14e-116">Aşağıdaki örnek, son veri öğesini ulaştınız olup olmadığını nasıl sınayabilirsiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b14e-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="0b14e-117">Son öğesi, varsa örnekte **sonraki** formundaki düğmesi devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="0b14e-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b14e-118">, Değişikliği kodda gezinme, liste, yeniden etkinleştirmeniz gerekir, unutmayın **sonraki** düğmesi, böylece kullanıcılar yeni liste tüm uzunluğu göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b14e-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="0b14e-119">Ayrıca, unutmayın, yukarıdaki <xref:System.Windows.Forms.BindingSource.PositionChanged> belirli olay <xref:System.Windows.Forms.BindingSource> kendi olay işleme yöntemi ile ilişkilendirilmesi gerekiyor çalıştığınız.</span><span class="sxs-lookup"><span data-stu-id="0b14e-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="0b14e-120">Aşağıdaki işleme için bir yöntem örneğidir <xref:System.Windows.Forms.BindingSource.PositionChanged> olay:</span><span class="sxs-lookup"><span data-stu-id="0b14e-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="0b14e-121">Bir öğeyi bulur ve geçerli öğesi olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0b14e-121">To find an item and set it as the current item</span></span>  
  
1.  <span data-ttu-id="0b14e-122">Geçerli öğesi olarak ayarlamak ister kaydı bulun.</span><span class="sxs-lookup"><span data-stu-id="0b14e-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="0b14e-123">Kullanarak bunu yapabilirsiniz <xref:System.Windows.Forms.BindingSource.Find%2A> yöntemi <xref:System.Windows.Forms.BindingSource>uygular, veri kaynağı, <xref:System.ComponentModel.IBindingList>.</span><span class="sxs-lookup"><span data-stu-id="0b14e-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="0b14e-124">Bazı örnekler veri kaynakları uygulayan <xref:System.ComponentModel.IBindingList> olan <xref:System.ComponentModel.BindingList%601> ve <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="0b14e-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0b14e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b14e-125">See Also</span></span>  
 [<span data-ttu-id="0b14e-126">Windows Forms Tarafından Desteklenen Veri Kaynakları</span><span class="sxs-lookup"><span data-stu-id="0b14e-126">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [<span data-ttu-id="0b14e-127">Windows Forms Veri Bağlamada Bildirimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0b14e-127">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="0b14e-128">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b14e-128">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="0b14e-129">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="0b14e-129">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
