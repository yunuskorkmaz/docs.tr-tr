---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: hizmet örneği oluşturmayı denetleme'
title: 'Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 014d7fb4b054a1b52c1fea671cd099267fba468c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779926"
---
# <a name="how-to-control-service-instancing"></a>Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme

Bir hizmetin örnek modunun ayarlanması, bir <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (ve ilişkili kullanıcı tanımlı hizmet nesnesi) oluşturulduğunda belirtmenize olanak sağlar. <xref:System.ServiceModel.InstanceContextMode>Olası modlar için bkz. sabit listesi. Davranışlar hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](../extending/configuring-and-extending-the-runtime-with-behaviors.md). Çalışma örnekleri için bkz. [davranışlar](../samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>Kod kullanarak hizmet örneği ömrünü denetlemek için  
  
1. <xref:System.ServiceModel.ServiceBehaviorAttribute>Hizmetini hizmet sınıfına uygulayın.  
  
2. <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>Özelliği aşağıdaki değerlerden birine ayarlayın: <xref:System.ServiceModel.InstanceContextMode.PerCall> , <xref:System.ServiceModel.InstanceContextMode.PerSession> , veya <xref:System.ServiceModel.InstanceContextMode.Single> .  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğinin özelliğini olarak ayarlar <xref:System.ServiceModel.InstanceContextMode.PerCall> .  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [Hizmet: davranışlar örnekleri](../samples/behaviors.md)
