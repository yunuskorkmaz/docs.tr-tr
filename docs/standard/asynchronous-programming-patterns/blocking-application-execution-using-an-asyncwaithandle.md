---
title: Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 054af36987d60c8aeb752c9c711f1cce19733efc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624476"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme
İşlem tamamlanana kadar zaman uyumsuz bir işlemin sonuçları için beklerken, diğer iş yapmak için devam edemiyor uygulamaları engellemeniz gerekir. Uygulamanızın ana iş parçacığı bir zaman uyumsuz bir işlemin tamamlanması beklenirken engellemek için aşağıdaki seçeneklerden birini kullanın:  
  
-   Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak ** * OperationName* yöntemi. Bu yaklaşım, bu konuda gösterilmiştir.  
  
-   Zaman uyumsuz işlemin çağrı **son *** OperationName* yöntemi. Bu yaklaşım gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırarak uygulama yürütmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Bir veya daha fazla kullanan uygulamaları <xref:System.Threading.WaitHandle> bir zaman uyumsuz işlem tamamlanana kadar engelleyin nesnelere genellikle çağıracaktır **başlamak *** OperationName* yöntemi sonuçlarını gerek kalmadan yapılabilir herhangi bir çalışma gerçekleştirme işlem ve ardından zaman uyumsuz işlemleri tamamlanana kadar blok. Bir uygulamanın tek bir işlem birini çağırarak engelleyebilirsiniz <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemlerini kullanarak <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Zaman uyumsuz işlemleri tamamlamak için bir dizi için beklenirken engellemek için ilişkili depolama <xref:System.IAsyncResult.AsyncWaitHandle%2A> bir dizi ve, çağrı nesneleri <xref:System.Threading.WaitHandle.WaitAll%2A> yöntemleri. Zaman uyumsuz işlemleri tamamlamak için bir dizi herhangi biri için beklenirken engellemek için ilişkili depolama <xref:System.IAsyncResult.AsyncWaitHandle%2A> bir dizi ve, çağrı nesneleri <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistemi bilgileri almak için DNS sınıfında zaman uyumsuz metotlar kullanma gösterilmektedir. Örnek kullanarak engelleme gösterir <xref:System.Threading.WaitHandle> zaman uyumsuz işlemle ilişkili. Unutmayın `null` (`Nothing` Visual Basic'te) geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` ve `stateObject` parametreleri olduğundan, bunlar bu yaklaşım kullanırken gerekli değildir.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
