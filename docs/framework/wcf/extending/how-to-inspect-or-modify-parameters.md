---
title: "Nasıl yapılır: Parametreleri İnceleme veya Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c974e37856fff60cd90ec435b1501393654253c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-inspect-or-modify-parameters"></a>Nasıl yapılır: Parametreleri İnceleme veya Değiştirme
İnceleme veya tek bir işlem için gelen veya giden iletiler değiştirin bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci nesnesi veya bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulayarak hizmet <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimi ve istemci veya hizmet çalışma zamanına ekleniyor. Genellikle bir işlemi davranışı, tek bir işlem için parametre denetçiler eklemek için kullanılır; diğer davranışlar çalışma zamanı büyük bir kapsamda kolay erişim sağlamak için kullanılabilir. Daha fazla bilgi için bkz: [genişletme istemcileri](../../../../docs/framework/wcf/extending/extending-clients.md) ve [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>İnceleme veya değiştirme parametreleri  
  
1.  Uygulama <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> arabirimi.  
  
2.  Uygulama bir <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (gerekli kapsam bağlı olarak), parametre denetçisi ya da eklemek için <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> özellikleri.  
  
3.  Çağrılmadan önce davranış Ekle <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> yöntemi <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Ayrıntılar için bkz [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri, sırada göster:  
  
-   Bir parametre denetçisi uygulaması.  
  
-   Kullanarak parametre denetçisi ekler davranışı uygulaması bir <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>ve bir <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
-   Yükler ve istemci üzerindeki parametre denetçisi eklemek için bir istemci uygulamasında uç noktası davranışı çalışan bir yapılandırma dosyası.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
