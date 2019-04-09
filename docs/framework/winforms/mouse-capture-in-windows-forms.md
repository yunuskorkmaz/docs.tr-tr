---
title: Windows Forms'ta Fare Yakalama
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 30432c6978f60cc9ad47d5df5dafc7aa45229f3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151651"
---
# <a name="mouse-capture-in-windows-forms"></a>Windows Forms'ta Fare Yakalama
*Fare yakalama* denetim tüm fare girişi komutunu aldığında ifade eder. Denetim fare yakalandı, işaretçi sınırlarının içinde olup olmadığını fare girişi alır.  
  
## <a name="setting-mouse-capture"></a>Fare yakalama ayarlama  
 Windows Forms'ta fare kullanıcı bir denetimde bir fare düğmesi ve kullanıcı fare düğmesini bıraktığında fare denetim tarafından serbest denetim tarafından yakalanır.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Özelliği <xref:System.Windows.Forms.Control> sınıfı bir denetim fareyi yakalanan olup olmadığını belirtir. Ne zaman bir denetim fare yakalamayı kaybettiğinde belirlemek için tanıtıcı <xref:System.Windows.Forms.Control.MouseCaptureChanged> olay.  
  
 Yalnızca ön plan penceresi fare yakalayabilirsiniz. Bir arka plan penceresi fare yakalama girişiminde bulunduğunda, pencerenin fare işaretçisi penceresi görünür bölümünün içinde olduğunda gerçekleşen fare olayları için iletileri alır. Ön plan penceresi fare yakalandı olsa bile, kullanıcı hala başka bir pencere ön plana çerçevesinde tıklatabilirsiniz. Fare yakalandığında kısayol tuşu çalışmıyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)
