---
title: Geçiş Kılavuzu
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 45f81b29f63701f690e396de2e9834f9933fd775
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796809"
---
# <a name="migration-guidance"></a>Geçiş Kılavuzu
[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]' De, Microsoft Windows Workflow Foundation (WF) uygulamasının ikinci ana sürümünü serbest bırakmadır. [!INCLUDE[wf1](../../../includes/wf1-md.md)], WinFX 'de yayımlanmıştır (System. Workflow.\* namespaces; WF3 olarak anılır) ve içinde [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]geliştirildi. WF3 ayrıca, öğesinin bir [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]parçasıdır, ancak yeni iş akışı teknolojisinin (System. Activities.\* namespaces; WF4 olarak adlandırılır) yanı sıra bu şekilde bulunur. WF4 ne zaman benimseneceği düşünürken, öncelikle zamanlamayı denetlemenizi öneririz.  
  
- WF3, [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]öğesinin tam olarak desteklenen bir parçasıdır.  
  
- WF3 uygulamaları değişiklik [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] yapılmadan çalışır ve tam olarak desteklenmeye devam eder.  
  
- Yeni WF3 uygulamaları oluşturulabilir ve var olan uygulamalarınız Visual Studio 2012 ' de düzenlenebilir ve tam olarak desteklenmektedir.  
  
 Bu nedenle, .NET Framework 4 ' ü benimsemeye yönelik karar, WF3 (System. Workflow.\*\*) öğesinden WF4 (System. Activities.) öğesine geçme kararına göre belirlenir. Bu konuda, WF3 ve WF4 ile çalışma hakkında bilgi sağlayan WF geçiş kılavuzunun bağlantıları sağlanmaktadır.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>WF geçiş teknik Incelemeleri ve tanıtım Rehberleri  
 [WF geçişine genel bakış](https://go.microsoft.com/fwlink/?LinkId=153873) konusu WF3 ve WF4 ile geçiş stratejileri arasındaki ilişkiye yönelik kapsamlı bir genel bakış sunar. Yardımcı konular belirli konularda detaya gitme.  
  
 [WF geçişine genel bakış](https://go.microsoft.com/fwlink/?LinkId=153873)  
 WF3 ve WF4 arasındaki ilişkiyi ve .NET 4 ' te bir kullanıcı veya iş akışı teknolojisinin potansiyel bir kullanıcısı olan seçenekleri açıklar.  
  
 [WF geçişi: WF3 geliştirmesi için en iyi uygulamalar](https://go.microsoft.com/fwlink/?LinkId=153852)  
 WF4 'e daha kolay geçirilebilecek şekilde WF3 yapıtları nasıl tasarlayabileceğinizi açıklar.  
  
 [WF Kılavuzu: Kuralın](https://go.microsoft.com/fwlink/?LinkId=153854)  
 Kuralların ilgili yatırımlarını [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] çözümlere nasıl getirebileceğinizi açıklar.  
  
 [WF Kılavuzu: Durum makinesi](https://go.microsoft.com/fwlink/?LinkId=153855)  
 Bir durum makinesi etkinliğinin yokluğu olarak WF4 denetim akışı modellemesini açıklar.  
  
 Bu kılavuzun yalnızca .NET Framework 4 ' ü hedefleyen iş akışı projelerine uygulandığını unutmayın. Durum makinesi iş akışları, Platform Güncelleştirme 1 ' in sürümü ile .NET 4.0.1 'ye eklenmiştir ve .NET Framework 4,5 ' nin bir parçası olarak eklenmiştir. .NET 4.0.1-4.0.3 ve .NET Framework 4,5 ' deki durum makinesi iş akışları hakkında daha fazla bilgi için, bkz. [Update 4.0.1 for Microsoft .NET Framework 4 Özellikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) ve [durum makine iş akışları](state-machine-workflows.md).  
  
 [WF geçişi kılavuz kitabı: Özel etkinlikler](https://go.microsoft.com/fwlink/?LinkId=153856)  
 WF4 üzerinde WF3 özel etkinliklerini yeniden tasarlamaya yönelik örnekler ve yönergeler sağlar.  
  
 [WF geçişi kılavuz kitabı: Gelişmiş özel etkinlikler](https://go.microsoft.com/fwlink/?LinkId=275560)  
 WF3 kuyruklarını kullanan ve alt etkinlikleri WF4 özel etkinlikler olarak zamanlayan gelişmiş WF3 özel etkinliklerini yeniden tasarlamaya yönelik rehberlik sağlar.  
  
 [WF geçişi kılavuz kitabı: Sürdürülen](https://go.microsoft.com/fwlink/?LinkId=153858)  
 WF4 üzerinde WF3 iş akışlarını yeniden tasarlamaya yönelik örnekler ve yönergeler sağlar.  
  
 [WF geçişi kılavuz kitabı: İş akışı barındırma](https://go.microsoft.com/fwlink/?LinkId=275561)  
 WF4 barındırma kodu olarak WF3 barındırma kodu yeniden tasarlanmasıyla ilgili rehberlik sağlar. Amaç, WF3 ve WF4 arasında iş akışı barındırma içindeki temel farklılıkları kapsamaktır.  
  
 [WF geçişi kılavuz kitabı: İş akışı Izleme](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Eşdeğer WF4 izleme kodu ve yapılandırması kullanılarak WF3 izleme kodu ve yapılandırmasını yeniden tasarlamaya yönelik rehberlik sağlar.  
  
 [WF Kılavuzu: İş akışı hizmetleri](https://go.microsoft.com/fwlink/?LinkId=275564)  
 WF3 ' de oluşturulan Windows Communication Foundation (WCF) Web Hizmetleri (yaygın olarak iş akışı hizmetleri olarak adlandırılır) uygulayan iş akışlarını yeniden tasarlamak için, kullanıma hazır olan yaygın senaryolar için örnek yönelimli adım adım yönergeler sağlar işlemleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Interop>
