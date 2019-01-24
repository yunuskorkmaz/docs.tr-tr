---
title: 'Nasıl yapılır: Hizmette iletileri denetleme ve değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 19487d3f401260a7a32e9aab63b8c2a75feccbd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599640"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Nasıl yapılır: Hizmette iletileri denetleme ve değiştirme
İnceleme veya uygulayarak bir Windows Communication Foundation (WCF) istemcisi gelen veya giden iletileri değiştirme bir <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> ve hizmet çalışma zamanına ekleme. Daha fazla bilgi için [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Hizmette eşdeğer özellik <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>İletileri denetleme veya değiştirme için  
  
1.  <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.  
  
2.  Uygulama bir <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> kolayca hizmet ileti Inspector'ı eklemek istediğiniz kapsama bağlı olarak arabirimi.  
  
3.  Davranış'ınızı çağrılmadan önce Ekle <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodunda <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri, sırada göster:  
  
-   Bir hizmet denetçisi uygulaması.  
  
-   Inspector ekleyen bir hizmet davranışı.  
  
-   Yükleyen ve davranışını bir hizmet uygulamasında çalışan bir yapılandırma dosyası.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
