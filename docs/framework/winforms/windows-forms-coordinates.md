---
title: "Windows Forms Koordinatları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4b42fd71dacb0071013067dc3c14add96c8aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-coordinates"></a>Windows Forms Koordinatları
Bir Windows formunda koordinat sistemi aygıt koordinatlarına göre ve temel ölçü Windows Forms'ta çizerken (genellikle piksel) cihaz birimdir. Ekran noktalarında x ve y koordinatını çiftlerinden sağa ve üstten alta artırma y koordinatları artırma x koordinatları ile açıklanmaktadır. Başlangıç ekranı göreli konumunu ekran veya istemci koordinatları olup belirtiyorsanız bağlı olarak değişir.  
  
## <a name="screen-coordinates"></a>Ekran koordinatları  
 Bir Windows Forms uygulaması ekran koordinatları ekranda bir pencere konumunu belirtir. Ekran koordinatları için kaynak ekranın sol üst köşesinde ' dir. Pencereyi tam konumunu genellikle tarafından açıklanan bir <xref:System.Drawing.Rectangle> penceresinin sol üst ve sağ alt köşe tanımlayan iki zaman noktası ekran koordinatları içeren yapısı.  
  
## <a name="client-coordinates"></a>İstemci koordinatları  
 Bir Windows Forms uygulaması, bir form veya istemci koordinatları kullanarak denetim noktaları konumunu belirtir. İstemci koordinatları başlangıç denetim veya formun istemci alanını sol üst köşesindeki ' dir. İstemci koordinatları bir form veya form veya denetim ekranında konumunu bağımsız olarak denetim çizerken uygulama tutarlı koordinat değerleri kullanabilirsiniz emin olun.  
  
 İstemci alanını boyutlarını da tarafından açıklanan bir <xref:System.Drawing.Rectangle> alan için istemci koordinatları içeren yapısı. Sağ alt koordinat dışlanan sırada her durumda, istemci alanında dikdörtgen sol üst koordinatını dahil edilir. Grafik işlemleri istemci alanını alt ve sağ kenarlarının dahil etmeyin. Örneğin <xref:System.Drawing.Graphics.FillRectangle%2A> yöntemi belirtilen dikdörtgenin alt ve sağ kenar doldurur, ancak bu kenarları dahil edilmez.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Koordinat türünden eşleme  
 Bazen, ekran koordinatları istemci koordinatları eşleme gerekebilir. Bunu kolayca kullanarak gerçekleştirebilirsiniz <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> yöntemleri kullanılabilir <xref:System.Windows.Forms.Control> sınıfı. Örneğin, <xref:System.Windows.Forms.Control.MousePosition%2A> özelliği <xref:System.Windows.Forms.Control> ekran koordinatları olarak bildirdi ancak bu istemci koordinatları dönüştürmek isteyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
