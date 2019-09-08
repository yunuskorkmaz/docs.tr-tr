---
title: 'Nasıl yapılır: Parametreleri İnceleme veya Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: b4a673f97f06e8d489d9acc85d84e1ecea4656e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795590"
---
# <a name="how-to-inspect-or-modify-parameters"></a>Nasıl yapılır: Parametreleri İnceleme veya Değiştirme
<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> Arabirimi uygulayarak ve istemci ya da hizmet çalışma zamanına ekleyerek bir Windows Communication Foundation (WCF) istemci nesnesi veya WCF hizmetinde tek bir işlem için gelen veya giden iletileri inceleyebilir veya değiştirebilirsiniz. Genellikle bir işlem davranışı, tek bir işlem için parametre Inspector eklemek için kullanılır; diğer davranışlar daha büyük bir kapsamdaki çalışma zamanına kolay erişim sağlamak için kullanılabilir. Daha fazla bilgi için bkz. [Istemcileri genişletme](extending-clients.md) ve [dispatchleri genişletme](extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Parametreleri İnceleme veya değiştirme  
  
1. <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimini gerçekleştirin.  
  
2. <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> Ya <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> da özelliklerine parametre denetçisi eklemek için bir, veya (gerekli kapsama bağlı olarak) uygulayın. <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType>  
  
3. ' <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> İçağırmadan<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> önce davranışını veya metodunu ekleyin. <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> Ayrıntılar için bkz. [çalışma zamanını davranışlar Ile yapılandırma ve genişletme](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri sırasıyla gösterilmektedir:  
  
- Bir parametre denetçisi uygulamasıdır.  
  
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType> ,<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> Ve<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>bir kullanarak parametre denetçisini ekleyen davranış uygulamasıdır.  
  
- İstemciye parametre denetçisi eklemek için bir istemci uygulamasındaki uç nokta davranışını yükleyen ve çalıştıran bir yapılandırma dosyası.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](configuring-and-extending-the-runtime-with-behaviors.md)
