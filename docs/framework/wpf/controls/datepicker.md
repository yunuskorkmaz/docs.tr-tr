---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd5c7c796ee9d51a216368de3f3b04c10a5a3acd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker"></a><span data-ttu-id="dbe61-102">DatePicker</span><span class="sxs-lookup"><span data-stu-id="dbe61-102">DatePicker</span></span>
<span data-ttu-id="dbe61-103"><xref:System.Windows.Controls.DatePicker> Denetimi sağlar kullanıcıya bir metin alanı içine ya da yazarak veya bir açılan kullanarak bir tarih seçin <xref:System.Windows.Controls.Calendar> denetim.</span><span class="sxs-lookup"><span data-stu-id="dbe61-103">The <xref:System.Windows.Controls.DatePicker> control allows the user to select a date by either typing it into a text field or by using a drop-down <xref:System.Windows.Controls.Calendar> control.</span></span>  
  
 <span data-ttu-id="dbe61-104">Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="dbe61-104">The following illustration shows a <xref:System.Windows.Controls.DatePicker>.</span></span>  
  
 <span data-ttu-id="dbe61-105">![DatePicker denetim](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span><span class="sxs-lookup"><span data-stu-id="dbe61-105">![DatePicker control](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span></span>  
<span data-ttu-id="dbe61-106">DatePicker denetimi</span><span class="sxs-lookup"><span data-stu-id="dbe61-106">DatePicker Control</span></span>  
  
 <span data-ttu-id="dbe61-107">Çoğu bir <xref:System.Windows.Controls.DatePicker> denetimin özelliklerdir yerleşik yönetmek için <xref:System.Windows.Controls.Calendar>ve eşdeğer özelliğinde aynı işleve <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="dbe61-107">Many of a <xref:System.Windows.Controls.DatePicker> control's properties are for managing its built-in <xref:System.Windows.Controls.Calendar>, and function identically to the equivalent property in <xref:System.Windows.Controls.Calendar>.</span></span> <span data-ttu-id="dbe61-108">Özellikle, <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, ve <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> özellikleri işlev aynı için kendi <xref:System.Windows.Controls.Calendar> ortaklarınıza.</span><span class="sxs-lookup"><span data-stu-id="dbe61-108">In particular, the <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, and <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> properties function identically to their <xref:System.Windows.Controls.Calendar> counterparts.</span></span> <span data-ttu-id="dbe61-109">Daha fazla bilgi için bkz. <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="dbe61-109">For more information, see <xref:System.Windows.Controls.Calendar>.</span></span>  
  
 <span data-ttu-id="dbe61-110">Kullanıcılar, ayarlar doğrudan bir metin alanı, bir tarih yazabilirsiniz <xref:System.Windows.Controls.DatePicker.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="dbe61-110">Users can type a date directly into a text field, which sets the <xref:System.Windows.Controls.DatePicker.Text%2A> property.</span></span> <span data-ttu-id="dbe61-111">Varsa <xref:System.Windows.Controls.DatePicker> girilen dizesi geçerli bir tarih dönüştürülemiyor <xref:System.Windows.Controls.DatePicker.DateValidationError> olay harekete geçirilen.</span><span class="sxs-lookup"><span data-stu-id="dbe61-111">If the <xref:System.Windows.Controls.DatePicker> cannot convert the entered string to a valid date, the <xref:System.Windows.Controls.DatePicker.DateValidationError> event will be raised.</span></span> <span data-ttu-id="dbe61-112">Varsayılan olarak, bu ancak bir olay işleyicisi için bir özel durum oluşur <xref:System.Windows.Controls.DatePicker.DateValidationError> ayarlayabilirsiniz <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> özelliğine `false` ve ortaya çıkan gelen bir özel durum engeller.</span><span class="sxs-lookup"><span data-stu-id="dbe61-112">By default, this causes an exception, but an event handler for <xref:System.Windows.Controls.DatePicker.DateValidationError> can set the <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> property to `false` and prevent an exception from being raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe61-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbe61-113">See Also</span></span>  
 [<span data-ttu-id="dbe61-114">Denetimleri</span><span class="sxs-lookup"><span data-stu-id="dbe61-114">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="dbe61-115">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbe61-115">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
