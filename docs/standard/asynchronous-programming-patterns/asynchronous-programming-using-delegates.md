---
title: Temsilcileri Kullanarak Zaman Uyumsuz Programlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bad5372af1d771dc93a20e61090ef84126f3e1eb
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006151"
---
# <a name="asynchronous-programming-using-delegates"></a>Temsilcileri Kullanarak Zaman Uyumsuz Programlama
Temsilciler, zaman uyumsuz olarak bir zaman uyumlu yöntem çağrısı sağlar. Zaman uyumlu olarak, bir temsilci çağırdığınızda `Invoke` yöntemi doğrudan geçerli iş parçacığı üzerinde hedef yöntemini çağırır. Varsa `BeginInvoke` yöntemi çağrıldığında, ortak dil çalışma zamanı (CLR) isteğini sıraya koyar ve hemen çağırana döner. Hedef yöntemin, iş parçacığı havuzundan bir iş parçacığında zaman uyumsuz olarak adlandırılır. Hedef yöntemin ile paralel yürütmeye devam isteği gönderildi, özgün iş parçacığı, ücretsizdir. Bir geri çağırma yöntemi çağrısında belirtildiğinde `BeginInvoke` yöntemi, geri çağırma yöntemi hedef yöntemin sona erdiğinde çağrılır. Geri çağırma yöntemi `EndInvoke` yöntemi, dönüş değeri ve giriş/çıkış ya da yalnızca çıktı parametreleri alır. Hiçbir geri çağırma yöntemi çağırırken belirtilmişse `BeginInvoke`, `EndInvoke` çağrılan iş parçacığından çağrılabilir `BeginInvoke`.  
  
> [!IMPORTANT]
>  Derleyiciler, temsilci sınıflarıyla yayma `Invoke`, `BeginInvoke`, ve `EndInvoke` yöntemlerini kullanarak kullanıcı tarafından belirtilen temsilci imzası. `BeginInvoke` Ve `EndInvoke` yöntemleri düzenlenmiş yerel olarak. Bu yöntemler, yerel olarak işaretlendikleri CLR sınıfı yükleme zamanında uygulamasını otomatik olarak sağlar. Yükleyici, bunlar geçersiz kılınmadığını güvence sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Sıradan bir yöntem zaman uyumsuz çağrı yapmak için temsilciler kullanmayı açıklar ve döndürmek zaman uyumsuz bir çağrı için beklenecek dört yolu gösteren basit kod örnekleri sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 .NET Framework ile zaman uyumsuz programlama açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

* <xref:System.Delegate>
