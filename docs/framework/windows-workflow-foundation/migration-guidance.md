---
title: Geçiş Kılavuzu
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 16f725dcb5d6f6e5d06771b7836fa187be005910
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559206"
---
# <a name="migration-guidance"></a>Geçiş Kılavuzu

.NET Framework 4 ' te, Microsoft, Windows Workflow Foundation (WF) ikinci ana sürümünü serbest bırakmadır. [!INCLUDE[wf1](../../../includes/wf1-md.md)] , WinFX 'de yayımlanmıştır (System. Workflow. \* namespaces; WF3 olarak anılacaktır) ve .NET Framework 3,5 ' de geliştirilmiştir. WF3 ayrıca .NET Framework 4 ' ün bir parçasıdır, ancak yeni iş akışı teknolojisinin (System. Activities. \* namespaces; WF4 olarak adlandırılır) yanı sıra bu şekilde bulunur. WF4 ne zaman benimseneceği düşünürken, öncelikle zamanlamayı denetlemenizi öneririz.  
  
- WF3, .NET Framework 4 ' ün tam olarak desteklenen bir parçasıdır.  
  
- WF3 uygulamaları değişiklik yapılmadan .NET Framework 4 üzerinde çalışır ve tam olarak desteklenmeye devam eder.  
  
- Yeni WF3 uygulamaları oluşturulabilir ve var olan uygulamalarınız Visual Studio 2012 ' de düzenlenebilir ve tam olarak desteklenmektedir.  
  
 Bu nedenle, .NET Framework 4 ' ü benimsemeye yönelik karar, \* WF3 (System. Workflow.) ÖĞESINDEN WF4 (System. Activities.) öğesine geçme kararına göre belirlenir \* . Bu konuda, WF3 ve WF4 ile çalışma hakkında bilgi sağlayan WF geçiş kılavuzunun bağlantıları sağlanmaktadır.  
  
## <a name="wf-migration-white-papers-and-cookbooks"></a>WF geçişi Teknik İncelemeleri ve tanıtım defterleri

 [WF geçişine genel bakış](/previous-versions/appfabric/ff383417(v=azure.10)) konusu WF3 ve WF4 ile geçiş stratejileri arasındaki ilişkiye yönelik kapsamlı bir genel bakış sunar. Yardımcı konular belirli konularda detaya gitme.  
  
 [WF geçişine genel bakış](/previous-versions/appfabric/ff383417(v=azure.10))  
 WF3 ve WF4 arasındaki ilişkiyi ve .NET 4 ' te bir kullanıcı veya iş akışı teknolojisinin potansiyel bir kullanıcısı olan seçenekleri açıklar.  
  
 [WF geçişi: WF3 geliştirmesi için En Iyi uygulamalar](/previous-versions/appfabric/ff383417(v=azure.10))  
 WF4 'e daha kolay geçirilebilecek şekilde WF3 yapıtları nasıl tasarlayabileceğinizi açıklar.  
  
 [WF Kılavuzu: kurallar](/previous-versions/appfabric/ff383417(v=azure.10))  
 Kurallarla ilgili yatırımların .NET Framework 4 ' e nasıl bir araya getirileceğini açıklar.  
  
 [WF Kılavuzu: durum makinesi](/previous-versions/appfabric/ff383417(v=azure.10))  
 Bir durum makinesi etkinliğinin yokluğu olarak WF4 denetim akışı modellemesini açıklar.  
  
 Bu kılavuzun yalnızca .NET Framework 4 ' ü hedefleyen iş akışı projelerine uygulandığını unutmayın. Durum makinesi iş akışları, Platform Güncelleştirme 1 ' in sürümü ile .NET 4.0.1 'ye eklenmiştir ve .NET Framework 4,5 ' nin bir parçası olarak eklenmiştir. .NET 4.0.1-4.0.3 ve .NET Framework 4,5 ' deki durum makinesi iş akışları hakkında daha fazla bilgi için, bkz. [Update 4.0.1 for Microsoft .NET Framework 4 Özellikler](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) ve [durum makine iş akışları](state-machine-workflows.md).  
  
 [WF geçişi kılavuz kitabı: özel etkinlikler](/previous-versions/appfabric/ff383417(v=azure.10))  
 WF4 üzerinde WF3 özel etkinliklerini yeniden tasarlamaya yönelik örnekler ve yönergeler sağlar.  
  
 [WF geçişi kılavuz kitabı: Gelişmiş özel etkinlikler](/previous-versions/appfabric/ff383417(v=azure.10))  
 WF3 kuyruklarını kullanan ve alt etkinlikleri WF4 özel etkinlikler olarak zamanlayan gelişmiş WF3 özel etkinliklerini yeniden tasarlamaya yönelik rehberlik sağlar.  
  
 [WF geçişi kılavuz kitabı: Iş akışları](/previous-versions/appfabric/ff383417(v=azure.10))  
 WF4 üzerinde WF3 iş akışlarını yeniden tasarlamaya yönelik örnekler ve yönergeler sağlar.  
  
 [WF geçişi kılavuz kitabı: Iş akışı barındırma](/previous-versions/appfabric/ff383417(v=azure.10))  
 WF4 barındırma kodu olarak WF3 barındırma kodu yeniden tasarlanmasıyla ilgili rehberlik sağlar. Amaç, WF3 ve WF4 arasında iş akışı barındırma içindeki temel farklılıkları kapsamaktır.  
  
 [WF geçişi kılavuz kitabı: Iş akışı Izleme](/previous-versions/appfabric/ff383417(v=azure.10))  
 Eşdeğer WF4 izleme kodu ve yapılandırması kullanılarak WF3 izleme kodu ve yapılandırmasını yeniden tasarlamaya yönelik rehberlik sağlar.  
  
 [WF Kılavuzu: Iş akışı hizmetleri](/previous-versions/appfabric/ff383417(v=azure.10))  
 Hazır etkinlikler için yaygın senaryolar için WF3 içinde oluşturulan Windows Communication Foundation (WCF) Web Hizmetleri (yaygın olarak iş akışı hizmetleri olarak adlandırılır) uygulayan iş akışlarını yeniden tasarlamak için örnek yönelimli adım adım yönergeler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Interop>
