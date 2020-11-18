---
title: Temsilcileri Kullanarak Zaman Uyumsuz Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
ms.openlocfilehash: da468d3b16ee504317c7de2e216a9be2073d1cf3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830512"
---
# <a name="asynchronous-programming-using-delegates"></a>Temsilcileri Kullanarak Zaman Uyumsuz Programlama

Temsilciler, zaman uyumlu bir yöntemi zaman uyumsuz bir şekilde aramanızı sağlar. Bir temsilciyi zaman uyumlu olarak çağırdığınızda, `Invoke` yöntemi hedef yöntemi doğrudan geçerli iş parçacığında çağırır. `BeginInvoke`Yöntemi çağrılırsa, ortak dil çalışma zamanı (CLR) isteği sıraya alır ve hemen çağırana döner. Hedef Yöntem, iş parçacığı havuzundan bir iş parçacığında zaman uyumsuz olarak çağrılır. İsteği gönderen orijinal iş parçacığı, hedef yöntemiyle paralel olarak yürütmeye devam etmek için ücretsizdir. Yöntemine yapılan çağrıda bir geri çağırma yöntemi belirtilmişse `BeginInvoke` , hedef Yöntem sona erdiğinde geri çağırma yöntemi çağrılır. Geri çağırma yönteminde, `EndInvoke` yöntemi dönüş değerini ve herhangi bir giriş/çıkış veya yalnızca çıkış parametrelerini alır. Çağrılırken hiçbir geri arama yöntemi belirtilmemişse, çağıran `BeginInvoke` `EndInvoke` iş parçacığından çağrılabilir `BeginInvoke` .  
  
> [!IMPORTANT]
> Derleyiciler `Invoke` , `BeginInvoke` `EndInvoke` Kullanıcı tarafından belirtilen temsilci imzasını kullanarak,, ve yöntemleriyle temsilci sınıfları göstermelidir. `BeginInvoke`Ve `EndInvoke` yöntemleri yerel olarak tasarlanmalıdır. Bu yöntemler yerel olarak işaretlendiğinden, CLR otomatik olarak uygulamayı sınıf yükleme zamanında sağlar. Yükleyici, bunların geçersiz kılınmamasını sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](calling-synchronous-methods-asynchronously.md)  
 Sıradan yöntemlere zaman uyumsuz çağrılar yapmak için temsilcilerin kullanımını açıklar ve zaman uyumsuz bir çağrının dönmesi için beklenecek dört yolu gösteren basit kod örnekleri sunar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)  
 .NET 'te zaman uyumsuz programlamayı açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
