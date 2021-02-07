---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: hizmette Iletileri Inceleme ve değiştirme'
title: 'Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 5fd3a5e49bdd35a3095e5855b399533337e133a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668883"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme

Bir Windows Communication Foundation (WCF) istemcisinde gelen veya giden iletileri, bir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> oluşturup hizmet çalışma zamanına ekleyerek inceleyebilir veya değiştirebilirsiniz. Daha fazla bilgi için bkz. [Dispatchleri genişletme](extending-dispatchers.md). Hizmetin eşdeğer özelliği <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> .  
  
### <a name="to-inspect-or-modify-messages"></a>İletileri incelemek veya değiştirmek için  
  
1. <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.  
  
2. <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> Hizmet ileti denetçinizi kolayca eklemek istediğiniz kapsama bağlı olarak, veya arabirimini uygulayın.  
  
3. Metodu üzerinde çağrılmadan önce davranışınızı ekleyin <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> . Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örnekleri sırasıyla gösterilmektedir:  
  
- Bir hizmet denetçisi uygulamasıdır.  
  
- Inspector 'ı ekleyen bir hizmet davranışı.  
  
- Bir hizmet uygulamasında davranışı yükleyen ve çalıştıran bir yapılandırma dosyası.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](configuring-and-extending-the-runtime-with-behaviors.md)
