---
title: Grafiklere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: 927fc327d9ad42cd3a99af207d04efbc520df8b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645697"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="c68eb-102">Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c68eb-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="c68eb-103">Microsoft Windows işletim sisteminin alt formları bir uygulama programlama arabirimi (API) olan.</span><span class="sxs-lookup"><span data-stu-id="c68eb-103">is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="c68eb-104">ekranlar ve yazıcılar hakkında bilgi görüntülemek için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c68eb-104">is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="c68eb-105">Adından da anlaşılacağı gibi [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] geçmiştir [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], önceki Windows sürümleriyle dahil grafik cihaz arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c68eb-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="c68eb-106">Yönetilen sınıf arabirimi</span><span class="sxs-lookup"><span data-stu-id="c68eb-106">Managed Class Interface</span></span>  
 <span data-ttu-id="c68eb-107">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API sınıfları yönetilen kod olarak dağıtılan bir dizi aracılığıyla gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c68eb-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="c68eb-108">Bu sınıf kümesi adlı *yönetilen sınıf arabirimi* için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c68eb-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="c68eb-109">Aşağıdaki ad alanları, yönetilen sınıf arabirimi oluşturan olun:</span><span class="sxs-lookup"><span data-stu-id="c68eb-109">The following namespaces make up the managed class interface:</span></span>  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="c68eb-110">Grafik cihaz arabirimi ile gibi [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], belirli bir görüntü ayrıntılarını merak zorunda kalmadan bir ekran veya yazıcı bilgileri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c68eb-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="c68eb-111">Programcı tarafından sağlanan yöntemlere yapılan çağrılar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c68eb-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="c68eb-112">Bu yöntemler, buna karşılık, belirli cihaz sürücülerini uygun çağrı yapmak.</span><span class="sxs-lookup"><span data-stu-id="c68eb-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="c68eb-113">grafik donanımının uygulamadan korunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c68eb-113">insulates the application from the graphics hardware.</span></span> <span data-ttu-id="c68eb-114">CİHAZDAN bağımsız uygulamalar oluşturmak için programcı sağlayan bu yalıtım var.</span><span class="sxs-lookup"><span data-stu-id="c68eb-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68eb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c68eb-115">See also</span></span>

- [<span data-ttu-id="c68eb-116">Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c68eb-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
