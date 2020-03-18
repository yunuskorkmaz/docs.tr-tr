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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121741"
---
# <a name="asynchronous-programming-using-delegates"></a>Temsilcileri Kullanarak Zaman Uyumsuz Programlama
Temsilciler, eşzamanlı bir yöntem çağırmanızı sağlar. Bir temsilciyi eşzamanlı olarak çağırdığınızda, `Invoke` yöntem hedef yöntemi doğrudan geçerli iş parçacığına çağırır. `BeginInvoke` Yöntem çağrılırsa, ortak dil çalışma süresi (CLR) isteği sıralar ve hemen arayana döner. Hedef yöntem iş parçacığı havuzundan bir iş parçacığı üzerinde eşzamanlı olarak adlandırılır. İsteği gönderen özgün iş parçacığı, hedef yönteme paralel olarak yürütmeye devam etmek için ücretsizdir. `BeginInvoke` Yönteme yapılan çağrıda bir geri arama yöntemi belirtilmişse, hedef yöntem sona erdiğinde geri arama yöntemi çağrılır. Geri arama yönteminde `EndInvoke` yöntem, iade değerini ve herhangi bir giriş/çıktı veya yalnızca çıktı parametrelerini elde eder. Ararken `BeginInvoke`geri arama yöntemi belirtilmemişse, `EndInvoke` . `BeginInvoke`  
  
> [!IMPORTANT]
> Derleyiciler, kullanıcı tarafından `Invoke`belirtilen `BeginInvoke`temsilci `EndInvoke` imzasını kullanarak , ve yöntemleri ile temsilci sınıfları yontmalıdır. `BeginInvoke` Ve `EndInvoke` yöntemler yerli olarak dekore edilmelidir. Bu yöntemler yerel olarak işaretlendirilenden, CLR uygulamayı sınıf yük zamanında otomatik olarak sağlar. Yükleyici geçersiz kılınmamasını sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Adlı metotlara asynchronous aramalar yapmak için temsilcilerin kullanımını tartışır ve asynchronous çağrısının geri dönmesini beklemenin dört yolunu gösteren basit kod örneği sağlıyor.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 .NET Framework ile eşzamanlı programlamayı açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
