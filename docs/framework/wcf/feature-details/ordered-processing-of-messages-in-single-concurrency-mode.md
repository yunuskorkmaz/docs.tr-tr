---
title: Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: ecabb9a6e838b0137c538d76c554646356ea87f5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991510"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
WCF, arka plandaki kanal oturumsuz olmadığı takdirde, iletilerin işlendiği sıra hakkında garanti vermez.  Örneğin, bir oturum kanalı olmayan MsmqInputChannel kullanan bir WCF hizmeti, iletileri sırayla işleyemeyecektir. Bir geliştiricinin sipariş işleme davranışını tercih edebileceği ancak oturumları kullanmak istemebileceği bazı durumlar vardır. Bu konu, bir hizmet tek bir eşzamanlılık modunda çalışırken bu davranışın nasıl yapılandırılacağını açıklar.  
  
## <a name="in-order-message-processing"></a>Sıralı Ileti Işleme  
 Adlı <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> yeni bir öznitelik eklendi <xref:System.ServiceModel.ServiceBehaviorAttribute>. True olarak ayarlandığında ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> hizmete gönderilen <xref:System.ServiceModel.ConcurrencyMode.Single> iletilere ayarlandığında, sırayla işlenir. <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> Aşağıdaki kod parçacığında, bu özniteliklerin nasıl ayarlanacağı gösterilmektedir.  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Diğer herhangi bir değere ayarlanırsa, bir <xref:System.InvalidOperationException> oluşturulur. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md)
