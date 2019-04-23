---
title: Sürüm 3.5’teki Yuva Performansı Geliştirmeleri
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 28f2543d1f8c81efd32ffbb644265fb5709a9bb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333294"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Sürüm 3.5’teki Yuva Performansı Geliştirmeleri
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> Sınıfı geliştirilmiştir sürüm 3.5 kullanmak için en yüksek performans elde etmek için zaman uyumsuz ağ g/ç kullanan uygulamalar tarafından. Yeni sınıflar birtakım geliştirmeler kümesinin bir parçası olarak eklenmiştir <xref:System.Net.Sockets.Socket> özel yüksek performanslı yuva uygulamaları tarafından kullanılabilecek bir diğer zaman uyumsuz desen sağlayan sınıf. Bu geliştirmeler, yüksek performans gerektiren ağ sunucu uygulamaları için özel olarak tasarlanmıştır. Bir uygulama Gelişmiş zaman uyumsuz desen özel olarak kullanabilirsiniz ya da yalnızca kendi uygulama sık erişimli alanlarını (büyük miktarlarda veri, örneğin alırken) hedeflenen.  
  
## <a name="class-enhancements"></a>Sınıf geliştirmeleri  
 Bu geliştirmeler'in ana özelliği mahal vermemek yinelenen ayırma ve nesne eşitleme sırasında yüksek hacimli zaman uyumsuz yuva g/ç ' dir. Şu anda tarafından uygulanan başlangıç/bitiş tasarım deseni <xref:System.Net.Sockets.Socket> zaman uyumsuz yuva g/ç gerektiren için sınıf bir <xref:System.IAsyncResult?displayProperty=nameWithType> nesne her zaman uyumsuz yuva işlem için ayrılan.  
  
 Yeni <xref:System.Net.Sockets.Socket> sınıfı geliştirmeleri, zaman uyumsuz yuva işlemleri tarafından yeniden kullanılabilir açıklanan <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> sınıfı ayrılan ve uygulama tarafından korunan nesneler. Yüksek performanslı yuva uygulamaları en iyi Sürdürülen gerekir çakışan yuva operations miktarını bildirin. Uygulama, çok oluşturabilirsiniz <xref:System.Net.Sockets.SocketAsyncEventArgs> ihtiyaç duyduğu nesneleri. Örneğin, bir sunucu uygulaması bekleyen işlemleri gelen istemci bağlantı hızları desteklemek için her zaman kabul 15 yuva olması gerekiyorsa, bunu yeniden kullanılabilir 15 ayırabilirsiniz <xref:System.Net.Sockets.SocketAsyncEventArgs> bu amaç için nesneleri.  
  
 Desen ile bu sınıf bir zaman uyumsuz yuva işlemi gerçekleştirmek için aşağıdaki adımlardan oluşur:  
  
1. Yeni bir ayırma <xref:System.Net.Sockets.SocketAsyncEventArgs> bağlam nesnesi veya bir uygulama havuzu ücretsiz bir tane alın.  
  
2. Bağlam özellikleri kümesi olarak (geri çağırma temsilci yöntemi ve veri arabelleği, örneğin) gerçekleştirilen hakkında işlemi için nesne.  
  
3. Zaman uyumsuz işlemi başlatmak için uygun yuva yöntemi (xxxAsync) çağırın.  
  
4. Zaman uyumsuz yuva yöntemi (xxxAsync) geri aramada true döndürürse, bağlam özelliklerini tamamlama durumu için sorgu.  
  
5. Yuva zaman uyumsuz yöntem (xxxAsync) işleminin zaman uyumlu olarak tamamlanan geri aramada false döndürürse. Bağlam özelliklerini işlem sonucu sorgulanan.  
  
6. Başka bir işlem bağlamı yeniden, havuzda bulunan put veya atmak.  
  
 Yeni zaman uyumsuz yuva işlemi bağlam nesnesinin yaşam süresi, uygulama kodundaki başvuruları ve zaman uyumsuz g/ç başvuruları tarafından belirlenir. Uygulamanın zaman uyumsuz yuva işlemi yöntemlerinden biri olan bir parametre olarak gönderildikten sonra bir zaman uyumsuz yuva işlemi bağlam nesnesine bir başvuru korumak gerekli değildir. Tamamlama geri dönene kadar başvurulan kalır. Ancak uygulama, böylece gelecekteki zaman uyumsuz yuva işlemi için yeniden kullanılabilir içerik nesnesine başvuru korumak avantajlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)
- [Yuva Kod Örnekleri](socket-code-examples.md)
