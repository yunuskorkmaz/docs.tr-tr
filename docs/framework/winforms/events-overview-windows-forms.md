---
title: "Olaylara Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f73a336da5b61de90a67a8392b5cfc8f28619254
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="events-overview-windows-forms"></a>Olaylara Genel Bakış (Windows Forms)
Olaya yanıt verebilirsiniz bir eylem veya "işlemek," kodunu içerir. Olaylar, fareyi tıklatarak veya bir tuşa basılması gibi bir kullanıcı eylemi tarafından oluşturulabilir; Program kodla; veya sistem tarafından.  
  
 Olay kaynaklı uygulamaları bir olaya yanıt olarak kodu yürütün. Her form ve denetim karşı program olayları önceden tanımlanmış bir kümesini gösterir. Aşağıdaki olaylardan biri gerçekleşene ve ilişkili olay işleyicisini kod ise, bu kodu çağrılır.  
  
 Nesne tarafından başlatılan olayları türlerini farklılık, ancak birçok türleri çoğu denetimleri için ortak olan. Örneğin, çoğu nesneyi işleyecek bir <xref:System.Windows.Forms.Control.Click> olay. Bir kullanıcı bir form tıklarsa formun kod <xref:System.Windows.Forms.Control.Click> olay işleyicisi gerçekleştirilir.  
  
> [!NOTE]
>  Diğer olaylar ile birlikte birçok olaylar oluşur. Örneğin, içinde course, <xref:System.Windows.Forms.Control.DoubleClick> gerçekleşmesini olay <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>, ve <xref:System.Windows.Forms.Control.Click> olayları oluşur.  
  
 Yükseltmek ve bir olay kullanma hakkında daha fazla bilgi için bkz: [olayları](../../../docs/standard/events/index.md).  
  
## <a name="delegates-and-their-role"></a>Temsilciler ve rolleri  
 Temsilciler sınıflardır içinde yaygın olarak kullanılan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] olay işleme mekanizmaları oluşturmak için. Temsilciler kabaca eşitlemek için yaygın olarak kullanılan işlev işaretçileri [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] ve diğer nesne yönelimli diller. İşlev işaretçileri, ancak, nesne yönelimli, tür kullanımı uyumlu ve güvenli temsilciler. Ayrıca, burada bir işlev işaretçisi yalnızca belirli bir işleve bir başvuru içeriyor bir temsilci bir nesneye başvuru oluşur ve nesne içinde bir veya daha fazla yöntemlerini başvuruyor.  
  
 Bu olay modelini kullanır, *Temsilciler* bunları işlemek için kullanılan yöntemleri olayları bağlanacak. Temsilci bir işleyici yöntemi belirterek olay bildirimi için kaydolmaya diğer sınıflar sağlar. Olay ortaya çıktığında temsilci ilişkili yöntemi çağırır. Temsilcileri tanımlama hakkında daha fazla bilgi için bkz: [olayları](../../../docs/standard/events/index.md).  
  
 Temsilciler, tek bir yöntemi veya birden çok yöntem, çok noktaya yayın başvurulan bağlanabilir. Bir olay için bir temsilci oluştururken, sizin (veya Windows Form Tasarımcısı) genellikle bir çok noktaya yayın olay oluşturursunuz. Nadir bir özel durum, mantıksal olarak birden çok kez olay yinelemeniz değil (örneğin bir iletişim kutusunu görüntüleme) belirli bir yordamı sonuçlanan bir olay olabilir. Çok noktaya yayın temsilci oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: temsilcileri birleştirme (çok noktaya yayın temsilcileri)](~/docs/csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).  
  
 Çok noktaya yayın temsilci bağlı yöntemleri çağırma listesini tutar. Çok noktaya yayını destekleyen temsilci bir <xref:System.Delegate.Combine%2A> bir yöntemi çağırma listesine eklemek için yöntem ve bir <xref:System.Delegate.Remove%2A> kaldırmaya yöntemi.  
  
 Bir olay uygulama tarafından kaydedildiğinde denetimi bu olay için temsilci çağırarak olayını başlatır. Temsilci sırayla ilişkili yöntemi çağırır. (Çok noktaya yayın temsilci) en sık karşılaşılan durumda temsilci her ilişkili yöntemini çağırma listesinde sırasıyla bir-çok bildirim sağlayan çağırır. Bu strateji denetim olayı bildirimi için hedef nesnelerin listesini korumak gerekmez anlamına gelir — tüm kayıt ve bildirim temsilci işler.  
  
 Temsilciler çok bir bildirim izin vererek aynı yönteme bağlı birden çok olay da etkinleştirin. Örneğin, bir düğme tıklama olay ve menü komutu – tıklatma olay her ikisi de aynı şekilde bu ayrı olayları işlemek için tek bir yöntemi çağırır aynı temsilci çağırabilirsiniz.  
  
 Temsilciler ile kullanılan bağlama dinamik mekanizmadır: çalışma zamanında, imza, olay işleyicisinin eşleşen herhangi bir yöntemi için bir temsilci bağlanabilir. Bu özellik ile ayarlayın veya bağlı bir koşul olarak ve bir olay işleyicisi için bir denetim dinamik olarak eklemek için bağlama yöntemini değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Olay İşleyicilerine Genel Bakış](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
