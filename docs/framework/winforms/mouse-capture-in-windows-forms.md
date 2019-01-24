---
title: Windows Forms'ta Fare Yakalama
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: ca16d2fa2339f8d9110bb748a687f90e093598fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690338"
---
# <a name="mouse-capture-in-windows-forms"></a>Windows Forms'ta Fare Yakalama
*Fare yakalama* denetim tüm fare girişi komutunu aldığında ifade eder. Denetim fare yakalandı, işaretçi sınırlarının içinde olup olmadığını fare girişi alır.  
  
## <a name="setting-mouse-capture"></a>Fare yakalama ayarlama  
 Windows Forms'ta fare kullanıcı bir denetimde bir fare düğmesi ve kullanıcı fare düğmesini bıraktığında fare denetim tarafından serbest denetim tarafından yakalanır.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Özelliği <xref:System.Windows.Forms.Control> sınıfı bir denetim fareyi yakalanan olup olmadığını belirtir. Ne zaman bir denetim fare yakalamayı kaybettiğinde belirlemek için tanıtıcı <xref:System.Windows.Forms.Control.MouseCaptureChanged> olay.  
  
 Yalnızca ön plan penceresi fare yakalayabilirsiniz. Bir arka plan penceresi fare yakalama girişiminde bulunduğunda, pencerenin fare işaretçisi penceresi görünür bölümünün içinde olduğunda gerçekleşen fare olayları için iletileri alır. Ön plan penceresi fare yakalandı olsa bile, kullanıcı hala başka bir pencere ön plana çerçevesinde tıklatabilirsiniz. Fare yakalandığında kısayol tuşu çalışmıyor.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
