---
title: Grafiklere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505326"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="8e43c-102">Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8e43c-102">Overview of Graphics</span></span>
<span data-ttu-id="8e43c-103">GDI + Microsoft Windows işletim sisteminin alt formları bir uygulama programlama arabirimi (API)'dır.</span><span class="sxs-lookup"><span data-stu-id="8e43c-103">GDI+ is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> <span data-ttu-id="8e43c-104">GDI + ekranları ve yazıcılar hakkında bilgi görüntülemek için sorumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="8e43c-104">GDI+ is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="8e43c-105">Adından da anlaşılacağı gibi GDI + GDI, önceki Windows sürümleriyle dahil grafik cihaz arabirimi geçmiştir.</span><span class="sxs-lookup"><span data-stu-id="8e43c-105">As its name suggests, GDI+ is the successor to GDI, the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="8e43c-106">Yönetilen sınıf arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e43c-106">Managed Class Interface</span></span>  
 <span data-ttu-id="8e43c-107">GDI + API sınıfları yönetilen kod olarak dağıtılan bir dizi aracılığıyla kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="8e43c-107">The GDI+ API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="8e43c-108">Bu sınıf kümesi adlı *yönetilen sınıf arabirimi* GDI +.</span><span class="sxs-lookup"><span data-stu-id="8e43c-108">This set of classes is called the *managed class interface* to GDI+.</span></span> <span data-ttu-id="8e43c-109">Aşağıdaki ad alanları, yönetilen sınıf arabirimi oluşturan olun:</span><span class="sxs-lookup"><span data-stu-id="8e43c-109">The following namespaces make up the managed class interface:</span></span>  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="8e43c-110">GDI +'gibi bir grafik cihaz arabirimi, bilgileri bir ekran veya yazıcı belirli görüntü cihazı ayrıntılarını merak gerek kalmadan görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e43c-110">With a Graphics Device Interface, such as GDI+, you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="8e43c-111">Programcı GDI + sınıfları tarafından sağlanan yöntemlere yapılan çağrılar yapar.</span><span class="sxs-lookup"><span data-stu-id="8e43c-111">The programmer makes calls to methods provided by GDI+ classes.</span></span> <span data-ttu-id="8e43c-112">Bu yöntemler, buna karşılık, belirli cihaz sürücülerini uygun çağrı yapmak.</span><span class="sxs-lookup"><span data-stu-id="8e43c-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> <span data-ttu-id="8e43c-113">GDI + grafik donanımının uygulamadan korunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e43c-113">GDI+ insulates the application from the graphics hardware.</span></span> <span data-ttu-id="8e43c-114">CİHAZDAN bağımsız uygulamalar oluşturmak için programcı sağlayan bu yalıtım var.</span><span class="sxs-lookup"><span data-stu-id="8e43c-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e43c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e43c-115">See also</span></span>

- [<span data-ttu-id="8e43c-116">Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8e43c-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
