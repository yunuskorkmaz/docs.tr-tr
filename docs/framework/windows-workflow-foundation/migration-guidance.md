---
title: "Geçiş Kılavuzu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04c63754960dca44558d888b8ce357220562ea7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="migration-guidance"></a>Geçiş Kılavuzu
İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ikinci ana sürümüne yönelik Microsoft serbest bırakma [!INCLUDE[wf](../../../includes/wf-md.md)]. [!INCLUDE[wf1](../../../includes/wf1-md.md)]içinde yayımlanan [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (Bu System.Workflow.* ad alanlarında türleri dahil; şimdi WF3 adlandırılır) ve geliştirilmiş içinde [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. WF3 olduğu da parçası [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ancak yanı sıra yeni iş akışı teknolojisi vardır (System.Activities. türlerinde\* ad alanları; için WF4 adlandırılır). WF4 benimsemek ne zaman değerlendirirken zamanlamasını denetlemek ilk bilmek önemlidir.  
  
-   WF3 tam olarak desteklenen bir parçası olan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
-   WF3 uygulamaları çalıştıracağınız [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] değişiklik yapmadan ve tam olarak desteklemeye devam eder.  
  
-   Yeni WF3 uygulamaları oluşturulabilir ve var olan uygulamalarınız içinde düzenlenebilir [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ve tam olarak desteklenir.  
  
 Bu nedenle, .NET Framework 4 benimsemeye karar WF4 için taşımaya karar den düşünülebilir (System.Activities.*) WF3 gelen (System.Workflow.\*). Bu konuda WF3 ve WF4 ile çalışma hakkında bilgi sağlar WF geçiş yönergelere bağlantılar sağlar.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>WF geçiş teknik incelemeler ve Cookbooks  
 [WF geçişine genel bakış](http://go.microsoft.com/fwlink/?LinkId=153873) konu WF3 ve WF4 ve geçiş stratejileri arasındaki ilişkinin kapsamlı bir genel bakış sağlar. Yardımcısı konuları belirli konulara ayrıntıya.  
  
 [WF geçişine genel bakış](http://go.microsoft.com/fwlink/?LinkId=153873)  
 WF3 ve WF4 ve bir kullanıcı veya iş akışı teknolojisinin .NET 4'te olası bir kullanıcı olarak sahip seçenekleri arasındaki ilişkiyi açıklar.  
  
 [WF geçişi: WF3 geliştirme için en iyi yöntemler](http://go.microsoft.com/fwlink/?LinkId=153852)  
 WF4 için daha kolay geçirilebilecek şekilde WF3 yapıları tasarlamak nasıl ele alınmaktadır.  
  
 [WF Kılavuzu: kuralları](http://go.microsoft.com/fwlink/?LinkId=153854)  
 Kuralları ile ilgili Yatırımlar İleri içine nasıl ele [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] çözümler.  
  
 [WF Kılavuzu: Durum makinesi](http://go.microsoft.com/fwlink/?LinkId=153855)  
 Durum makinesinin Etkinlik olmaması durumunda modelleme WF4 denetim akışı açıklanır.  
  
 Bu kılavuz yalnızca .NET Framework 4 hedefleyen iş akışı projeler için geçerlidir. Durum makinesi iş akışları .NET 4.0.1 Platform güncelleştirme 1'in çıkışıyla eklenmiştir ve .NET Framework 4. 5 ' bir parçası olarak dahil. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Durum makinesi .NET 4.0.1 - 4.0.3 ve .NET Framework 4.5, iş akışlarında bkz [4.0.1 Microsoft .NET Framework 4 özellikleri için güncelleştirme](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) ve [durumu makine iş akışları](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
 [WF Geçiş Kılavuzu: Özel etkinlikler](http://go.microsoft.com/fwlink/?LinkId=153856)  
 Örnekler ve WF4 WF3 özel etkinlikleri yeniden için yönergeler sağlar.  
  
 [WF Geçiş Kılavuzu: Özel etkinlikler Gelişmiş](http://go.microsoft.com/fwlink/?LinkId=275560)  
 WF3 kuyrukları kullanan gelişmiş WF3 özel etkinlikler ve zamanlama alt etkinlikleri WF4 özel etkinlikler olarak yeniden ilişkin yönergeler sağlar.  
  
 [WF Geçiş Kılavuzu: iş akışları](http://go.microsoft.com/fwlink/?LinkId=153858)  
 Örnekler ve WF4 WF3 iş akışlarında yeniden için yönergeler sağlar.  
  
 [WF Geçiş Kılavuzu: İş akışı barındırma](http://go.microsoft.com/fwlink/?LinkId=275561)  
 WF3 barındırma kodu WF4 barındırma kodu olarak yeniden ilişkin yönergeler sağlar. İş akışı barındırma WF3 ve WF4 temel farklılıkları kapsayacak şekilde belirtilir.  
  
 [WF Geçiş Kılavuzu: İş akışı izleme](http://go.microsoft.com/fwlink/?LinkId=275562)  
 WF3 izleme kodu ve eşdeğer WF4 izleme kodunu ve yapılandırma kullanarak yapılandırmayı yeniden ilişkin yönergeler sağlar.  
  
 [WF Kılavuzu: İş akışı Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=275564)  
 (Genellikle iş akışı Hizmetleri olarak adlandırılır) Windows Communication Foundation (WCF) web hizmetlerini out-of-box için genel senaryolar için WF4, kullanılacak WF3 oluşturulan uygulama iş akışlarını yeniden örnek yönelik adım adım yönergeler sağlar etkinlikler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Statements.Interop>
