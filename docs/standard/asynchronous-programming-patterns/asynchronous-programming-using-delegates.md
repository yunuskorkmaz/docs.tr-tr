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
ms.openlocfilehash: ce77e57eb049c031ed506e8812fff59ba97a978e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950857"
---
# <a name="asynchronous-programming-using-delegates"></a>Temsilcileri Kullanarak Zaman Uyumsuz Programlama
Temsilciler, zaman uyumlu bir yöntemi zaman uyumsuz bir şekilde aramanızı sağlar. Bir temsilciyi zaman uyumlu olarak çağırdığınızda, `Invoke` yöntemi hedef yöntemi doğrudan geçerli iş parçacığında çağırır. `BeginInvoke` Yöntemi çağrılırsa, ortak dil çalışma zamanı (CLR) isteği sıraya alır ve hemen çağırana döner. Hedef Yöntem, iş parçacığı havuzundan bir iş parçacığında zaman uyumsuz olarak çağrılır. İsteği gönderen orijinal iş parçacığı, hedef yöntemiyle paralel olarak yürütmeye devam etmek için ücretsizdir. `BeginInvoke` Yöntemine yapılan çağrıda bir geri çağırma yöntemi belirtilmişse, hedef Yöntem sona erdiğinde geri çağırma yöntemi çağrılır. Geri çağırma yönteminde, `EndInvoke` yöntemi dönüş değerini ve herhangi bir giriş/çıkış veya yalnızca çıkış parametrelerini alır. Çağrılırken `BeginInvoke`hiçbir geri arama yöntemi belirtilmemişse, `EndInvoke` çağıran iş parçacığından `BeginInvoke`çağrılabilir.  
  
> [!IMPORTANT]
> Derleyiciler `Invoke`, Kullanıcı tarafından belirtilen temsilci `BeginInvoke`imzasını kullanarak `EndInvoke` ,, ve yöntemleriyle temsilci sınıfları göstermelidir. `BeginInvoke` Ve`EndInvoke` yöntemleri yerel olarak tasarlanmalıdır. Bu yöntemler yerel olarak işaretlendiğinden, CLR otomatik olarak uygulamayı sınıf yükleme zamanında sağlar. Yükleyici, bunların geçersiz kılınmamasını sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Sıradan yöntemlere zaman uyumsuz çağrılar yapmak için temsilcilerin kullanımını açıklar ve zaman uyumsuz bir çağrının dönmesi için beklenecek dört yolu gösteren basit kod örnekleri sunar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 .NET Framework zaman uyumsuz programlamayı açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
