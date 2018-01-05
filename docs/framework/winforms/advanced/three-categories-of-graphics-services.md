---
title: "Üç Grafik Hizmeti Kategorisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 305ffae04b6f1ddb94081f8a6ee334f8195caba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="three-categories-of-graphics-services"></a><span data-ttu-id="915c3-102">Üç Grafik Hizmeti Kategorisi</span><span class="sxs-lookup"><span data-stu-id="915c3-102">Three Categories of Graphics Services</span></span>
<span data-ttu-id="915c3-103">Windows Forms'ta grafik teklifleri aşağıdaki üç ana kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="915c3-103">The graphics offerings in Windows Forms fall into the following three broad categories:</span></span>  
  
-   <span data-ttu-id="915c3-104">İki boyutlu (2-D) vektör grafikleri</span><span class="sxs-lookup"><span data-stu-id="915c3-104">Two-dimensional (2-D) vector graphics</span></span>  
  
-   <span data-ttu-id="915c3-105">Görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="915c3-105">Imaging</span></span>  
  
-   <span data-ttu-id="915c3-106">Tipografi</span><span class="sxs-lookup"><span data-stu-id="915c3-106">Typography</span></span>  
  
## <a name="2-d-vector-graphics"></a><span data-ttu-id="915c3-107">2B vektör grafikleri</span><span class="sxs-lookup"><span data-stu-id="915c3-107">2-D Vector Graphics</span></span>  
 <span data-ttu-id="915c3-108">İki boyutlu vektör grafikleri temelleri; yine de uygun istiyor musunuz? çizgiler, eğriler ve şekiller gibi; Bu, koordinat sistemi noktalarında kümesi tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="915c3-108">Two-dimensional vector graphics are primitives; such as lines, curves, and figures; that are specified by sets of points on a coordinate system.</span></span> <span data-ttu-id="915c3-109">Örneğin, bir çizgide kendi iki uç noktaları tarafından belirtilir ve bir dikdörtgen konumu, sol üst köşe ve genişlik ve yükseklik vermiş numaraları çifti vermiş bir noktası tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="915c3-109">For example, a straight line is specified by its two endpoints, and a rectangle is specified by a point giving the location of its upper-left corner and a pair of numbers giving its width and height.</span></span> <span data-ttu-id="915c3-110">Basit bir yol düz çizgilerle bağlı noktalar dizisi belirtilir.</span><span class="sxs-lookup"><span data-stu-id="915c3-110">A simple path is specified by an array of points that are connected by straight lines.</span></span> <span data-ttu-id="915c3-111">Bir Bézier eğrisi dört denetim noktaları tarafından belirtilen karmaşık bir eğri ' dir.</span><span class="sxs-lookup"><span data-stu-id="915c3-111">A Bézier spline is a sophisticated curve specified by four control points.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="915c3-112">sınıfları ve temelleri hakkında bilgi depolamak yapıları, temelleri nasıl düzenleneceği hakkında bilgi depolamak sınıfları ve gerçekte çizimi yapmak sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="915c3-112"> provides classes and structures that store information about the primitives themselves, classes that store information about how the primitives will be drawn, and classes that actually do the drawing.</span></span> <span data-ttu-id="915c3-113">Örneğin, <xref:System.Drawing.Rectangle> yapısı depolayan bir dikdörtgen; boyutunu ve konumunu <xref:System.Drawing.Pen> sınıfı çizgi rengi, çizgi genişliğini ve çizgi stilini; hakkında bilgi depolar ve <xref:System.Drawing.Graphics> sınıfına sahip çizim satırlar, dikdörtgenler, yollar, yöntemleri ve diğer şekiller.</span><span class="sxs-lookup"><span data-stu-id="915c3-113">For example, the <xref:System.Drawing.Rectangle> structure stores the location and size of a rectangle; the <xref:System.Drawing.Pen> class stores information about line color, line width, and line style; and the <xref:System.Drawing.Graphics> class has methods for drawing lines, rectangles, paths, and other figures.</span></span> <span data-ttu-id="915c3-114">Vardır de birkaç <xref:System.Drawing.Brush> hakkında bilgi depolamak sınıfları kapalı şekiller ve yollar renk veya desen ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="915c3-114">There are also several <xref:System.Drawing.Brush> classes that store information about how closed figures and paths will be filled with colors or patterns.</span></span>  
  
 <span data-ttu-id="915c3-115">Bir dizi grafik komutları da vektör görüntü meta dosyası kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="915c3-115">You can record a vector image, which is a sequence of graphics commands, in a metafile.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="915c3-116">sağlar <xref:System.Drawing.Imaging.Metafile> kaydı, görüntüleme ve meta dosyaları kaydetme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="915c3-116"> provides the <xref:System.Drawing.Imaging.Metafile> class for recording, displaying, and saving metafiles.</span></span> <span data-ttu-id="915c3-117">İle <xref:System.Drawing.Imaging.MetafileHeader> ve <xref:System.Drawing.Imaging.MetaHeader> sınıfları, meta dosyası üstbilgisinde depolanan verileri incelemek.</span><span class="sxs-lookup"><span data-stu-id="915c3-117">With the <xref:System.Drawing.Imaging.MetafileHeader> and <xref:System.Drawing.Imaging.MetaHeader> classes, you can inspect the data stored in a metafile header.</span></span>  
  
## <a name="imaging"></a><span data-ttu-id="915c3-118">Görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="915c3-118">Imaging</span></span>  
 <span data-ttu-id="915c3-119">Belirli türde bir resim güç veya imkansız vektör grafikleri teknikleri ile görüntülemek.</span><span class="sxs-lookup"><span data-stu-id="915c3-119">Certain kinds of pictures are difficult or impossible to display with the techniques of vector graphics.</span></span> <span data-ttu-id="915c3-120">Örneğin, araç çubuğu düğmelerini üzerindeki resimler ve simgeler görünür resimler çizgiler ve eğrilerle koleksiyonları belirtmek zordur.</span><span class="sxs-lookup"><span data-stu-id="915c3-120">For example, the pictures on toolbar buttons and the pictures that appear as icons are difficult to specify as collections of lines and curves.</span></span> <span data-ttu-id="915c3-121">Kalabalık Beyzbol stadyum yüksek çözünürlüklü dijital fotoğrafını vektör teknikleri ile oluşturmak daha da zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="915c3-121">A high-resolution digital photograph of a crowded baseball stadium is even more difficult to create with vector techniques.</span></span> <span data-ttu-id="915c3-122">Görüntüleri bu tür diziler ekranında noktalar tek tek renkleri temsil eden sayı olan bit eşlemler olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="915c3-122">Images of this type are stored as bitmaps, which are arrays of numbers that represent the colors of individual dots on the screen.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="915c3-123">sağlar <xref:System.Drawing.Bitmap> görüntüleme, düzenleme ve bit eşlemleri kaydetme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="915c3-123"> provides the <xref:System.Drawing.Bitmap> class for displaying, manipulating, and saving bitmaps.</span></span>  
  
## <a name="typography"></a><span data-ttu-id="915c3-124">Tipografi</span><span class="sxs-lookup"><span data-stu-id="915c3-124">Typography</span></span>  
 <span data-ttu-id="915c3-125">Tipografi metni yazı tiplerini, boyutlarını ve stiller çeşitli görüntüdür.</span><span class="sxs-lookup"><span data-stu-id="915c3-125">Typography is the display of text in a variety of fonts, sizes, and styles.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="915c3-126">Bu karmaşık görev için kapsamlı destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="915c3-126"> provides extensive support for this complex task.</span></span> <span data-ttu-id="915c3-127">' Deki yeni özelliklerin biri [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] metin verir piksel düzgünleştirme LCD ekranında daha sorunsuz bir görünüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="915c3-127">One of the new features in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is subpixel antialiasing, which gives text rendered on an LCD screen a smoother appearance.</span></span>  
  
 <span data-ttu-id="915c3-128">Ayrıca, Windows Forms ile metin çizme seçeneği sunar [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] yetenekleri kendi <xref:System.Windows.Forms.TextRenderer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="915c3-128">In addition, Windows Forms offers the option to draw text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] capabilities in its <xref:System.Windows.Forms.TextRenderer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915c3-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="915c3-129">See Also</span></span>  
 [<span data-ttu-id="915c3-130">Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="915c3-130">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [<span data-ttu-id="915c3-131">GDI+ Yönetilen Kodu Hakkında</span><span class="sxs-lookup"><span data-stu-id="915c3-131">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [<span data-ttu-id="915c3-132">Yönetilen Grafik Sınıflarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="915c3-132">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
