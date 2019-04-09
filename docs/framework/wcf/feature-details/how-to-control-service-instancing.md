---
title: 'Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 1c1a08c702ab1bdc4579cb05359db1681e7203b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135024"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="3bb83-102">Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme</span><span class="sxs-lookup"><span data-stu-id="3bb83-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="3bb83-103">Bir hizmet örneği modunu ayarlama ne zaman belirtmenizi sağlar bir <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (ve onun ilişkili kullanıcı tanımlı bir hizmet nesnesi) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3bb83-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="3bb83-104">Bkz: <xref:System.ServiceModel.InstanceContextMode> olası modları için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3bb83-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="3bb83-105">Davranışlar hakkında daha fazla bilgi için bkz. [yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="3bb83-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="3bb83-106">Çalışan örnekler için bkz [davranışları](../../../../docs/framework/wcf/samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="3bb83-106">For working examples, see [Behaviors](../../../../docs/framework/wcf/samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="3bb83-107">Kod kullanarak hizmet örneği ömrünü denetlemek için</span><span class="sxs-lookup"><span data-stu-id="3bb83-107">To control the service instance lifetime using code</span></span>  
  
1.  <span data-ttu-id="3bb83-108">Uygulama <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmet sınıfı için.</span><span class="sxs-lookup"><span data-stu-id="3bb83-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2.  <span data-ttu-id="3bb83-109">Ayarlama <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliğini şu değerlerden biri: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, veya <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="3bb83-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="3bb83-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3bb83-110">Example</span></span>  
 <span data-ttu-id="3bb83-111">Aşağıdaki örnek kod <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğini <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span><span class="sxs-lookup"><span data-stu-id="3bb83-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3bb83-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bb83-112">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="3bb83-113">Hizmet: Davranışlar örnekleri</span><span class="sxs-lookup"><span data-stu-id="3bb83-113">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
