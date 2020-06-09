---
title: 'Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 8a73dd90d268c61e0df974861753119e205a870f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599080"
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
