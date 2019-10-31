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
ms.openlocfilehash: 4e17e6a96a12b705cf455d70add7e12a30f5fa90
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121741"
---
# <a name="asynchronous-programming-using-delegates"></a>Temsilcileri Kullanarak Zaman Uyumsuz Programlama
Temsilciler, zaman uyumlu bir yöntemi zaman uyumsuz bir şekilde aramanızı sağlar. Bir temsilciyi zaman uyumlu olarak çağırdığınızda `Invoke` yöntemi hedef yöntemi doğrudan geçerli iş parçacığında çağırır. `BeginInvoke` yöntemi çağrılırsa, ortak dil çalışma zamanı (CLR) isteği sıralar ve çağrıyı yapana hemen döndürür. Hedef Yöntem, iş parçacığı havuzundan bir iş parçacığında zaman uyumsuz olarak çağrılır. İsteği gönderen orijinal iş parçacığı, hedef yöntemiyle paralel olarak yürütmeye devam etmek için ücretsizdir. `BeginInvoke` yöntemine yapılan çağrıda bir geri çağırma yöntemi belirtilmişse, hedef Yöntem sona erdiğinde geri çağırma yöntemi çağrılır. Geri çağırma yönteminde `EndInvoke` yöntemi, dönüş değerini ve herhangi bir giriş/çıkış ya da yalnızca çıkış parametrelerini alır. `BeginInvoke`çağrılırken hiçbir geri arama yöntemi belirtilmemişse, `EndInvoke` `BeginInvoke`çağıran iş parçacığından çağrılabilir.  
  
> [!IMPORTANT]
> Derleyiciler, Kullanıcı tarafından belirtilen temsilci imzasını kullanarak temsilci sınıflarını `Invoke`, `BeginInvoke`ve `EndInvoke` yöntemlerle yaymalıdır. `BeginInvoke` ve `EndInvoke` yöntemleri yerel olarak tasarlanmalıdır. Bu yöntemler yerel olarak işaretlendiğinden, CLR otomatik olarak uygulamayı sınıf yükleme zamanında sağlar. Yükleyici, bunların geçersiz kılınmamasını sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Sıradan yöntemlere zaman uyumsuz çağrılar yapmak için temsilcilerin kullanımını açıklar ve zaman uyumsuz bir çağrının dönmesi için beklenecek dört yolu gösteren basit kod örnekleri sunar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 .NET Framework zaman uyumsuz programlamayı açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
