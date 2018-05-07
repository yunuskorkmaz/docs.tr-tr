---
title: 'Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 2f9e4f298eb95498ec8d3603624763bfd95bfda1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-service-instancing"></a>Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme
Bir hizmet örneği modunu ayarlama, sağlar, ne zaman belirtmek bir <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (ve onun ilişkili kullanıcı tanımlı bir hizmet nesnesi) oluşturulur. Bkz: <xref:System.ServiceModel.InstanceContextMode> olası modları için numaralandırması. Davranışları hakkında daha fazla bilgi için bkz: [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md). Çalışma örnekler için bkz: [davranışları](../../../../docs/framework/wcf/samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>Kod kullanarak hizmet örneği ömrü denetlemek için  
  
1.  Uygulama <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmet sınıfı.  
  
2.  Ayarlama <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliğini aşağıdaki değerlerden birine: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, veya <xref:System.ServiceModel.InstanceContextMode.Single>.  
  
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
 [Hizmet: Davranışları örnekleri](http://msdn.microsoft.com/library/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
