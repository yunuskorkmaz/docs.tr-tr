---
title: Grafik Arabiriminin Yapısı
ms.date: 03/30/2017
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
ms.openlocfilehash: 33be9d4d4e5a1aca933bb84e948b2200cd96b152
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708125"
---
# <a name="structure-of-the-graphics-interface"></a>Grafik Arabiriminin Yapısı
Yönetilen sınıf arabirimine [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] yaklaşık 60 sınıfları, 50 sabit listeleri ve 8 yapıları içerir. <xref:System.Drawing.Graphics> Sınıftır özünde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] işlevselliği; aslında çizgiler, eğriler, rakamları, görüntü ve metin çizer sınıftır.  
  
## <a name="important-classes"></a>Önemli sınıfları  
 Çok sayıda sınıfa birlikte çalışmak <xref:System.Drawing.Graphics> sınıfı. Örneğin, <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi alır bir <xref:System.Drawing.Pen> öznitelikleri (renk, genişlik, kesik çizgi stili ve benzeri) çizilecek satırının tutan nesne. <xref:System.Drawing.Graphics.FillRectangle%2A> Yönteminde bir işaretçi alır bir <xref:System.Drawing.Drawing2D.LinearGradientBrush> ile çalışan nesne <xref:System.Drawing.Graphics> dikdörtgen kademeli olarak değişen bir rengi ile doldurmak için nesne. <xref:System.Drawing.Font> ve <xref:System.Drawing.StringFormat> nesnelerin şeklini etkileyen bir <xref:System.Drawing.Graphics> nesne metin çizer. A <xref:System.Drawing.Drawing2D.Matrix> nesne depolar ve dünya dönüşümü işleyen bir <xref:System.Drawing.Graphics> görüntüleri çevirme döndürme ve ölçeklendirme için kullanılan nesne.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çeşitli yapılar sağlar (örneğin, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, ve <xref:System.Drawing.Size>) grafik veri düzenlemek için. Ayrıca, belirli sınıfların birincil olarak yapılandırılmış veri türleri işlevi görür. Örneğin, <xref:System.Drawing.Imaging.BitmapData> için bir yardımcı sınıftır <xref:System.Drawing.Bitmap> sınıfı ve <xref:System.Drawing.Drawing2D.PathData> için bir yardımcı sınıftır <xref:System.Drawing.Drawing2D.GraphicsPath> sınıfı.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] koleksiyonları ilgili sabitlerinin birkaç sabit listeleri tanımlanmıştır. Örneğin, <xref:System.Drawing.Drawing2D.LineJoin> sabit listesi öğeleri içerir <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, ve <xref:System.Drawing.Drawing2D.LineJoin.Round>, iki satır katılmak için kullanılan stilleri belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Grafiklere Genel Bakış](graphics-overview-windows-forms.md)
- [GDI+ Yönetilen Kodu Hakkında](about-gdi-managed-code.md)
- [Yönetilen Grafik Sınıflarını Kullanma](using-managed-graphics-classes.md)
