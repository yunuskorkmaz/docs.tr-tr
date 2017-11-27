---
title: "Grafik Arabiriminin Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd1da930df151869ea3e891da7057f44ed0a4603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-of-the-graphics-interface"></a><span data-ttu-id="d3e12-102">Grafik Arabiriminin Yapısı</span><span class="sxs-lookup"><span data-stu-id="d3e12-102">Structure of the Graphics Interface</span></span>
<span data-ttu-id="d3e12-103">Yönetilen sınıf arabirimi [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 60 sınıfları, 50 numaralandırmalar ve 8 yapılar içerir.</span><span class="sxs-lookup"><span data-stu-id="d3e12-103">The managed class interface to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contains about 60 classes, 50 enumerations, and 8 structures.</span></span> <span data-ttu-id="d3e12-104"><xref:System.Drawing.Graphics> Sınıftır çekirdeği, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] işlevselliği; gerçekten çizgiler, eğriler, rakamları, görüntüler ve metin çizer sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d3e12-104">The <xref:System.Drawing.Graphics> class is at the core of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] functionality; it is the class that actually draws lines, curves, figures, images, and text.</span></span>  
  
## <a name="important-classes"></a><span data-ttu-id="d3e12-105">Önemli sınıfları</span><span class="sxs-lookup"><span data-stu-id="d3e12-105">Important Classes</span></span>  
 <span data-ttu-id="d3e12-106">Birçok sınıflarının ile birlikte çalışma <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d3e12-106">Many classes work together with the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="d3e12-107">Örneğin, <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> öznitelikleri (renk, genişlik, çizgi stili ve benzeri) çizilecek satırının tutan nesne.</span><span class="sxs-lookup"><span data-stu-id="d3e12-107">For example, the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object, which holds attributes (color, width, dash style, and the like) of the line to be drawn.</span></span> <span data-ttu-id="d3e12-108"><xref:System.Drawing.Graphics.FillRectangle%2A> Yöntemi için bir işaretçi alabilir bir <xref:System.Drawing.Drawing2D.LinearGradientBrush> çalışır nesne <xref:System.Drawing.Graphics> dikdörtgen kademeli olarak değişen bir renkle doldurmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="d3e12-108">The <xref:System.Drawing.Graphics.FillRectangle%2A> method can receive a pointer to a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object, which works with the <xref:System.Drawing.Graphics> object to fill a rectangle with a gradually changing color.</span></span> <span data-ttu-id="d3e12-109"><xref:System.Drawing.Font>ve <xref:System.Drawing.StringFormat> nesneleri biçimini etkileyen bir <xref:System.Drawing.Graphics> nesne çizer metin.</span><span class="sxs-lookup"><span data-stu-id="d3e12-109"><xref:System.Drawing.Font> and <xref:System.Drawing.StringFormat> objects influence the way a <xref:System.Drawing.Graphics> object draws text.</span></span> <span data-ttu-id="d3e12-110">A <xref:System.Drawing.Drawing2D.Matrix> nesne depolar ve dünya dönüşümü işleyen bir <xref:System.Drawing.Graphics> döndürme, ölçeklendirme ve görüntüleri ters çevirmek için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="d3e12-110">A <xref:System.Drawing.Drawing2D.Matrix> object stores and manipulates the world transformation of a <xref:System.Drawing.Graphics> object, which is used to rotate, scale, and flip images.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="d3e12-111">çeşitli yapılar sağlar (örneğin, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, ve <xref:System.Drawing.Size>) grafik veri düzenlemek için.</span><span class="sxs-lookup"><span data-stu-id="d3e12-111"> provides several structures (for example, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, and <xref:System.Drawing.Size>) for organizing graphics data.</span></span> <span data-ttu-id="d3e12-112">Ayrıca, belirli sınıfları, birincil olarak yapılandırılmış veri türleri hizmet.</span><span class="sxs-lookup"><span data-stu-id="d3e12-112">Also, certain classes serve primarily as structured data types.</span></span> <span data-ttu-id="d3e12-113">Örneğin, <xref:System.Drawing.Imaging.BitmapData> için bir yardımcı sınıfıdır <xref:System.Drawing.Bitmap> sınıfı ve <xref:System.Drawing.Drawing2D.PathData> için bir yardımcı sınıfıdır <xref:System.Drawing.Drawing2D.GraphicsPath> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d3e12-113">For example, the <xref:System.Drawing.Imaging.BitmapData> class is a helper for the <xref:System.Drawing.Bitmap> class, and the <xref:System.Drawing.Drawing2D.PathData> class is a helper for the <xref:System.Drawing.Drawing2D.GraphicsPath> class.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="d3e12-114">ilgili sabitleri koleksiyonlarıdır birkaç numaralandırmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3e12-114"> defines several enumerations, which are collections of related constants.</span></span> <span data-ttu-id="d3e12-115">Örneğin, <xref:System.Drawing.Drawing2D.LineJoin> numaralandırma öğeleri içeren <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, ve <xref:System.Drawing.Drawing2D.LineJoin.Round>, iki satır katılmak için kullanılan stiller belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3e12-115">For example, the <xref:System.Drawing.Drawing2D.LineJoin> enumeration contains the elements <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, and <xref:System.Drawing.Drawing2D.LineJoin.Round>, which specify styles that can be used to join two lines.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e12-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3e12-116">See Also</span></span>  
 [<span data-ttu-id="d3e12-117">Grafiklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="d3e12-117">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [<span data-ttu-id="d3e12-118">GDI + yönetilen kodu hakkında</span><span class="sxs-lookup"><span data-stu-id="d3e12-118">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [<span data-ttu-id="d3e12-119">Yönetilen grafik sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="d3e12-119">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
