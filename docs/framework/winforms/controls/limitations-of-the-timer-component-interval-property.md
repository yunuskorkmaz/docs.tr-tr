---
title: "Windows Forms süreölçer bileşeni &#39;sınırlamaları; s aralık özelliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72af16b7dcb7709dd132a3748a454eda57acc168
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a>Windows Forms süreölçer bileşeni &#39;sınırlamaları; s aralık özelliği
Windows Forms <xref:System.Windows.Forms.Timer> bileşen bir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği yalnızca bir süreölçer olayı ve sonraki arasında geçen süreyi milisaniye olarak belirtir. Bileşen devre dışı bırakılmadığı sürece bir süreölçer almaya devam eder <xref:System.Windows.Forms.Timer.Tick> süre kabaca eşit aralıklarla olay.  
  
 Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun bir süreölçer gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="the-interval-property"></a>Aralık özelliği  
 <xref:System.Windows.Forms.Timer.Interval%2A> Özelliği, ne zaman programlama dikkate alınması gereken birkaç sınırlamalara sahiptir bir <xref:System.Windows.Forms.Timer> bileşen:  
  
-   Uygulamanızı veya başka bir uygulama sistem üzerinde ağır taleplerini değiştirirken, — uzun döngüler, yoğun hesaplamalar veya sürücü, ağ veya bağlantı noktası erişim gibi — uygulamanızı Süreölçer olayları kadar sık olarak alamayabilirsiniz <xref:System.Windows.Forms.Timer.Interval%2A> özelliği belirtir.  
  
-   Aralık tam zamanında geçmesi garanti edilmez. Doğruluk emin olmak için Zamanlayıcı gerektiği gibi sistem saatini denetleyin yerine biriken zaman dahili olarak izlemek deneyin.  
  
-   Kesinliğini <xref:System.Windows.Forms.Timer.Interval%2A> milisaniye cinsinden bir özelliktir. Bazı bilgisayarlarda milisaniye yüksek çözünürlüğe olan yüksek çözünürlüklü bir sayaç sağlar. Bu tür bir sayaç kullanılabilirliği bilgisayarınızı işlemci donanımda bağlıdır. Daha fazla bilgi için 172338, "Nasıl için kullanım QueryPerformanceCounter için zamanı kodu," http://support.microsoft.com adresindeki Microsoft Bilgi Bankası makalesine bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Timer>  
 [Süreölçer bileşeni](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Süreölçer bileşenine genel bakış](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
