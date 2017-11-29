---
title: "Sürüm 3.5 yuva performans geliştirmeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d4746e2303949ddeabee36e4875e7480467f33e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="socket-performance-enhancements-in-version-35"></a>Sürüm 3.5 yuva performans geliştirmeleri
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> Sınıfı geliştirilmiştir sürüm 3.5 kullanmak için en yüksek performans elde etmek için zaman uyumsuz ağ g/ç kullanan uygulamalar tarafından. Bir dizi yeni sınıflar, geliştirmeler kümesinin bir parçası olarak eklenmiştir <xref:System.Net.Sockets.Socket> özel yüksek performanslı yuva uygulamaları tarafından kullanılan bir alternatif zaman uyumsuz desen sağlayan sınıf. Bu geliştirmeler, yüksek performans gerektiren ağ sunucu uygulamaları için özel olarak tasarlanmıştır. Bir uygulama Gelişmiş zaman uyumsuz desen özel olarak kullanabilir veya yalnızca kendi uygulama etkin alanlarını (büyük miktarlarda verinin, örneğin alırken) hedeflenen.  
  
## <a name="class-enhancements"></a>Sınıf geliştirmeleri  
 Ana, bu geliştirmeler yinelenen ayırma kaçınma ve nesneleri eşitleme yüksek hacimli zaman uyumsuz yuva g/ç sırasında özelliğidir. Şu anda tarafından uygulanan başlangıç/bitiş tasarım deseni <xref:System.Net.Sockets.Socket> zaman uyumsuz yuva g/ç gerektirir sınıfı bir <xref:System.IAsyncResult?displayProperty=nameWithType> nesne için her zaman uyumsuz yuva işlemi ayrılan.  
  
 Yeni <xref:System.Net.Sockets.Socket> sınıf geliştirmeleri, zaman uyumsuz yuva işlemleri tarafından yeniden kullanılabilir açıklanan <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> sınıf ayrılmış ve uygulama tarafından korunan nesneler. Yüksek performanslı yuva uygulamaları en iyi Sürdürülen gerekir çakışan yuva işlemleri miktarını bilirsiniz. Uygulama, birçok oluşturabilirsiniz <xref:System.Net.Sockets.SocketAsyncEventArgs> gerekli nesneleri. Örneğin, bir sunucu uygulaması bekleyen işlemleri her zaman gelen istemci bağlantı hızları desteklemek için kabul 15 yuva olması gerekiyorsa, bunu yeniden kullanılabilir 15 ayırabilirsiniz <xref:System.Net.Sockets.SocketAsyncEventArgs> nesneleri önceden bu amaç için.  
  
 Bu sınıf ile bir zaman uyumsuz yuva işlemi gerçekleştirmek için desen aşağıdaki adımlardan oluşur:  
  
1.  Yeni bir ayırma <xref:System.Net.Sockets.SocketAsyncEventArgs> bağlam nesnesi ya da boş bir uygulama havuzundaki alın.  
  
2.  Bağlam kümesi özellikleri olması (geri çağırma temsilci yöntemi ve veri arabelleği, örneğin) gerçekleştirilen hakkında çalışması için nesne.  
  
3.  Zaman uyumsuz işlemi başlatmak için uygun yuva yöntemi (xxxAsync) çağırın.  
  
4.  Zaman uyumsuz yuva yöntemi (xxxAsync) geri true değerini döndürür, tamamlanma durumu için içerik özelliklerine sorgu.  
  
5.  Zaman uyumsuz yuva yöntemi (xxxAsync) geri, işlem eşzamanlı olarak tamamlandı false değeri döndürülürse. Bağlam özellikleri için işlem sonucu sorgulanan.  
  
6.  Başka bir işlem bağlamı yeniden havuzu içinde beklemeye veya atmak.  
  
 Yeni zaman uyumsuz yuva işlemi bağlam nesnesinin ömrü uygulama kodundaki başvuruları ve zaman uyumsuz g/ç başvuruları tarafından belirlenir. Uygulamanın zaman uyumsuz yuva işlemi yöntemlerden birini parametre olarak gönderildikten sonra bir zaman uyumsuz yuva işlemi bağlam nesnesi başvuru korumak gerekli değildir. Tamamlama geri çağırma dönene kadar başvurulan kalır. Ancak gelecekteki zaman uyumsuz yuva işlemi için yeniden kullanılabilir içerik nesnesine başvuru tutulacak uygulama avantajlıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>  
 [Ağ programlama örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Yuva performans teknolojisi örnek](http://go.microsoft.com/fwlink/?LinkID=179570)
