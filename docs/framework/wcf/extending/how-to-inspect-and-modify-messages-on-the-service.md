---
title: 'Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 1356983361c483170d9d7365932b788f2421bf09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795608"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Nasıl yapılır: Hizmette İletileri Denetleme ve Değiştirme
Bir Windows Communication Foundation (WCF) istemcisinde gelen veya giden iletileri, bir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> oluşturup hizmet çalışma zamanına ekleyerek inceleyebilir veya değiştirebilirsiniz. Daha fazla bilgi için bkz. [Dispatchleri genişletme](extending-dispatchers.md). Hizmetin eşdeğer özelliği <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>İletileri incelemek veya değiştirmek için  
  
1. <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.  
  
2. Hizmet ileti denetçinizi kolayca <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> eklemek istediğiniz kapsama bağlı olarak <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>,veyaarabiriminiuygulayın <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
3. <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> Metodu<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>üzerinde çağrılmadan önce davranışınızı ekleyin. Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
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
