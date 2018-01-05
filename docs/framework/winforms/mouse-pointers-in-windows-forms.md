---
title: "Windows Forms'ta Fare İşaretçileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aaca18bff265fafbb5bad26adfe2a8c490d85132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-pointers-in-windows-forms"></a><span data-ttu-id="f8df1-102">Windows Forms'ta Fare İşaretçileri</span><span class="sxs-lookup"><span data-stu-id="f8df1-102">Mouse Pointers in Windows Forms</span></span>
<span data-ttu-id="f8df1-103">Fare *işaretçi*, ekranında fareyle kullanıcı girişi için odak noktası belirten bir bit eşlem olduğundan, bazen imleci adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f8df1-103">The mouse *pointer*, which is sometimes referred to as the cursor, is a bitmap that specifies a focus point on the screen for user input with the mouse.</span></span> <span data-ttu-id="f8df1-104">Bu konu Windows Forms'ta fare işaretçisini genel bir bakış sağlar ve bazı değiştirebilir ve fare işaretçisini denetim yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8df1-104">This topic provides an overview of the mouse pointer in Windows Forms and describes some of the ways to modify and control the mouse pointer.</span></span>  
  
## <a name="accessing-the-mouse-pointer"></a><span data-ttu-id="f8df1-105">Fare işaretçisini erişme</span><span class="sxs-lookup"><span data-stu-id="f8df1-105">Accessing the Mouse Pointer</span></span>  
 <span data-ttu-id="f8df1-106">Fare işaretçisini tarafından temsil edilen <xref:System.Windows.Forms.Cursor> sınıfı ve her <xref:System.Windows.Forms.Control> sahip bir <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> denetleyen işaretçisi belirten özellik.</span><span class="sxs-lookup"><span data-stu-id="f8df1-106">The mouse pointer is represented by the <xref:System.Windows.Forms.Cursor> class, and each <xref:System.Windows.Forms.Control> has a <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> property that specifies the pointer for that control.</span></span> <span data-ttu-id="f8df1-107"><xref:System.Windows.Forms.Cursor> Sınıfı içeriyor gibi işaretçi tanımlayan özelliği <xref:System.Windows.Forms.Cursor.Position%2A> ve <xref:System.Windows.Forms.Cursor.HotSpot%2A> özellikleri ve işaretçi görünümünü gibi değiştirebilirsiniz yöntemleri <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, ve <xref:System.Windows.Forms.Cursor.DrawStretched%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f8df1-107">The <xref:System.Windows.Forms.Cursor> class contains properties that describe the pointer, such as the <xref:System.Windows.Forms.Cursor.Position%2A> and <xref:System.Windows.Forms.Cursor.HotSpot%2A> properties, and methods that can modify the appearance of the pointer, such as the <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, and <xref:System.Windows.Forms.Cursor.DrawStretched%2A> methods.</span></span>  
  
## <a name="controlling-the-mouse-pointer"></a><span data-ttu-id="f8df1-108">Fare işaretçisini denetleme</span><span class="sxs-lookup"><span data-stu-id="f8df1-108">Controlling the Mouse Pointer</span></span>  
 <span data-ttu-id="f8df1-109">Bazen, fare işaretçisini kullanılabilir veya fare konumunu değiştirme alanı sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8df1-109">Sometimes you may want to limit the area in which the mouse pointer can be used or change the position the mouse.</span></span> <span data-ttu-id="f8df1-110">Almak veya Fare kullanmada geçerli konumu ayarlamak <xref:System.Windows.Forms.Cursor.Position%2A> özelliği <xref:System.Windows.Forms.Cursor>.</span><span class="sxs-lookup"><span data-stu-id="f8df1-110">You can get or set the current location of the mouse using the <xref:System.Windows.Forms.Cursor.Position%2A> property of the <xref:System.Windows.Forms.Cursor>.</span></span> <span data-ttu-id="f8df1-111">Ayrıca, fare işaretçisini kullanılabilir alanı sınırlayabilirsiniz ayarı <xref:System.Windows.Forms.Cursor.Clip%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f8df1-111">In addition, you can limit the area the mouse pointer can be used be setting the <xref:System.Windows.Forms.Cursor.Clip%2A> property.</span></span> <span data-ttu-id="f8df1-112">Küçük, varsayılan olarak, tüm ekranı alanıdır.</span><span class="sxs-lookup"><span data-stu-id="f8df1-112">The clip area, by default, is the entire screen.</span></span>  
  
## <a name="changing-the-mouse-pointer"></a><span data-ttu-id="f8df1-113">Fare işaretçisini değiştirme</span><span class="sxs-lookup"><span data-stu-id="f8df1-113">Changing the Mouse Pointer</span></span>  
 <span data-ttu-id="f8df1-114">Fare işaretçisini değiştirme kullanıcıya geri bildirim sağlama önemli bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="f8df1-114">Changing the mouse pointer is an important way of providing feedback to the user.</span></span> <span data-ttu-id="f8df1-115">Örneğin, fare işaretçisini işleyiciler değiştirilebilir <xref:System.Windows.Forms.Control.MouseEnter> ve <xref:System.Windows.Forms.Control.MouseLeave> olayları hesaplamalar yaşanan kullanıcıya bildirmek için ve kullanıcı etkileşimi denetiminde sınırlamak için.</span><span class="sxs-lookup"><span data-stu-id="f8df1-115">For example, the mouse pointer can be modified in the handlers of the <xref:System.Windows.Forms.Control.MouseEnter> and <xref:System.Windows.Forms.Control.MouseLeave> events to tell the user that computations are occurring and to limit user interaction in the control.</span></span> <span data-ttu-id="f8df1-116">Bazı durumlarda, fare işaretçisini, uygulamanızı bir Sürükle ve bırak işlemi zaman söz konusu gibi sistem olayları nedeniyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f8df1-116">Sometimes, the mouse pointer will change because of system events, such as when your application is involved in a drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="f8df1-117">Fare işaretçisini değiştirmek için birincil ayarlayarak yoludur <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.Control.DefaultCursor%2A> yeni bir denetimin özelliğini <xref:System.Windows.Forms.Cursor>.</span><span class="sxs-lookup"><span data-stu-id="f8df1-117">The primary way to change the mouse pointer is by setting the <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.Control.DefaultCursor%2A> property of a control to a new <xref:System.Windows.Forms.Cursor>.</span></span> <span data-ttu-id="f8df1-118">Fare işaretçisini değiştirme örnekleri görmek için aşağıdaki kod örneğinde <xref:System.Windows.Forms.Cursor> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f8df1-118">For examples of changing the mouse pointer, see the code example in the <xref:System.Windows.Forms.Cursor> class.</span></span> <span data-ttu-id="f8df1-119">Ayrıca, <xref:System.Windows.Forms.Cursors> sınıfı kullanıma sunan bir dizi <xref:System.Windows.Forms.Cursor> işaretçileri el benzer bir işaretçi gibi birçok farklı türde nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f8df1-119">In addition, the <xref:System.Windows.Forms.Cursors> class exposes a set of <xref:System.Windows.Forms.Cursor> objects for many different types of pointers, such as a pointer that resembles a hand.</span></span> <span data-ttu-id="f8df1-120">Fare işaretçisini denetiminde olduğunda bir kum saati benzer, bekleme işaretçisi görüntülemek için kullanın <xref:System.Windows.Forms.Control.UseWaitCursor%2A> özelliği <xref:System.Windows.Forms.Control> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f8df1-120">To display the wait pointer, which resembles an hourglass, whenever the mouse pointer is on the control, use the <xref:System.Windows.Forms.Control.UseWaitCursor%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8df1-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8df1-121">See Also</span></span>  
 <xref:System.Windows.Forms.Cursor>  
 [<span data-ttu-id="f8df1-122">Bir Windows Forms Uygulamasında Fare Girdisi</span><span class="sxs-lookup"><span data-stu-id="f8df1-122">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="f8df1-123">Windows Forms'ta Sürükle ve Bırak İşlevi</span><span class="sxs-lookup"><span data-stu-id="f8df1-123">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
