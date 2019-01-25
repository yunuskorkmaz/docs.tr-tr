---
title: Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: c9f2460a1def19212d3ba866b0b443830e9b69bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745859"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
Arka plandaki kanal kapatamaması olmadığı sürece, WCF iletileri işlenme, sipariş tutarlılık garantisi sağlar.  Örneğin, bir oturum kanalı olmayan MsmqInputChannel kullanan bir WCF hizmet sırası iletileri işlemek başarısız olur. Bir geliştirici burada ancak içinde sipariş davranışı işleme istediğiniz oturumları kullanmak istemiyor bazı durumlar vardır. Bu konu, bir hizmet, tek bir eşzamanlılık modunda çalışırken bu davranışı yapılandırmak açıklar.  
  
## <a name="in-order-message-processing"></a>Sıralı ileti işleme  
 Olarak adlandırılan yeni bir öznitelik <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> eklendi <xref:System.ServiceModel.ServiceBehaviorAttribute>. Zaman <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> ayarlanır true ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ayarlanır <xref:System.ServiceModel.ConcurrencyMode.Single> sırada gönderilen iletileri işlenmeyecek. Aşağıdaki kod parçacığını bu öznitelikler kümesi gösterilmektedir.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Varsa <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> başka herhangi bir değer için ayarlanmış bir <xref:System.InvalidOperationException> oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md)
