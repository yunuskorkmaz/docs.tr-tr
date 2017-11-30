---
title: "Windows Forms Koordinatları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ecb47efdd69730350cf98e1c7b1e49150ad324d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-coordinates"></a><span data-ttu-id="ab890-102">Windows Forms Koordinatları</span><span class="sxs-lookup"><span data-stu-id="ab890-102">Windows Forms Coordinates</span></span>
<span data-ttu-id="ab890-103">Bir Windows formunda koordinat sistemi aygıt koordinatlarına göre ve temel ölçü Windows Forms'ta çizerken (genellikle piksel) cihaz birimdir.</span><span class="sxs-lookup"><span data-stu-id="ab890-103">The coordinate system for a Windows Form is based on device coordinates, and the basic unit of measure when drawing in Windows Forms is the device unit (typically, the pixel).</span></span> <span data-ttu-id="ab890-104">Ekran noktalarında x ve y koordinatını çiftlerinden sağa ve üstten alta artırma y koordinatları artırma x koordinatları ile açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab890-104">Points on the screen are described by x- and y-coordinate pairs, with the x-coordinates increasing to the right and the y-coordinates increasing from top to bottom.</span></span> <span data-ttu-id="ab890-105">Başlangıç ekranı göreli konumunu ekran veya istemci koordinatları olup belirtiyorsanız bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="ab890-105">The location of the origin, relative to the screen, will vary depending on whether you are specifying screen or client coordinates.</span></span>  
  
## <a name="screen-coordinates"></a><span data-ttu-id="ab890-106">Ekran koordinatları</span><span class="sxs-lookup"><span data-stu-id="ab890-106">Screen Coordinates</span></span>  
 <span data-ttu-id="ab890-107">Bir Windows Forms uygulaması ekran koordinatları ekranda bir pencere konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab890-107">A Windows Forms application specifies the position of a window on the screen in screen coordinates.</span></span> <span data-ttu-id="ab890-108">Ekran koordinatları için kaynak ekranın sol üst köşesinde ' dir.</span><span class="sxs-lookup"><span data-stu-id="ab890-108">For screen coordinates, the origin is the upper-left corner of the screen.</span></span> <span data-ttu-id="ab890-109">Pencereyi tam konumunu genellikle tarafından açıklanan bir <xref:System.Drawing.Rectangle> penceresinin sol üst ve sağ alt köşe tanımlayan iki zaman noktası ekran koordinatları içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="ab890-109">The full position of a window is often described by a <xref:System.Drawing.Rectangle> structure containing the screen coordinates of two points that define the upper-left and lower-right corners of the window.</span></span>  
  
## <a name="client-coordinates"></a><span data-ttu-id="ab890-110">İstemci koordinatları</span><span class="sxs-lookup"><span data-stu-id="ab890-110">Client Coordinates</span></span>  
 <span data-ttu-id="ab890-111">Bir Windows Forms uygulaması, bir form veya istemci koordinatları kullanarak denetim noktaları konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab890-111">A Windows Forms application specifies the position of points in a form or control using client coordinates.</span></span> <span data-ttu-id="ab890-112">İstemci koordinatları başlangıç denetim veya formun istemci alanını sol üst köşesindeki ' dir.</span><span class="sxs-lookup"><span data-stu-id="ab890-112">The origin for client coordinates is the upper-left corner of the client area of the control or form.</span></span> <span data-ttu-id="ab890-113">İstemci koordinatları bir form veya form veya denetim ekranında konumunu bağımsız olarak denetim çizerken uygulama tutarlı koordinat değerleri kullanabilirsiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="ab890-113">Client coordinates ensure that an application can use consistent coordinate values while drawing in a form or control, regardless of the position of the form or control on the screen.</span></span>  
  
 <span data-ttu-id="ab890-114">İstemci alanını boyutlarını da tarafından açıklanan bir <xref:System.Drawing.Rectangle> alan için istemci koordinatları içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="ab890-114">The dimensions of the client area are also described by a <xref:System.Drawing.Rectangle> structure that contains client coordinates for the area.</span></span> <span data-ttu-id="ab890-115">Sağ alt koordinat dışlanan sırada her durumda, istemci alanında dikdörtgen sol üst koordinatını dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="ab890-115">In all cases, the upper-left coordinate of the rectangle is included in the client area, while the lower-right coordinate is excluded.</span></span> <span data-ttu-id="ab890-116">Grafik işlemleri istemci alanını alt ve sağ kenarlarının dahil etmeyin.</span><span class="sxs-lookup"><span data-stu-id="ab890-116">Graphics operations do not include the right and lower edges of a client area.</span></span> <span data-ttu-id="ab890-117">Örneğin <xref:System.Drawing.Graphics.FillRectangle%2A> yöntemi belirtilen dikdörtgenin alt ve sağ kenar doldurur, ancak bu kenarları dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="ab890-117">For example the <xref:System.Drawing.Graphics.FillRectangle%2A> method will fill up to the right and lower edge of the specified rectangle, but will not include these edges.</span></span>  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a><span data-ttu-id="ab890-118">Koordinat türünden eşleme</span><span class="sxs-lookup"><span data-stu-id="ab890-118">Mapping From One Type of Coordinate to Another</span></span>  
 <span data-ttu-id="ab890-119">Bazen, ekran koordinatları istemci koordinatları eşleme gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ab890-119">Occasionally, you may need to map from screen coordinates to client coordinates.</span></span> <span data-ttu-id="ab890-120">Bunu kolayca kullanarak gerçekleştirebilirsiniz <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> yöntemleri kullanılabilir <xref:System.Windows.Forms.Control> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ab890-120">You can easily accomplish this by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available in the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="ab890-121">Örneğin, <xref:System.Windows.Forms.Control.MousePosition%2A> özelliği <xref:System.Windows.Forms.Control> ekran koordinatları olarak bildirdi ancak bu istemci koordinatları dönüştürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab890-121">For example, the <xref:System.Windows.Forms.Control.MousePosition%2A> property of <xref:System.Windows.Forms.Control> is reported in screen coordinates, but you may want to convert these to client coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab890-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab890-122">See Also</span></span>  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
