---
title: 'Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: b9e622903f871564495796b1690ab4e3a1f66fb7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514830"
---
# <a name="how-to-control-service-instancing"></a>Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme
Bir hizmet örneği modunu ayarlama ne zaman belirtmenizi sağlar bir <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (ve onun ilişkili kullanıcı tanımlı bir hizmet nesnesi) oluşturulur. Bkz: <xref:System.ServiceModel.InstanceContextMode> olası modları için sabit listesi. Davranışlar hakkında daha fazla bilgi için bkz. [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md). Çalışan örnekler için bkz [davranışları](../../../../docs/framework/wcf/samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>Kod kullanarak hizmet örneği ömrünü denetlemek için  
  
1.  Uygulama <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmet sınıfı için.  
  
2.  Ayarlama <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliğini şu değerlerden biri: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, veya <xref:System.ServiceModel.InstanceContextMode.Single>.  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğini <xref:System.ServiceModel.InstanceContextMode.PerCall>.  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>  
 <xref:System.ServiceModel.InstanceContextMode>  
 [Hizmet: Davranışları örnekleri](https://msdn.microsoft.com/library/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
