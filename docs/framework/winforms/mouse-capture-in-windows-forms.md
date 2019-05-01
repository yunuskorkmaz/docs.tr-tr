---
title: Windows Forms'ta Fare Yakalama
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 30432c6978f60cc9ad47d5df5dafc7aa45229f3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800964"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="fdb08-102">Windows Forms'ta Fare Yakalama</span><span class="sxs-lookup"><span data-stu-id="fdb08-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="fdb08-103">*Fare yakalama* denetim tüm fare girişi komutunu aldığında ifade eder.</span><span class="sxs-lookup"><span data-stu-id="fdb08-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="fdb08-104">Denetim fare yakalandı, işaretçi sınırlarının içinde olup olmadığını fare girişi alır.</span><span class="sxs-lookup"><span data-stu-id="fdb08-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="fdb08-105">Fare yakalama ayarlama</span><span class="sxs-lookup"><span data-stu-id="fdb08-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="fdb08-106">Windows Forms'ta fare kullanıcı bir denetimde bir fare düğmesi ve kullanıcı fare düğmesini bıraktığında fare denetim tarafından serbest denetim tarafından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="fdb08-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="fdb08-107"><xref:System.Windows.Forms.Control.Capture%2A> Özelliği <xref:System.Windows.Forms.Control> sınıfı bir denetim fareyi yakalanan olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdb08-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="fdb08-108">Ne zaman bir denetim fare yakalamayı kaybettiğinde belirlemek için tanıtıcı <xref:System.Windows.Forms.Control.MouseCaptureChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="fdb08-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="fdb08-109">Yalnızca ön plan penceresi fare yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdb08-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="fdb08-110">Bir arka plan penceresi fare yakalama girişiminde bulunduğunda, pencerenin fare işaretçisi penceresi görünür bölümünün içinde olduğunda gerçekleşen fare olayları için iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="fdb08-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="fdb08-111">Ön plan penceresi fare yakalandı olsa bile, kullanıcı hala başka bir pencere ön plana çerçevesinde tıklatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdb08-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="fdb08-112">Fare yakalandığında kısayol tuşu çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="fdb08-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb08-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdb08-113">See also</span></span>

- [<span data-ttu-id="fdb08-114">Bir Windows Forms Uygulamasında Fare Girdisi</span><span class="sxs-lookup"><span data-stu-id="fdb08-114">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
