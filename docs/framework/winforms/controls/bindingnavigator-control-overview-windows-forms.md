---
title: "BindingNavigator Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 932223a48500d8a0df5be6ae1ca08e1f333fc711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bindingnavigator-control-overview-windows-forms"></a><span data-ttu-id="769d7-102">BindingNavigator Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="769d7-102">BindingNavigator Control Overview (Windows Forms)</span></span>
<span data-ttu-id="769d7-103">Kullanabileceğiniz <xref:System.Windows.Forms.BindingNavigator> aramak ve bir Windows formunda veri değiştirmek kullanıcılar için standartlaştırılmış bir yol oluşturmak için denetim.</span><span class="sxs-lookup"><span data-stu-id="769d7-103">You can use the <xref:System.Windows.Forms.BindingNavigator> control to create a standardized means for users to search and change data on a Windows Form.</span></span> <span data-ttu-id="769d7-104">Sık kullandığınız <xref:System.Windows.Forms.BindingNavigator> ile <xref:System.Windows.Forms.BindingSource> bir form üzerinde veri kayıtlarda taşımak ve kayıtlarıyla etkileşim kullanıcılar etkinleştirmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="769d7-104">You frequently use <xref:System.Windows.Forms.BindingNavigator> with the <xref:System.Windows.Forms.BindingSource> component to enable users to move through data records on a form and interact with the records.</span></span>  
  
## <a name="how-the-bindingnavigator-works"></a><span data-ttu-id="769d7-105">BindingNavigator nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="769d7-105">How the BindingNavigator Works</span></span>  
 <span data-ttu-id="769d7-106"><xref:System.Windows.Forms.BindingNavigator> Denetim oluşan bir <xref:System.Windows.Forms.ToolStrip> bir dizi <xref:System.Windows.Forms.ToolStripItem> nesneleri için ortak veri ile ilgili eylemler çoğunu: veri ekleme, verileri siliniyor ve verilerine gezinme.</span><span class="sxs-lookup"><span data-stu-id="769d7-106">The <xref:System.Windows.Forms.BindingNavigator> control is composed of a <xref:System.Windows.Forms.ToolStrip> with a series of <xref:System.Windows.Forms.ToolStripItem> objects for most of the common data-related actions: adding data, deleting data, and navigating through data.</span></span> <span data-ttu-id="769d7-107">Varsayılan olarak, <xref:System.Windows.Forms.BindingNavigator> denetimi bu standart düğmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="769d7-107">By default, the <xref:System.Windows.Forms.BindingNavigator> control contains these standard buttons.</span></span> <span data-ttu-id="769d7-108">Aşağıdaki ekran görüntüsü gösterildiği <xref:System.Windows.Forms.BindingNavigator> bir form üzerinde denetim.</span><span class="sxs-lookup"><span data-stu-id="769d7-108">The following screen shot shows the <xref:System.Windows.Forms.BindingNavigator> control on a form.</span></span>  
  
 <span data-ttu-id="769d7-109">![BindingNavigator denetimi](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")</span><span class="sxs-lookup"><span data-stu-id="769d7-109">![BindingNavigator Control](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")</span></span>  
  
 <span data-ttu-id="769d7-110">Aşağıdaki tabloda denetimlerini listeler ve bunların işlevleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="769d7-110">The following table lists the controls and describes their functions.</span></span>  
  
|<span data-ttu-id="769d7-111">Denetim</span><span class="sxs-lookup"><span data-stu-id="769d7-111">Control</span></span>|<span data-ttu-id="769d7-112">İşlev</span><span class="sxs-lookup"><span data-stu-id="769d7-112">Function</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="769d7-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A>düğmesi</span><span class="sxs-lookup"><span data-stu-id="769d7-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> button</span></span>|<span data-ttu-id="769d7-114">Temel alınan veri kaynağında yeni bir satır ekler.</span><span class="sxs-lookup"><span data-stu-id="769d7-114">Inserts a new row into the underlying data source.</span></span>|  
|<span data-ttu-id="769d7-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A>düğmesi</span><span class="sxs-lookup"><span data-stu-id="769d7-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button</span></span>|<span data-ttu-id="769d7-116">Geçerli satırda temel alınan veri kaynağından siler.</span><span class="sxs-lookup"><span data-stu-id="769d7-116">Deletes the current row from the underlying data source.</span></span>|  
|<span data-ttu-id="769d7-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>düğmesi</span><span class="sxs-lookup"><span data-stu-id="769d7-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button</span></span>|<span data-ttu-id="769d7-118">Veri kaynağındaki ilk öğenin taşır.</span><span class="sxs-lookup"><span data-stu-id="769d7-118">Moves to the first item in the underlying data source.</span></span>|  
|<span data-ttu-id="769d7-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A>düğmesi</span><span class="sxs-lookup"><span data-stu-id="769d7-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> button</span></span>|<span data-ttu-id="769d7-120">Son temel alınan veri kaynağında öğesi taşır.</span><span class="sxs-lookup"><span data-stu-id="769d7-120">Moves to the last item in the underlying data source.</span></span>|  
|<span data-ttu-id="769d7-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A>düğmesi</span><span class="sxs-lookup"><span data-stu-id="769d7-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> button</span></span>|<span data-ttu-id="769d7-122">Temel alınan veri kaynağında bir sonraki öğeye taşır.</span><span class="sxs-lookup"><span data-stu-id="769d7-122">Moves to the next item in the underlying data source.</span></span>|  
|<span data-ttu-id="769d7-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A>düğmesi</span><span class="sxs-lookup"><span data-stu-id="769d7-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> button</span></span>|<span data-ttu-id="769d7-124">Temel alınan veri kaynağı önceki öğede taşır.</span><span class="sxs-lookup"><span data-stu-id="769d7-124">Moves to the previous item in the underlying data source.</span></span>|  
|<span data-ttu-id="769d7-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A>metin kutusu</span><span class="sxs-lookup"><span data-stu-id="769d7-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> text box</span></span>|<span data-ttu-id="769d7-126">Temel alınan veri kaynağı içindeki geçerli konumu döndürür.</span><span class="sxs-lookup"><span data-stu-id="769d7-126">Returns the current position within the underlying data source.</span></span>|  
|<span data-ttu-id="769d7-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A>metin kutusu</span><span class="sxs-lookup"><span data-stu-id="769d7-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A> text box</span></span>|<span data-ttu-id="769d7-128">Temel alınan veri kaynağında toplam öğe sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="769d7-128">Returns the total number of items in the underlying data source.</span></span>|  
  
 <span data-ttu-id="769d7-129">Bu koleksiyondaki her denetim için karşılık gelen bir üyesi yok <xref:System.Windows.Forms.BindingSource> program aracılığıyla aynı işlevselliği sunar bileşeni.</span><span class="sxs-lookup"><span data-stu-id="769d7-129">For each control in this collection, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically provides the same functionality.</span></span> <span data-ttu-id="769d7-130">Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemi <xref:System.Windows.Forms.BindingSource> bileşeni <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemi ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="769d7-130">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span>  
  
 <span data-ttu-id="769d7-131">Varsayılan düğmeleri uygulamanız için uygun değilse ya da diğer işlevleri türlerini desteklemek için ek düğmeler ihtiyacınız varsa, kendi sağlayabilirsiniz <xref:System.Windows.Forms.ToolStrip> düğmeler.</span><span class="sxs-lookup"><span data-stu-id="769d7-131">If the default buttons are not suited to your application, or if you require additional buttons to support other types of functionality, you can supply your own <xref:System.Windows.Forms.ToolStrip> buttons.</span></span> <span data-ttu-id="769d7-132">Ayrıca bkz. [nasıl yapılır: yükleme, kaydetme ve ekleme İptal düğmeleri Windows Forms BindingNavigator denetimi](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="769d7-132">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769d7-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="769d7-133">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="769d7-134">BindingNavigator denetimi</span><span class="sxs-lookup"><span data-stu-id="769d7-134">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
