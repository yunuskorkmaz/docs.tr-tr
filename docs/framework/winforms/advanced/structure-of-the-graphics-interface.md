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
ms.workload: dotnet
ms.openlocfilehash: 43bd899a1dd53dc8cdae4f81e90b1aa74c29cb67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="structure-of-the-graphics-interface"></a>Grafik Arabiriminin Yapısı
Yönetilen sınıf arabirimi [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 60 sınıfları, 50 numaralandırmalar ve 8 yapılar içerir. <xref:System.Drawing.Graphics> Sınıftır çekirdeği, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] işlevselliği; gerçekten çizgiler, eğriler, rakamları, görüntüler ve metin çizer sınıftır.  
  
## <a name="important-classes"></a>Önemli sınıfları  
 Birçok sınıflarının ile birlikte çalışma <xref:System.Drawing.Graphics> sınıfı. Örneğin, <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> öznitelikleri (renk, genişlik, çizgi stili ve benzeri) çizilecek satırının tutan nesne. <xref:System.Drawing.Graphics.FillRectangle%2A> Yöntemi için bir işaretçi alabilir bir <xref:System.Drawing.Drawing2D.LinearGradientBrush> çalışır nesne <xref:System.Drawing.Graphics> dikdörtgen kademeli olarak değişen bir renkle doldurmak için nesne. <xref:System.Drawing.Font>ve <xref:System.Drawing.StringFormat> nesneleri biçimini etkileyen bir <xref:System.Drawing.Graphics> nesne çizer metin. A <xref:System.Drawing.Drawing2D.Matrix> nesne depolar ve dünya dönüşümü işleyen bir <xref:System.Drawing.Graphics> döndürme, ölçeklendirme ve görüntüleri ters çevirmek için kullanılan nesne.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]çeşitli yapılar sağlar (örneğin, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, ve <xref:System.Drawing.Size>) grafik veri düzenlemek için. Ayrıca, belirli sınıfları, birincil olarak yapılandırılmış veri türleri hizmet. Örneğin, <xref:System.Drawing.Imaging.BitmapData> için bir yardımcı sınıfıdır <xref:System.Drawing.Bitmap> sınıfı ve <xref:System.Drawing.Drawing2D.PathData> için bir yardımcı sınıfıdır <xref:System.Drawing.Drawing2D.GraphicsPath> sınıfı.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]ilgili sabitleri koleksiyonlarıdır birkaç numaralandırmaları tanımlar. Örneğin, <xref:System.Drawing.Drawing2D.LineJoin> numaralandırma öğeleri içeren <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, ve <xref:System.Drawing.Drawing2D.LineJoin.Round>, iki satır katılmak için kullanılan stiller belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafiklere Genel Bakış](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [GDI+ Yönetilen Kodu Hakkında](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Yönetilen Grafik Sınıflarını Kullanma](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
