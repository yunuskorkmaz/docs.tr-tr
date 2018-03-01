---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... ctor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4c50d9754b71386e6809d46cd9666987a704fbf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="a273f-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... ctor</span><span class="sxs-lookup"><span data-stu-id="a273f-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="a273f-103">Bir örneğini oluşturur [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a273f-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a273f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a273f-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a273f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a273f-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="a273f-106">ParameTRe değerleri</span><span class="sxs-lookup"><span data-stu-id="a273f-106">Parameter Values</span></span>  
 <span data-ttu-id="a273f-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="a273f-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="a273f-108">İşlem adı, dönüş türü ve parameTRe bilgileri de dahil olmak üzere oluşturulması için iş akışı etkinlikte gerçekleştirilecek işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a273f-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="a273f-109">Bu parametrenin değeri olmamalıdır **null**.</span><span class="sxs-lookup"><span data-stu-id="a273f-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="a273f-110">İleti sözleşmesi kullanan ve bir bağımsız değişken bir ileti ile eşzamanlı bir işlem açıklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a273f-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="a273f-111">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="a273f-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="a273f-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="a273f-112">*configurationName*</span></span>  
  
 <span data-ttu-id="a273f-113">Bitiş noktası yapılandırma adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a273f-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="a273f-114">Bu parametrenin değeri ya da olmamalıdır **null** veya boş.</span><span class="sxs-lookup"><span data-stu-id="a273f-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="a273f-115">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="a273f-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="a273f-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="a273f-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="a273f-117">İşlem için hizmet ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a273f-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="a273f-118">Bu parametrenin değeri ya da olmamalıdır **null** veya boş.</span><span class="sxs-lookup"><span data-stu-id="a273f-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="a273f-119">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="a273f-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a273f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a273f-120">See Also</span></span>  
 [<span data-ttu-id="a273f-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="a273f-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
