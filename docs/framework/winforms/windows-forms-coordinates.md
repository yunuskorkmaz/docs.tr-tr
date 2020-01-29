---
title: M
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: c95888f31bfc867e9c028d53072ab3d710256708
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734669"
---
# <a name="windows-forms-coordinates"></a>Windows Forms Koordinatları
Bir Windows form için koordinat sistemi, cihaz koordinatlarına ve Windows Forms çizim sırasında temel ölçü biriminden (genellikle piksel) oluşur. Ekrandaki noktalara, x ve y koordinatı çiftleri ve en üstten alta doğru artan y koordinatları olacak şekilde x koordinatları ile açıklanmıştır. Ekranın, ekran veya istemci koordinatları belirtdiğinize bağlı olarak değişir.  
  
## <a name="screen-coordinates"></a>Ekran koordinatları  
 Bir Windows Forms uygulaması Ekran koordinatlarındaki ekranda pencerenin konumunu belirtir. Ekran koordinatları için, başlangıç ekranın sol üst köşesidir. Pencerenin tam konumu genellikle pencerenin sol üst ve sağ alt köşelerinden oluşan iki noktanın ekran koordinatlarını içeren <xref:System.Drawing.Rectangle> yapısıyla açıklanır.  
  
## <a name="client-coordinates"></a>İstemci koordinatları  
 Windows Forms bir uygulama, istemci koordinatlarını kullanarak bir formdaki veya denetimdeki noktaların konumunu belirtir. İstemci koordinatları için kaynak, denetimin veya formun istemci alanının sol üst köşesindedir. İstemci koordinatları, bir uygulamanın, ekranda formun veya denetimin konumundan bağımsız olarak bir form veya denetimde çizim yaparken tutarlı koordinat değerlerini kullanmasını sağlar.  
  
 İstemci alanının boyutları Ayrıca, alanı için istemci koordinatlarını içeren <xref:System.Drawing.Rectangle> yapısı tarafından da açıklanır. Her durumda, dikdörtgenin sol üst koordinatı istemci alanına dahil edilir, ancak sağ alt koordinat hariç tutulur. Grafik işlemleri bir istemci alanının sağ ve alt kenarlarını içermez. Örneğin <xref:System.Drawing.Graphics.FillRectangle%2A> yöntemi belirtilen dikdörtgenin sağ ve alt kenarına dolduracak, ancak bu kenarları içermemelidir.  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>Bir koordinat türünden diğerine eşleme  
 Bazen ekran koordinatlarından istemci koordinatlarına eşleme yapmanız gerekebilir. <xref:System.Windows.Forms.Control> sınıfında bulunan <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> yöntemlerini kullanarak kolayca bunu yapabilirsiniz. Örneğin, <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Control.MousePosition%2A> özelliği ekran koordinatlarında raporlanır, ancak bunları istemci koordinatlarına dönüştürmek isteyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
