---
title: Fare yakalama
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741025"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="1013b-102">Windows Forms'ta Fare Yakalama</span><span class="sxs-lookup"><span data-stu-id="1013b-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="1013b-103">*Fare yakalama* , bir denetimin tüm fare girişi komutunu ne zaman aldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1013b-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="1013b-104">Bir denetim fareyi yakaladıktan sonra, işaretçinin sınırları içinde olup olmadığını fare girişi alır.</span><span class="sxs-lookup"><span data-stu-id="1013b-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="1013b-105">Fare yakalamayı ayarlama</span><span class="sxs-lookup"><span data-stu-id="1013b-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="1013b-106">Windows Forms fare, Kullanıcı denetimin üzerinde fare düğmesine bastığında denetim tarafından yakalanır ve Kullanıcı fare düğmesini bıraktığında denetim tarafından serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="1013b-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="1013b-107"><xref:System.Windows.Forms.Control> sınıfının <xref:System.Windows.Forms.Control.Capture%2A> özelliği, bir denetimin fareyi yakalamasının gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1013b-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="1013b-108">Bir denetimin fare yakalamayı kaybettiğini öğrenmek için <xref:System.Windows.Forms.Control.MouseCaptureChanged> olayını işleyin.</span><span class="sxs-lookup"><span data-stu-id="1013b-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="1013b-109">Yalnızca ön plan penceresi fareyi yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="1013b-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="1013b-110">Arka plan penceresi fare yakalamayı denediğinde, pencere yalnızca fare işaretçisi pencerenin görünür bölümü içindeyse oluşan fare olayları için ileti alır.</span><span class="sxs-lookup"><span data-stu-id="1013b-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="1013b-111">Ayrıca, ön plan penceresi fareyi yakalasa bile, Kullanıcı başka bir pencereye tıklayabilir ve bu da ön plana devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="1013b-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="1013b-112">Fare yakalandığında kısayol tuşları çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="1013b-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1013b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1013b-113">See also</span></span>

- [<span data-ttu-id="1013b-114">Bir Windows Forms Uygulamasında Fare Girdisi</span><span class="sxs-lookup"><span data-stu-id="1013b-114">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
