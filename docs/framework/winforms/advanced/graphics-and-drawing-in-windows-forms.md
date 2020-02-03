---
title: Grafikler ve çizim
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746407"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="a619c-102">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="a619c-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="a619c-103">Ortak dil çalışma zamanı, GDI+ adlı Windows Grafik Cihaz Arabirimi (GDI) gelişmiş uygulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a619c-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="a619c-104">GDI+ ile grafik oluşturabilir, metin çizebilir ve grafik görüntülerini nesne olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a619c-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="a619c-105">GDI+, performans ve kullanım kolaylığı sunacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a619c-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="a619c-106">Windows Forms ve denetimlerinde grafik görüntülerini işlemek için GDI+ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a619c-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="a619c-107">Doğrudan Web Forms üzerinde GDI+ kullanamazsınız, ancak görüntü Web sunucusu denetimi aracılığıyla grafik görüntüleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a619c-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="a619c-108">Bu bölümde, GDI+ programlama temellerini ortaya çıkaracak konuları bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a619c-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="a619c-109">Kapsamlı bir başvuru olmasını amaçlanmamış olsa da, bu bölüm <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>ve <xref:System.Drawing.Color> nesneleri hakkında bilgiler içerir ve bu görevlerin, şekil çizme, metin çizme veya görüntü görüntüleme gibi görevleri nasıl gerçekleştirebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="a619c-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="a619c-110">Daha fazla bilgi için bkz. [GDI+ başvurusu](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="a619c-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="a619c-111">Hızlı bir başlangıç yapmak ve hemen başlamak istiyorsanız bkz. [Grafik programlamaya Başlarken](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="a619c-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="a619c-112">Windows Forms 'ta çizgi, şekil, metin ve daha fazlasını çizmek için kodun nasıl kullanılacağına ilişkin konular içerir.</span><span class="sxs-lookup"><span data-stu-id="a619c-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a619c-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a619c-113">In This Section</span></span>  
 [<span data-ttu-id="a619c-114">Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a619c-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="a619c-115">Grafiklerle ilgili yönetilen sınıflara bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="a619c-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="a619c-116">GDI+ Yönetilen Kodu Hakkında</span><span class="sxs-lookup"><span data-stu-id="a619c-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="a619c-117">Yönetilen GDI+ sınıfları hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a619c-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="a619c-118">Yönetilen Grafik Sınıflarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a619c-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="a619c-119">GDI+ Yönetilen sınıfları kullanarak çeşitli görevlerin nasıl tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a619c-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a619c-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a619c-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="a619c-121">GDI+ temel grafik işlevselliğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a619c-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="a619c-122">Gelişmiş iki boyutlu ve vektör grafik işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a619c-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="a619c-123">Gelişmiş GDI+ görüntüleme işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a619c-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="a619c-124">Gelişmiş GDI+ tipografi işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a619c-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="a619c-125">Bu ad alanındaki sınıflar, yazı tipi koleksiyonları oluşturmak ve kullanmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a619c-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="a619c-126">Yazdırma işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a619c-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a619c-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a619c-127">Related Sections</span></span>  
 [<span data-ttu-id="a619c-128">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="a619c-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="a619c-129">Boyama denetimleri için kod sağlama hakkında ayrıntılı bilgi.</span><span class="sxs-lookup"><span data-stu-id="a619c-129">Details how to provide code for painting controls.</span></span>
