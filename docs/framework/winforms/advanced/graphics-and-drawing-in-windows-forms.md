---
title: Windows Formlarında Grafikler ve Çizim
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 08f87436ade62bb54295b012a1c24dc177ea9667
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705434"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="fe3d2-102">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="fe3d2-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="fe3d2-103">Ortak dil çalışma zamanı kullanan Windows grafik cihaz arabirimi Gelişmiş uygulaması ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) olarak adlandırılan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe3d2-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="fe3d2-104">İle [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafikler oluşturun, metin çizme ve grafik görüntüleri nesneler olarak yönetmek.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="fe3d2-105">Performans ve kullanım kolaylığı sunmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-105">is designed to offer performance and ease of use.</span></span> <span data-ttu-id="fe3d2-106">Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik görüntüleri Windows formlar ve denetimler üzerinde oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="fe3d2-107">Kullanamasanız [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] doğrudan Web formlarında, grafik görüntüleri görüntü Web sunucusu denetimi ile görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="fe3d2-108">Bu bölümde, temelleri tanıtan konuları bulabilirsiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programlama.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="fe3d2-109">Kapsamlı bir referans olacak şekilde tasarlanmamıştır olsa da, bu bölüm hakkında bilgiler içerir <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, ve <xref:System.Drawing.Color> nesneleri ve şekiller, metin çizme çizim gibi görevleri gerçekleştirmek açıklanmaktadır veya Görüntüleri görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="fe3d2-110">Daha fazla bilgi için [GDI +'BAŞVURU](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="fe3d2-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="fe3d2-111">İsterseniz hemen ve hemen kullanmaya başlamak için bkz: [grafik programlama ile çalışmaya başlama](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="fe3d2-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="fe3d2-112">Kod satırları, şekiller, metin ve Windows forms hakkında daha fazla bilgi çizmek için kullanma hakkında konular bulunur.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe3d2-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fe3d2-113">In This Section</span></span>  
 [<span data-ttu-id="fe3d2-114">Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fe3d2-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="fe3d2-115">Grafikler ile ilgili yönetilen sınıflar için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="fe3d2-116">GDI+ Yönetilen Kodu Hakkında</span><span class="sxs-lookup"><span data-stu-id="fe3d2-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="fe3d2-117">Yönetilen hakkında bilgi sağlar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="fe3d2-118">Yönetilen Grafik Sınıflarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="fe3d2-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="fe3d2-119">Çeşitli kullanarak görevleri tamamlamak gösterilmiştir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] yönetilen sınıflar.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fe3d2-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="fe3d2-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="fe3d2-121">Erişim sağlayan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] temel grafik işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="fe3d2-122">Gelişmiş iki boyutlu sağlar ve vektör grafik işlevlerini.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="fe3d2-123">Sağlayan gelişmiş [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] görüntüleme işlevlerini.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="fe3d2-124">Sağlayan gelişmiş [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tipografi işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="fe3d2-125">Bu ad alanındaki sınıflar oluşturmak ve yazı tipi koleksiyonları kullanmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="fe3d2-126">Yazdırma işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fe3d2-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fe3d2-127">Related Sections</span></span>  
 [<span data-ttu-id="fe3d2-128">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="fe3d2-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="fe3d2-129">Boyama denetimleri için kodu sağlayabilir açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe3d2-129">Details how to provide code for painting controls.</span></span>
