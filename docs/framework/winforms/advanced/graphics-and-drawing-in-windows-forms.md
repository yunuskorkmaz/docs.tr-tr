---
title: "Windows Formlarında Grafikler ve Çizim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b2e8bde5d1c2904723282f03a815f17c5cc7622d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="c9351-102">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="c9351-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="c9351-103">Ortak dil çalışma zamanı Windows grafik cihaz arabirimi Gelişmiş uygulaması kullanır ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) olarak adlandırılan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9351-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="c9351-104">İle [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik oluşturma, metin çizme ve grafik görüntü nesneleri olarak değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="c9351-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c9351-105">Performans ve kullanım kolaylığı sunmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c9351-105"> is designed to offer performance and ease of use.</span></span> <span data-ttu-id="c9351-106">Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik görüntüleri Windows formlar ve denetimler üzerinde oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="c9351-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="c9351-107">Kullanamasanız [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] doğrudan Web formlarında grafik görüntüleri görüntü Web sunucusu denetimi ile görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9351-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="c9351-108">Bu bölümde, temel ilkeleri tanıtmak konuları bulur [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programlama.</span><span class="sxs-lookup"><span data-stu-id="c9351-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="c9351-109">Kapsamlı bir başvuru olarak tasarlanmamıştır karşın, bu bölümde hakkında bilgiler içerir <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, ve <xref:System.Drawing.Color> nesneleri ve bir metin çizim şekiller çizme gibi görevleri gerçekleştirmek açıklanmaktadır veya Görüntüleri görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="c9351-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="c9351-110">Daha fazla bilgi için bkz: [GDI + başvuru](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span><span class="sxs-lookup"><span data-stu-id="c9351-110">For more information, see [GDI+ Reference](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span></span>  
  
 <span data-ttu-id="c9351-111">İsterseniz hemen ve hemen kullanmaya başlamak için bkz: [grafik programlama ile çalışmaya başlama](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="c9351-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="c9351-112">Kod satırlarını, şekiller, metin ve Windows forms hakkında daha fazla bilgi çizmek için nasıl kullanılacağı hakkında konular bulunur.</span><span class="sxs-lookup"><span data-stu-id="c9351-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9351-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c9351-113">In This Section</span></span>  
 [<span data-ttu-id="c9351-114">Grafiklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="c9351-114">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 <span data-ttu-id="c9351-115">Grafik ilgili yönetilen sınıflar bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9351-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="c9351-116">GDI + yönetilen kodu hakkında</span><span class="sxs-lookup"><span data-stu-id="c9351-116">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 <span data-ttu-id="c9351-117">Yönetilen hakkında bilgi sağlar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c9351-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="c9351-118">Yönetilen grafik sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="c9351-118">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 <span data-ttu-id="c9351-119">Çeşitli kullanarak görevleri tamamlamak gösterilmiştir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] yönetilen sınıflar.</span><span class="sxs-lookup"><span data-stu-id="c9351-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c9351-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c9351-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="c9351-121">Erişim sağlayan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] temel grafik işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="c9351-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="c9351-122">Vektör grafikleri işlevselliği ve Gelişmiş iki boyutlu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9351-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="c9351-123">Sağlayan gelişmiş [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] görüntüleme işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="c9351-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="c9351-124">Sağlayan gelişmiş [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tipografi işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="c9351-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="c9351-125">Bu ad alanındaki sınıflar, yazı tipi koleksiyonları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9351-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="c9351-126">Yazdırma işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9351-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c9351-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c9351-127">Related Sections</span></span>  
 [<span data-ttu-id="c9351-128">Özel denetim boyama ve işleme</span><span class="sxs-lookup"><span data-stu-id="c9351-128">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="c9351-129">Boyama denetimleri için kod sağlamak nasıl ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9351-129">Details how to provide code for painting controls.</span></span>
