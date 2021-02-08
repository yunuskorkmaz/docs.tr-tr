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
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="c7b5c-103">Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme</span><span class="sxs-lookup"><span data-stu-id="c7b5c-103">How to: Control Service Instancing</span></span>

<span data-ttu-id="c7b5c-104">Bir hizmetin örnek modunun ayarlanması, bir <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (ve ilişkili kullanıcı tanımlı hizmet nesnesi) oluşturulduğunda belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7b5c-104">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="c7b5c-105"><xref:System.ServiceModel.InstanceContextMode>Olası modlar için bkz. sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c7b5c-105">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="c7b5c-106">Davranışlar hakkında daha fazla bilgi için bkz. [çalışma zamanını davranışlarla birlikte yapılandırma ve genişletme](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c7b5c-106">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="c7b5c-107">Çalışma örnekleri için bkz. [davranışlar](../samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c7b5c-107">For working examples, see [Behaviors](../samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="c7b5c-108">Kod kullanarak hizmet örneği ömrünü denetlemek için</span><span class="sxs-lookup"><span data-stu-id="c7b5c-108">To control the service instance lifetime using code</span></span>  
  
1. <span data-ttu-id="c7b5c-109"><xref:System.ServiceModel.ServiceBehaviorAttribute>Hizmetini hizmet sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c7b5c-109">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2. <span data-ttu-id="c7b5c-110"><xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>Özelliği aşağıdaki değerlerden birine ayarlayın: <xref:System.ServiceModel.InstanceContextMode.PerCall> , <xref:System.ServiceModel.InstanceContextMode.PerSession> , veya <xref:System.ServiceModel.InstanceContextMode.Single> .</span><span class="sxs-lookup"><span data-stu-id="c7b5c-110">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="c7b5c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7b5c-111">Example</span></span>  

 <span data-ttu-id="c7b5c-112">Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğinin özelliğini olarak ayarlar <xref:System.ServiceModel.InstanceContextMode.PerCall> .</span><span class="sxs-lookup"><span data-stu-id="c7b5c-112">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c7b5c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7b5c-113">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="c7b5c-114">Hizmet: davranışlar örnekleri</span><span class="sxs-lookup"><span data-stu-id="c7b5c-114">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
