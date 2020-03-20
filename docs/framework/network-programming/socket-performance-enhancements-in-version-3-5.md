---
title: Sürüm 3.5’teki Yuva Performansı Geliştirmeleri
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 577c033fc5639f9d9f50e413fd2cb55a75d48f2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047239"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Sürüm 3.5’teki Yuva Performansı Geliştirmeleri
Sınıf, <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> en yüksek performansı elde etmek için eşzamanlı ağ G/Ç kullanan uygulamalar tarafından kullanılmak üzere Sürüm 3.5'te geliştirilmiştir. Özel leştirilmiş yüksek performanslı soket uygulamaları tarafından kullanılabilecek <xref:System.Net.Sockets.Socket> alternatif bir eşzamanlı desen sağlayan sınıfa bir dizi geliştirmenin parçası olarak bir dizi yeni sınıf eklendi. Bu geliştirmeler, yüksek performans gerektiren ağ sunucusu uygulamaları için özel olarak tasarlanmıştır. Bir uygulama yalnızca gelişmiş eşzamanlı deseni kullanabilir veya yalnızca uygulamanın hedeflenen sıcak alanlarında (örneğin, büyük miktarda veri alırken).  
  
## <a name="class-enhancements"></a>Sınıf Geliştirmeleri  
 Bu geliştirmelerin temel özelliği, yüksek hacimli asynchronous soket G/Ç sırasında nesnelerin tekrarlanan ayırma ve eşitlemeden kaçınmasIdır. Şu anda <xref:System.Net.Sockets.Socket> sınıf tarafından asynchronous soket G/Ç için <xref:System.IAsyncResult?displayProperty=nameWithType> uygulanan Begin/End tasarım deseni, her bir eşzamanlı soket işlemi için bir nesne ayrılmasını gerektirir.  
  
 Yeni <xref:System.Net.Sockets.Socket> sınıf geliştirmelerinde, eşzamanlı soket işlemleri, uygulama tarafından <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> ayrılan ve sürdürülen yeniden kullanılabilir sınıf nesneleri tarafından tanımlanır. Yüksek performanslı soket uygulamaları, sürdürülmesi gereken çakışan soket işlemlerinin miktarını en iyi şekilde bilir. Uygulama, ihtiyaç duyduğu nesnelerin <xref:System.Net.Sockets.SocketAsyncEventArgs> çoğunu oluşturabilir. Örneğin, bir sunucu uygulamasının gelen istemci bağlantı oranlarını desteklemek için her zaman bekleyen işlemleri kabul etmek için <xref:System.Net.Sockets.SocketAsyncEventArgs> 15 sokete sahip olması gerekiyorsa, bu amaçla 15 yeniden kullanılabilir nesne ayırabilir.  
  
 Bu sınıfla bir eşzamanlı soket işlemi gerçekleştirmek için desen aşağıdaki adımlardan oluşur:  
  
1. Yeni <xref:System.Net.Sockets.SocketAsyncEventArgs> bir bağlam nesnesi tahsis edin veya uygulama havuzundan ücretsiz bir nesne alın.  
  
2. Yapılmak üzere olan işlem için bağlam nesnesi üzerindeki özellikleri ayarlama (örneğin geri arama temsilcisi yöntemi ve veri arabelleği).  
  
3. Eşzamanlı işlemi başlatmak için uygun soket yöntemini (xxxAsync) çağırın.  
  
4. Asynchronous soket yöntemi (xxxAsync) geri aramadoğru döndürür, tamamlama durumu için bağlam özelliklerini sorgun.  
  
5. Asynchronous soket yöntemi (xxxAsync) geri aramada yanlış dönerse, işlem eşzamanlı olarak tamamlanır. İçerik özellikleri işlem sonucu için sorgulanabilir.  
  
6. Başka bir işlem için bağlamı yeniden kullanın, havuza geri koyun veya atın.  
  
 Yeni asynchronous soket çalışma bağlamı nesnesinin ömrü, uygulama kodundaki referanslar ve eşzamanlı G/Ç referansları ile belirlenir. Uygulamanın, asynchronous soket çalışma yöntemlerinden birine parametre olarak gönderildikten sonra bir asynchronous soket çalışma bağlamı nesnesine başvuruda bulunmaları gerekli değildir. Tamam geri arama dönene kadar başvurulan kalır. Ancak uygulamanın bağlam nesnesine başvuruyu tutması avantajlıdır, böylece gelecekteki bir eşzamanlı soket çalışması için yeniden kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [Ağ Programlama Örnekleri](network-programming-samples.md)
- [Yuva Kod Örnekleri](socket-code-examples.md)
