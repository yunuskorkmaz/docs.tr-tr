---
title: 'Nasıl yapılır: Parametreleri İnceleme veya Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 1238c81e2607da6fc5e742aacd1b1dcc69996a8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209950"
---
# <a name="how-to-inspect-or-modify-parameters"></a>Nasıl yapılır: Parametreleri İnceleme veya Değiştirme
İnceleme veya gelen veya giden iletiler için bir Windows Communication Foundation (WCF) istemci nesnesi veya bir WCF hizmetini sunucuda tek bir işlem uygulayarak değiştirme <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimi ve istemci veya hizmet çalışma zamanına ekleme. Genellikle işlem davranışı, tek bir işlem için parametre denetçiler eklemek için kullanılır; diğer davranışlar çalışma zamanı büyük bir kapsamda kolay erişim sağlamak için kullanılabilir. Daha fazla bilgi için [genişletme istemciler](../../../../docs/framework/wcf/extending/extending-clients.md) ve [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>İnceleme veya değiştirme parametreleri  
  
1.  <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.  
  
2.  Uygulama bir <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (gerekli kapsamın bağlı olarak), parametre denetçisi eklenecek <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> özellikleri.  
  
3.  Davranış'ınızı çağrılmadan önce Ekle <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodunda <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri, sırada göster:  
  
-   Bir parametre denetçisi uygulaması.  
  
-   Parametre Inspector'ı kullanarak ekler davranışını uygulama bir <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>ve bir <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
-   Yükleyen ve istemci üzerinde parametresi Inspector'ı eklemek için bir istemci uygulaması, uç nokta davranışı çalışır bir yapılandırma dosyası.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
