---
title: Windows Forms Koordinatları
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: 6feabadff17538f4a7368c348f7b72226e2d678e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980661"
---
# <a name="windows-forms-coordinates"></a>Windows Forms Koordinatları
Koordinat sistemi bir Windows formu için cihaz koordinatlarına temel alır ve cihaz birim (genellikle, piksel) temel Windows Forms'ta çizme, ölçü birimidir. Ekran noktalarında x ve y koordinatını çiftlerine göre sağa ve yukarıdan altına artırma y koordinatları artırma x koordinatları ile açıklanmaktadır. Ekranına göre kaynak konumu, ekran veya istemci koordinatları olup belirtiyorsanız bağlı olarak değişir.  
  
## <a name="screen-coordinates"></a>Ekran koordinatları  
 Bir Windows Forms uygulaması ekranında ekran koordinatlarına göre bir pencerenin konumunu belirtir. Ekran koordinatları için kaynak ekranın sol üst köşesinde ' dir. Tam bir pencerenin konumunun genellikle tarafından açıklanan bir <xref:System.Drawing.Rectangle> penceresinin sol ve sağ alt köşe tanımlayan iki nokta ekran koordinatları içeren yapısı.  
  
## <a name="client-coordinates"></a>İstemci koordinatları  
 Bir Windows Forms uygulaması, bir form veya istemci koordinatları kullanarak denetim noktaları konumunu belirtir. İstemci koordinatları için kaynak denetim veya formun istemci alanını sol üst köşesinde ' dir. İstemci koordinatları bir form veya denetim, form veya denetim ekranda konumunu bakılmaksızın çizerken uygulama tutarlı koordinat değerleri kullanabilirsiniz emin olun.  
  
 İstemci alanını boyutlarını da tarafından açıklanan bir <xref:System.Drawing.Rectangle> alan için istemci koordinatları içeren yapısı. Sağ alt koordinat dışlandı ancak her durumda, istemci alanında dikdörtgenin sol üst koordinat dahil edilir. Grafik işlemleri istemci alanını alt ve sağ kenarları içermez. Örneğin <xref:System.Drawing.Graphics.FillRectangle%2A> yöntemi belirtilen dikdörtgen alt ve sağ kenarı dolar, ancak bu kenarları içermez.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Koordinat türünden diğerine eşleme  
 Bazen, istemci koordinatları ekran koordinatlarından harita gerekebilir. Kullanarak bunu kolayca gerçekleştirebilirsiniz <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> kullanılabilir yöntemleri <xref:System.Windows.Forms.Control> sınıfı. Örneğin, <xref:System.Windows.Forms.Control.MousePosition%2A> özelliği <xref:System.Windows.Forms.Control> ekran koordinatlarında bildirilir ancak bunlar istemci koordinatlarına Dönüştür isteyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
