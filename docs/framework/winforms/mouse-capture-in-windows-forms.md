---
title: Windows Forms'ta Fare Yakalama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8004b05ea25341a142bfcfd9ae812ee3bebd6d5b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a>Windows Forms'ta Fare Yakalama
*Fare yakalama* denetim tüm fare girişi komutu yönlendirdiğinde başvuruyor. Bir denetim fare yakalandı, işaretçi sınırlarının içinde olup olmadığını fare girdisi alır.  
  
## <a name="setting-mouse-capture"></a>Fare yakalama ayarlama  
 Windows Forms'ta fare bir denetimde bir fare düğmesini kullanıcı ve kullanıcı fare düğmesini bıraktığında fare denetim tarafından yayımlanan denetim tarafından yakalanır.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Özelliği <xref:System.Windows.Forms.Control> sınıfı bir denetim fare yakalanan olup olmadığını belirtir. Ne zaman bir denetim fare yakalama kaybederse belirlemek için tanıtıcı <xref:System.Windows.Forms.Control.MouseCaptureChanged> olay.  
  
 Yalnızca ön plan penceresi fare yakalayabilirsiniz. Bir arka plan penceresi fare yakalama girişiminde bulunduğunda, pencere iletileri için fare işaretçisini penceresinde görünen dilimini içinde olduğunda oluşan fare olayları alır. Ön plan penceresi fare yakalandı olsa bile, kullanıcı hala başka bir pencere ön plana getiren tıklatabilirsiniz. Fare yakalandığında kısayol tuşları çalışmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Forms bir Windows uygulamasında fare girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
