---
title: Grafiklere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: 927fc327d9ad42cd3a99af207d04efbc520df8b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645697"
---
# <a name="overview-of-graphics"></a>Grafiklere Genel Bakış
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Microsoft Windows işletim sisteminin alt formları bir uygulama programlama arabirimi (API) olan. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ekranlar ve yazıcılar hakkında bilgi görüntülemek için sorumludur. Adından da anlaşılacağı gibi [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] geçmiştir [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], önceki Windows sürümleriyle dahil grafik cihaz arabirimi.  
  
## <a name="managed-class-interface"></a>Yönetilen sınıf arabirimi  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API sınıfları yönetilen kod olarak dağıtılan bir dizi aracılığıyla gösterilir. Bu sınıf kümesi adlı *yönetilen sınıf arabirimi* için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Aşağıdaki ad alanları, yönetilen sınıf arabirimi oluşturan olun:  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 Grafik cihaz arabirimi ile gibi [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], belirli bir görüntü ayrıntılarını merak zorunda kalmadan bir ekran veya yazıcı bilgileri görüntüleyebilirsiniz. Programcı tarafından sağlanan yöntemlere yapılan çağrılar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları. Bu yöntemler, buna karşılık, belirli cihaz sürücülerini uygun çağrı yapmak. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik donanımının uygulamadan korunmasını sağlar. CİHAZDAN bağımsız uygulamalar oluşturmak için programcı sağlayan bu yalıtım var.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafiklere Genel Bakış](graphics-overview-windows-forms.md)
