---
title: Geçiş Kılavuzu
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 405ed0dcbd730f08b84ad0b40008c4d77b02e26f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719682"
---
# <a name="migration-guidance"></a>Geçiş Kılavuzu
İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Microsoft ikinci ana sürüm Windows Workflow Foundation (WF) yayımladı. [!INCLUDE[wf1](../../../includes/wf1-md.md)] çıkan [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (Bu System.Workflow.* ad alanlarında türleri dahil; artık WF3 adlandırılır) ve geliştirilmiş içinde [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. WF3 olduğunu da parçası [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ancak yeni bir iş akışı teknoloji vardır (System.Activities. türlerinde\* ad alanları; WF4 başvurulan). WF4 benimsemek ne zaman düşünürken öncelikle zamanlamasını denetlemek bilmek önemlidir.  
  
-   WF3 tam olarak desteklenen bir parçası olan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
-   WF3 uygulamaları çalıştırıp [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] yapmadan ve tam olarak desteklenmeye devam edilir.  
  
-   Yeni WF3 uygulamalar oluşturulabilir ve mevcut uygulamalarınızı Visual Studio 2012'de düzenlenebilir ve tam olarak desteklenir.  
  
 Bu nedenle, .NET Framework 4 benimsemeye karar kullanacağınıza karar WF4 için Taşı'den ayrılmış (System.Activities.*) WF3 gelen (System.Workflow.\*). Bu konuda WF4 WF3 ile çalışma hakkında bilgi sağlayan WF geçiş kılavuzuna bağlantılar sağlar.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>WF geçiş teknik incelemeler ve tarif kitapları  
 [WF geçişine genel bakış](https://go.microsoft.com/fwlink/?LinkId=153873) konu WF3 ve WF4 ve geçiş stratejileri arasındaki ilişkiyi geniş kapsamlı bir genel bakış sağlar. Yardımcısı konuları belirli konulara detayına gidin.  
  
 [WF geçişine genel bakış](https://go.microsoft.com/fwlink/?LinkId=153873)  
 WF3 WF4 ve bir kullanıcı veya iş akışı teknoloji .NET 4'teki olası bir kullanıcı olarak sahip olduğunuz seçenekler arasındaki ilişkiyi açıklar.  
  
 [WF geçişi: WF3 geliştirme için en iyi uygulamalar](https://go.microsoft.com/fwlink/?LinkId=153852)  
 WF3 yapıtları WF4 için daha kolay geçirilebilecek şekilde tasarlamak nasıl ele alınmaktadır.  
  
 [WF kılavuz: kuralları](https://go.microsoft.com/fwlink/?LinkId=153854)  
 Kuralları ile ilgili yatırım İleri Getir anlatılmaktadır [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] çözümler.  
  
 [WF kılavuz: Durum makinesi](https://go.microsoft.com/fwlink/?LinkId=153855)  
 Bir Durum makinesi Etkinlik olmaması durumunda modelleme WF4 denetim akışı açıklanır.  
  
 Bu kılavuz yalnızca .NET Framework 4'ü hedefleyen iş akışı projeleri için geçerli olduğunu unutmayın. Durum makine iş akışları .NET 4.0.1'in Platform güncelleştirme 1 sürümünde eklenmiştir ve .NET Framework 4. 5 ' bir parçası olarak dahil. .NET 4.0.1'in - 4.0.3 ve .NET Framework 4.5, durum makine iş akışları hakkında daha fazla bilgi için bkz. [4.0.1'in güncelleştirmek için Microsoft .NET Framework 4 özellikleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) ve [durum makine iş akışları](state-machine-workflows.md).  
  
 [WF geçiş Kitapçığı: Özel etkinlikler](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Örnekler ve yeniden tasarlanmasını WF4 WF3 özel etkinliklere yönelik yönergeler sağlar.  
  
 [WF geçiş Kitapçığı: Gelişmiş özel etkinlikler](https://go.microsoft.com/fwlink/?LinkId=275560)  
 WF3 kuyrukları kullanan gelişmiş WF3 özel etkinlikler ve zamanlama çocuk etkinliklerinin WF4 özel etkinlikler olarak yeniden tasarlanmasını yönelik rehberlik sağlar.  
  
 [WF geçiş Kitapçığı: İş akışları](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Örnekler ve WF4 WF3 iş akışlarında yeniden tasarlanmasını için yönergeler sağlar.  
  
 [WF geçiş Kitapçığı: İş akışı barındırma](https://go.microsoft.com/fwlink/?LinkId=275561)  
 WF3 barındırma kodu WF4 barındırma kodu olarak yeniden tasarlanmasını yönelik rehberlik sağlar. İş akışı barındırma WF3 ve WF4 arasında anahtar farklılıkları kapsar olmaktır.  
  
 [WF geçiş Kitapçığı: İş akışı izleme](https://go.microsoft.com/fwlink/?LinkId=275562)  
 WF3 izleme kod ve yapılandırma eşdeğer WF4 izleme kodu ve yapılandırması kullanarak yeniden tasarlanmasını yönelik rehberlik sağlar.  
  
 [WF kılavuz: İş akışı Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=275564)  
 (Genellikle iş akışı hizmetleri adlandırılır) Windows Communication Foundation (WCF) web hizmetlerini WF3 WF4, yaygın senaryoları için kullanıma hazır kullanılmak üzere oluşturulan uygulamayı iş akışlarını yeniden tasarlanmasını örnek yönelik adım adım yönergeler sağlar etkinlikler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Activities.Statements.Interop>
