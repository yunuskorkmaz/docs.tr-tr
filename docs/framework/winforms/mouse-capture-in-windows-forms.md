---
title: Windows Forms'ta Fare Yakalama
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: afb58df99ea30f5e7e6ab5b9156af195d273c44d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712714"
---
# <a name="mouse-capture-in-windows-forms"></a>Windows Forms'ta Fare Yakalama
*Fare yakalama* denetim tüm fare girişi komutunu aldığında ifade eder. Denetim fare yakalandı, işaretçi sınırlarının içinde olup olmadığını fare girişi alır.  
  
## <a name="setting-mouse-capture"></a>Fare yakalama ayarlama  
 Windows Forms'ta fare kullanıcı bir denetimde bir fare düğmesi ve kullanıcı fare düğmesini bıraktığında fare denetim tarafından serbest denetim tarafından yakalanır.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Özelliği <xref:System.Windows.Forms.Control> sınıfı bir denetim fareyi yakalanan olup olmadığını belirtir. Ne zaman bir denetim fare yakalamayı kaybettiğinde belirlemek için tanıtıcı <xref:System.Windows.Forms.Control.MouseCaptureChanged> olay.  
  
 Yalnızca ön plan penceresi fare yakalayabilirsiniz. Bir arka plan penceresi fare yakalama girişiminde bulunduğunda, pencerenin fare işaretçisi penceresi görünür bölümünün içinde olduğunda gerçekleşen fare olayları için iletileri alır. Ön plan penceresi fare yakalandı olsa bile, kullanıcı hala başka bir pencere ön plana çerçevesinde tıklatabilirsiniz. Fare yakalandığında kısayol tuşu çalışmıyor.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)
