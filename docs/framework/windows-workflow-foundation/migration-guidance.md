---
title: Geçiş Kılavuzu
description: 'Daha fazla bilgi edinin: geçiş kılavuzu'
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 83c6af4d8eed396501aafc568de8e64d30ae7cfe
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104867"
---
# <a name="migration-guidance"></a>Geçiş kılavuzu

.NET Framework 4 ' te, Microsoft, Windows Workflow Foundation (WF) ikinci ana sürümünü yayımladı. [!INCLUDE[wf1](../../../includes/wf1-md.md)] , WinFX 'de yayımlanmıştır (System. Workflow. \* namespaces; WF3 olarak anılacaktır) ve .NET Framework 3,5 ' de geliştirilmiştir. WF3 ayrıca .NET Framework 4 ' ün bir parçasıdır, ancak yeni iş akışı teknolojisinin (System. Activities. \* namespaces; WF4 olarak adlandırılır) yanı sıra bu şekilde bulunur. WF4 ne zaman benimseneceği düşünürken, öncelikle zamanlamayı denetlemenizi öneririz.

- WF3, .NET Framework 4 ' ün tam olarak desteklenen bir parçasıdır.

- WF3 uygulamaları değişiklik yapılmadan .NET Framework 4 ' te çalışır ve tam olarak desteklenmeye devam eder.

- Yeni WF3 uygulamaları oluşturulabilir ve var olan uygulamalarınız Visual Studio 2012 ' de düzenlenebilir ve tam olarak desteklenmektedir.

Bu nedenle, .NET Framework 4 benimseme kararı, \* WF3 (System. Workflow.) ÖĞESINDEN WF4 (System. Activities.) ' e geçmek için kararınızdan ayrılır \* . Bu konuda, WF3 ve WF4 ile çalışma hakkında bilgi sağlayan WF geçiş kılavuzunun bağlantıları sağlanmaktadır.

## <a name="wf-migration-white-papers-and-cookbooks"></a>WF geçişi Teknik İncelemeleri ve tanıtım defterleri

 [WF geçişine genel bakış](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Overview.docx)\
 WF3 ile WF4 arasındaki ilişkiyi ve .NET Framework 4 ' te bir kullanıcı veya bir iş akışı teknolojisinin olası bir kullanıcısı olan seçenekleri açıklar.

 [WF geçişi: WF3 geliştirmesi için En Iyi uygulamalar](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Best%20Practices.docx)\
 WF4 'e daha kolay geçirilebilecek şekilde WF3 yapıtları nasıl tasarlayabileceğinizi açıklar.

 [WF Kılavuzu: kurallar](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF4%20Rules%20Guidance.docx)\
 Kurallarla ilgili yatırımların .NET Framework 4 ' e nasıl bir araya getirileceğini açıklar.

 [WF Kılavuzu: durum makinesi](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF4%20State%20Machine%20Guidance.doc) State-Machine etkinlik yokluğunda WF4 denetim akışı modellemesini açıklar. Bu kılavuz yalnızca .NET Framework 4 ' ü hedefleyen iş akışı projelerine uygulanır. Durum makinesi iş akışları, Platform Güncelleştirme 1 ' in sürümü ile .NET Framework 4.0.1 eklenmiştir ve .NET Framework 4,5 ' nin bir parçası olarak eklenmiştir. .NET Framework 4.0.1-4.0.3 ve .NET Framework 4,5 ' deki durum makinesi iş akışları hakkında daha fazla bilgi için bkz. [Update 4.0.1 for Microsoft .NET Framework 4 özellikleri](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) ve [durum makine iş akışları](state-machine-workflows.md).

 [WF geçişi kılavuz kitabı: özel etkinlikler](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Custom%20Activities.docx)\
 WF4 üzerinde WF3 özel etkinliklerini yeniden tasarlamaya yönelik örnekler ve yönergeler sağlar.

 [WF geçişi kılavuz kitabı: Gelişmiş özel etkinlikler](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Advanced%20Custom%20Activities.docx)\
 WF3 kuyruklarını kullanan ve alt etkinlikleri WF4 özel etkinlikler olarak zamanlayan gelişmiş WF3 özel etkinliklerini yeniden tasarlamaya yönelik rehberlik sağlar.
%20 [WF geçişi kılavuz kitabı: Iş akışları](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Workflows.docx)\
 WF4 üzerinde WF3 iş akışlarını yeniden tasarlamaya yönelik örnekler ve yönergeler sağlar.

 [WF geçişi kılavuz kitabı: Iş akışı barındırma](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Workflow%20Hosting.docx)\
 WF4 barındırma kodu olarak WF3 barındırma kodu yeniden tasarlanmasıyla ilgili rehberlik sağlar. Amaç, WF3 ve WF4 arasında iş akışı barındırma içindeki temel farklılıkları kapsamaktır.

 [WF geçişi kılavuz kitabı: Iş akışı Izleme](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Workflow%20Tracking.docx)\
 Eşdeğer WF4 izleme kodu ve yapılandırması kullanılarak WF3 izleme kodu ve yapılandırmasını yeniden tasarlamaya yönelik rehberlik sağlar.

 [WF Kılavuzu: Iş akışı hizmetleri](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF4%20Workflow%20Services%20Guidance.docx)\
 Hazır etkinlikler için yaygın senaryolar için WF3 içinde oluşturulan Windows Communication Foundation (WCF) Web Hizmetleri (yaygın olarak iş akışı hizmetleri olarak adlandırılır) uygulayan iş akışlarını yeniden tasarlamak için örnek yönelimli adım adım yönergeler sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Interop>
