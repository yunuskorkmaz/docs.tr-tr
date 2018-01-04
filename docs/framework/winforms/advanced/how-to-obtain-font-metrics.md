---
title: "Nasıl yapılır: Yazı Tipi Ölçümleri Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16f1126cc75b75ae98298f5d1c58c78ff30edbb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-font-metrics"></a>Nasıl yapılır: Yazı Tipi Ölçümleri Alma
<xref:System.Drawing.FontFamily> Sınıfı, belirli ailesi/stil birleşimi için çeşitli ölçümleri alma aşağıdaki yöntemleri sağlar:  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Boyut ve belirli bir ölçü bağımsız şekilde bu yöntemler tarafından döndürülen yazı tipi tasarım birimlerinde numaralarıdır <xref:System.Drawing.Font> nesnesi.  
  
 Aşağıdaki çizimde, çeşitli ölçümleri gösterir.  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Arial yazı tipi ailesinin Normal stilini ölçümleri görüntüler. Kod ayrıca oluşturur bir <xref:System.Drawing.Font> boyutu 16 piksel ve bu belirli (piksel cinsinden) ölçümlerini görüntüler'ün (Arial ailesini temel alan) nesnesiyle <xref:System.Drawing.Font> nesnesi.  
  
 Aşağıdaki çizimde örnek kod çıktısını gösterir.  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")  
  
 Önceki çizimde çıktısını ilk iki satır unutmayın. <xref:System.Drawing.Font> Nesnesi döndürür 16, boyutunu ve <xref:System.Drawing.FontFamily> nesne 2.048 em yüksekliğini döndürür. Bu iki (16 ve 2.048) yazı tipi tasarım birimleri ve (Bu örnek piksel cinsinden) birimleri arasında dönüştürme anahtarını numaralarıdır <xref:System.Drawing.Font> nesnesi.  
  
 Örneğin, Yokuş tasarım birimlerinden piksel olarak şu şekilde dönüştürebilirsiniz:  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")  
  
 Aşağıdaki kod konumlandırır metin dikey olarak ayarlayarak <xref:System.Drawing.PointF.Y%2A> veri üyesi bir <xref:System.Drawing.PointF> nesnesi. Y koordinatını artırılır `font.Height` yeni her metin satırının için. <xref:System.Drawing.Font.Height%2A> Özelliği bir <xref:System.Drawing.Font> nesnesi döndürür (piksel cinsinden) satır aralığı için bu belirli <xref:System.Drawing.Font> nesnesi. Bu örnekte, sayısı tarafından döndürülen <xref:System.Drawing.Font.Height%2A> 19 değil. Bunun için piksel satır aralığı ölçüm dönüştürerek elde (tamsayıya yuvarlanan) numarasıyla aynı olduğunu unutmayın.  
  
 (Boyutu veya em boyutu olarak da bilinir) em yükseklik Yokuş ve düşüşü toplamı olmadığını unutmayın. Hücre Yüksekliği Yokuş ve düşüşü toplamı denir. Hücre Yüksekliği iç başında eksi em yüksekliğini eşittir. Hücre Yüksekliği artı dış başında eşittir satır aralığı.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
