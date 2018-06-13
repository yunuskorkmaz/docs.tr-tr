---
title: Grafiklere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: a69bfc2e9983484f90b1b65abd234df2519b503e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523561"
---
# <a name="overview-of-graphics"></a>Grafiklere Genel Bakış
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Microsoft Windows işletim sistemi alt formları bir uygulama programlama arabirimi (API) var. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ekranlar ve yazıcılar bilgilerini görüntülemek için sorumludur. Adından da anlaşılacağı gibi [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] devamıdır [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], önceki Windows sürümlerinde bulunan grafik cihaz arabirimi.  
  
## <a name="managed-class-interface"></a>Yönetilen sınıf arabirimi  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API kümesi ile yönetilen kod dağıtılan sınıfları gösterilir. Bu sınıf kümesini olarak adlandırılır *yönetilen sınıf arabirimi* için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Şu ad alanlarından yönetilen sınıf arabirimi olun:  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 Grafik cihaz arabirimi ile gibi [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], belirli görüntü aygıtı ayrıntılar hakkında endişelenmeniz zorunda kalmadan bir ekran veya yazıcı bilgileri görüntüleyebilirsiniz. Programcı tarafından sağlanan yöntemleri çağrılar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları. Bu yöntem, buna karşılık, belirli aygıt sürücüleri için uygun çağrıları yapma. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Grafik donanım uygulamadan korunmasını sağlar. CİHAZDAN bağımsız uygulamalar oluşturmak için programcı sağlayan bu yalıtımı olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafiklere Genel Bakış](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
