---
title: "Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c677ed869c0e5dd0df1288de48668ba403df5aa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Tek Bir Eşzamanlılık Modunda İletilerin Sıralı İşlenmesi
Temel alınan kanal süre sonuyla olmadığı sürece WCF garanti iletileri işlenme, sipariş hakkında yapar.  Örneğin, bir süre sonuyla kanal değil, MsmqInputChannel kullanan bir WCF hizmeti işlem iletileri sırasına başarısız olur. Bir geliştirici nerede ancak içinde sipariş davranış işleme istediğiniz oturumları kullanmak istemiyor bazı durumlar vardır. Bu konuda, bir hizmet tek eşzamanlılık modunda çalışırken bu davranışı yapılandırmak açıklar.  
  
## <a name="in-order-message-processing"></a>Düzen dışı ileti işleme  
 Yeni bir öznitelik adı verilen <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> eklendi <xref:System.ServiceModel.ServiceBehaviorAttribute>. Zaman <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> ayarlanmış true ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ayarlanır <xref:System.ServiceModel.ConcurrencyMode.Single> sırada hizmete gönderilen iletileri işlenmeyecek. Aşağıdaki kod parçacığını nasıl bu öznitelikler ayarlanacağını gösterir.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Varsa <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> başka herhangi bir değer için ayarlanmış bir <xref:System.InvalidOperationException> oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oturumlar, örnek oluşturma ve eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md)
