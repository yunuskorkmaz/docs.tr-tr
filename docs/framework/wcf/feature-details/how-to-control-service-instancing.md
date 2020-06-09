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
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="202b0-102">Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme</span><span class="sxs-lookup"><span data-stu-id="202b0-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="202b0-103">Bir hizmetin örnek modunun ayarlanması, bir <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (ve ilişkili kullanıcı tanımlı hizmet nesnesi) oluşturulduğunda belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="202b0-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="202b0-104"><xref:System.ServiceModel.InstanceContextMode>Olası modlar için bkz. sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="202b0-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="202b0-105">Davranışlar hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="202b0-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="202b0-106">Çalışma örnekleri için bkz. [davranışlar](../samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="202b0-106">For working examples, see [Behaviors](../samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="202b0-107">Kod kullanarak hizmet örneği ömrünü denetlemek için</span><span class="sxs-lookup"><span data-stu-id="202b0-107">To control the service instance lifetime using code</span></span>  
  
1. <span data-ttu-id="202b0-108"><xref:System.ServiceModel.ServiceBehaviorAttribute>Hizmetini hizmet sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="202b0-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2. <span data-ttu-id="202b0-109"><xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>Özelliği aşağıdaki değerlerden birine ayarlayın: <xref:System.ServiceModel.InstanceContextMode.PerCall> , <xref:System.ServiceModel.InstanceContextMode.PerSession> , veya <xref:System.ServiceModel.InstanceContextMode.Single> .</span><span class="sxs-lookup"><span data-stu-id="202b0-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="202b0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="202b0-110">Example</span></span>  
 <span data-ttu-id="202b0-111">Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğinin özelliğini olarak ayarlar <xref:System.ServiceModel.InstanceContextMode.PerCall> .</span><span class="sxs-lookup"><span data-stu-id="202b0-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="202b0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="202b0-112">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="202b0-113">Hizmet: davranışlar örnekleri</span><span class="sxs-lookup"><span data-stu-id="202b0-113">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
