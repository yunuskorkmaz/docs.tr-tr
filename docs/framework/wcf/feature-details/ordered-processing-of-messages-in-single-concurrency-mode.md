---
title: Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: d70087a6dc1501f9a7f7ed057eae3dad181761ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248025"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi

WCF, arka plandaki kanal oturumsuz olmadığı takdirde, iletilerin işlendiği sıra hakkında garanti vermez.  Örneğin, bir oturum kanalı olmayan MsmqInputChannel kullanan bir WCF hizmeti, iletileri sırayla işleyemeyecektir. Bir geliştiricinin sipariş işleme davranışını tercih edebileceği ancak oturumları kullanmak istemebileceği bazı durumlar vardır. Bu konu, bir hizmet tek bir eşzamanlılık modunda çalışırken bu davranışın nasıl yapılandırılacağını açıklar.  
  
## <a name="in-order-message-processing"></a>Sıralı Ileti Işleme  

 Adlı yeni bir öznitelik <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> eklendi <xref:System.ServiceModel.ServiceBehaviorAttribute> . <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A>True olarak ayarlandığında ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> <xref:System.ServiceModel.ConcurrencyMode.Single> hizmete gönderilen iletilere ayarlandığında, sırayla işlenir. Aşağıdaki kod parçacığında, bu özniteliklerin nasıl ayarlanacağı gösterilmektedir.  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>Diğer herhangi bir değere ayarlanırsa, bir <xref:System.InvalidOperationException> oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](sessions-instancing-and-concurrency.md)
- [Eşzamanlılık](../samples/concurrency.md)
