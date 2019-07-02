---
title: Windows Formlarında Grafikler ve Çizim
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505546"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="bbfb1-102">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="bbfb1-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="bbfb1-103">Ortak dil çalışma zamanı, Gelişmiş bir uygulaması, Windows grafik cihaz arabirimi (GDI +'OLARAK adlandırılan GDI) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="bbfb1-104">GDI + ile grafikler oluşturabilir, metin çizme ve grafik görüntüleri nesneler olarak yönetmek.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="bbfb1-105">GDI +'da performans ve kullanım kolaylığı sunmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="bbfb1-106">Windows formlar ve denetimler grafik görüntülerinde işlenecek GDI +'da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="bbfb1-107">GDI +'da doğrudan Web formlarında kullanamasanız, grafik görüntüleri görüntü Web sunucusu denetimi ile görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="bbfb1-108">Bu bölümde, GDI + programlamanın temellerini tanıtan konuları bulur.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="bbfb1-109">Kapsamlı bir referans olacak şekilde tasarlanmamıştır olsa da, bu bölüm hakkında bilgiler içerir <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, ve <xref:System.Drawing.Color> nesneleri ve şekiller, metin çizme çizim gibi görevleri gerçekleştirmek açıklanmaktadır veya Görüntüleri görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="bbfb1-110">Daha fazla bilgi için [GDI +'BAŞVURU](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="bbfb1-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="bbfb1-111">İsterseniz hemen ve hemen kullanmaya başlamak için bkz: [grafik programlama ile çalışmaya başlama](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="bbfb1-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="bbfb1-112">Kod satırları, şekiller, metin ve Windows forms hakkında daha fazla bilgi çizmek için kullanma hakkında konular bulunur.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bbfb1-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bbfb1-113">In This Section</span></span>  
 [<span data-ttu-id="bbfb1-114">Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bbfb1-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="bbfb1-115">Grafikler ile ilgili yönetilen sınıflar için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="bbfb1-116">GDI+ Yönetilen Kodu Hakkında</span><span class="sxs-lookup"><span data-stu-id="bbfb1-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="bbfb1-117">Yönetilen GDI + sınıflar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="bbfb1-118">Yönetilen Grafik Sınıflarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbfb1-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="bbfb1-119">Nasıl için tam çeşitli görevleri kullanarak GDI + yönetilen sınıflar gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bbfb1-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bbfb1-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="bbfb1-121">GDI + grafik temel işlevlerini erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="bbfb1-122">Gelişmiş iki boyutlu sağlar ve vektör grafik işlevlerini.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="bbfb1-123">Gelişmiş GDI görüntüleme işlevlerini + sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="bbfb1-124">Gelişmiş GDI + tipografi işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="bbfb1-125">Bu ad alanındaki sınıflar oluşturmak ve yazı tipi koleksiyonları kullanmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="bbfb1-126">Yazdırma işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bbfb1-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bbfb1-127">Related Sections</span></span>  
 [<span data-ttu-id="bbfb1-128">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="bbfb1-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="bbfb1-129">Boyama denetimleri için kodu sağlayabilir açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbfb1-129">Details how to provide code for painting controls.</span></span>
