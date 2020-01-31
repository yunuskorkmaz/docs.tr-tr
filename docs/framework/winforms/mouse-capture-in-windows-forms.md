---
title: Fare yakalama
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741025"
---
# <a name="mouse-capture-in-windows-forms"></a>Windows Forms'ta Fare Yakalama
*Fare yakalama* , bir denetimin tüm fare girişi komutunu ne zaman aldığını belirtir. Bir denetim fareyi yakaladıktan sonra, işaretçinin sınırları içinde olup olmadığını fare girişi alır.  
  
## <a name="setting-mouse-capture"></a>Fare yakalamayı ayarlama  
 Windows Forms fare, Kullanıcı denetimin üzerinde fare düğmesine bastığında denetim tarafından yakalanır ve Kullanıcı fare düğmesini bıraktığında denetim tarafından serbest bırakılır.  
  
 <xref:System.Windows.Forms.Control> sınıfının <xref:System.Windows.Forms.Control.Capture%2A> özelliği, bir denetimin fareyi yakalamasının gerekip gerekmediğini belirtir. Bir denetimin fare yakalamayı kaybettiğini öğrenmek için <xref:System.Windows.Forms.Control.MouseCaptureChanged> olayını işleyin.  
  
 Yalnızca ön plan penceresi fareyi yakalayabilir. Arka plan penceresi fare yakalamayı denediğinde, pencere yalnızca fare işaretçisi pencerenin görünür bölümü içindeyse oluşan fare olayları için ileti alır. Ayrıca, ön plan penceresi fareyi yakalasa bile, Kullanıcı başka bir pencereye tıklayabilir ve bu da ön plana devam edebilir. Fare yakalandığında kısayol tuşları çalışmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)
