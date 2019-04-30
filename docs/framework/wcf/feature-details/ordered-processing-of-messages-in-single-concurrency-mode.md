---
title: Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: 785c2953e57eaf967209b0d9e52ab85a3a99c450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769453"
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
