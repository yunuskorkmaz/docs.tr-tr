---
title: Geçiş Kılavuzu
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: f0c21d32b745a51bada9133230dd0c87be9c915e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937964"
---
# <a name="migration-guidance"></a>Geçiş Kılavuzu

.NET Framework 4 ' te, Microsoft, Windows Workflow Foundation (WF) ikinci ana sürümünü serbest bırakmadır. [!INCLUDE[wf1](../../../includes/wf1-md.md)], WinFX 'de yayımlanmıştır (System. Workflow.\* ad alanlarında bulunan türleri; artık WF3 olarak anılır) ve .NET Framework 3,5 ' de geliştirildi. WF3 ayrıca .NET Framework 4 ' ün bir parçasıdır, ancak yeni iş akışı teknolojisinin (System. Activities.\* ad alanlarında bulunan türler) (WF4 olarak adlandırılır) bulunur. WF4 ne zaman benimseneceği düşünürken, öncelikle zamanlamayı denetlemenizi öneririz.  
  
- WF3, .NET Framework 4 ' ün tam olarak desteklenen bir parçasıdır.  
  
- WF3 uygulamaları değişiklik yapılmadan .NET Framework 4 üzerinde çalışır ve tam olarak desteklenmeye devam eder.  
  
- Yeni WF3 uygulamaları oluşturulabilir ve var olan uygulamalarınız Visual Studio 2012 ' de düzenlenebilir ve tam olarak desteklenmektedir.  
  
 Bu nedenle, .NET Framework 4 ' ü benimsemeye yönelik karar, WF3 (System. Workflow.\*) öğesinden WF4 (System. Activities.\*) öğesine geçme kararına göre belirlenir. Bu konuda, WF3 ve WF4 ile çalışma hakkında bilgi sağlayan WF geçiş kılavuzunun bağlantıları sağlanmaktadır.  
  
## <a name="wf-migration-white-papers-and-cookbooks"></a>WF geçişi Teknik İncelemeleri ve tanıtım defterleri

 [WF geçişine genel bakış](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)) konusu WF3 ve WF4 ile geçiş stratejileri arasındaki ilişkiye yönelik kapsamlı bir genel bakış sunar. Yardımcı konular belirli konularda detaya gitme.  
  
 [WF geçişine genel bakış](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 WF3 ve WF4 arasındaki ilişkiyi ve .NET 4 ' te bir kullanıcı veya iş akışı teknolojisinin potansiyel bir kullanıcısı olan seçenekleri açıklar.  
  
 [WF geçişi: WF3 geliştirmesi için En Iyi uygulamalar](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 WF4 'e daha kolay geçirilebilecek şekilde WF3 yapıtları nasıl tasarlayabileceğinizi açıklar.  
  
 [WF Kılavuzu: kurallar](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Kurallarla ilgili yatırımların .NET Framework 4 ' e nasıl bir araya getirileceğini açıklar.  
  
 [WF Kılavuzu: durum makinesi](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Bir durum makinesi etkinliğinin yokluğu olarak WF4 denetim akışı modellemesini açıklar.  
  
 Bu kılavuzun yalnızca .NET Framework 4 ' ü hedefleyen iş akışı projelerine uygulandığını unutmayın. Durum makinesi iş akışları, Platform Güncelleştirme 1 ' in sürümü ile .NET 4.0.1 'ye eklenmiştir ve .NET Framework 4,5 ' nin bir parçası olarak eklenmiştir. .NET 4.0.1-4.0.3 ve .NET Framework 4,5 ' deki durum makinesi iş akışları hakkında daha fazla bilgi için, bkz. [Update 4.0.1 for Microsoft .NET Framework 4 Özellikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) ve [durum makine iş akışları](state-machine-workflows.md).  
  
 [WF geçişi kılavuz kitabı: özel etkinlikler](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 WF4 üzerinde WF3 özel etkinliklerini yeniden tasarlamaya yönelik örnekler ve yönergeler sağlar.  
  
 [WF geçişi kılavuz kitabı: Gelişmiş özel etkinlikler](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 WF3 kuyruklarını kullanan ve alt etkinlikleri WF4 özel etkinlikler olarak zamanlayan gelişmiş WF3 özel etkinliklerini yeniden tasarlamaya yönelik rehberlik sağlar.  
  
 [WF geçişi kılavuz kitabı: Iş akışları](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 WF4 üzerinde WF3 iş akışlarını yeniden tasarlamaya yönelik örnekler ve yönergeler sağlar.  
  
 [WF geçişi kılavuz kitabı: Iş akışı barındırma](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 WF4 barındırma kodu olarak WF3 barındırma kodu yeniden tasarlanmasıyla ilgili rehberlik sağlar. Amaç, WF3 ve WF4 arasında iş akışı barındırma içindeki temel farklılıkları kapsamaktır.  
  
 [WF geçişi kılavuz kitabı: Iş akışı Izleme](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Eşdeğer WF4 izleme kodu ve yapılandırması kullanılarak WF3 izleme kodu ve yapılandırmasını yeniden tasarlamaya yönelik rehberlik sağlar.  
  
 [WF Kılavuzu: Iş akışı hizmetleri](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 WF3 ' de oluşturulan Windows Communication Foundation (WCF) Web Hizmetleri (yaygın olarak iş akışı hizmetleri olarak adlandırılır) uygulayan iş akışlarını yeniden tasarlamak için, kullanıma hazır olan yaygın senaryolar için örnek yönelimli adım adım yönergeler sağlar işlemleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Interop>
