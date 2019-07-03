---
title: Grafiklere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505326"
---
# <a name="overview-of-graphics"></a>Grafiklere Genel Bakış
GDI + Microsoft Windows işletim sisteminin alt formları bir uygulama programlama arabirimi (API)'dır. GDI + ekranları ve yazıcılar hakkında bilgi görüntülemek için sorumlu değildir. Adından da anlaşılacağı gibi GDI + GDI, önceki Windows sürümleriyle dahil grafik cihaz arabirimi geçmiştir.  
  
## <a name="managed-class-interface"></a>Yönetilen sınıf arabirimi  
 GDI + API sınıfları yönetilen kod olarak dağıtılan bir dizi aracılığıyla kullanıma sunulur. Bu sınıf kümesi adlı *yönetilen sınıf arabirimi* GDI +. Aşağıdaki ad alanları, yönetilen sınıf arabirimi oluşturan olun:  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 GDI +'gibi bir grafik cihaz arabirimi, bilgileri bir ekran veya yazıcı belirli görüntü cihazı ayrıntılarını merak gerek kalmadan görüntüleyebilirsiniz. Programcı GDI + sınıfları tarafından sağlanan yöntemlere yapılan çağrılar yapar. Bu yöntemler, buna karşılık, belirli cihaz sürücülerini uygun çağrı yapmak. GDI + grafik donanımının uygulamadan korunmasını sağlar. CİHAZDAN bağımsız uygulamalar oluşturmak için programcı sağlayan bu yalıtım var.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafiklere Genel Bakış](graphics-overview-windows-forms.md)
