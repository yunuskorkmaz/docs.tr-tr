---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: aca5a6ad07d96e08203e9e1cad7dec632035caf0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="1df0a-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... ctor</span><span class="sxs-lookup"><span data-stu-id="1df0a-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="1df0a-103">Bir örneğini oluşturur [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1df0a-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1df0a-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1df0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1df0a-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="1df0a-106">ParameTRe değerleri</span><span class="sxs-lookup"><span data-stu-id="1df0a-106">Parameter Values</span></span>  
 <span data-ttu-id="1df0a-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="1df0a-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="1df0a-108">İşlem adı, dönüş türü ve parameTRe bilgileri de dahil olmak üzere oluşturulması için iş akışı etkinlikte gerçekleştirilecek işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1df0a-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="1df0a-109">Bu parametrenin değeri olmamalıdır **null**.</span><span class="sxs-lookup"><span data-stu-id="1df0a-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="1df0a-110">İleti sözleşmesi kullanan ve bir bağımsız değişken bir ileti ile eşzamanlı bir işlem açıklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1df0a-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="1df0a-111">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="1df0a-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="1df0a-112">*ConfigurationName*</span><span class="sxs-lookup"><span data-stu-id="1df0a-112">*configurationName*</span></span>  
  
 <span data-ttu-id="1df0a-113">Bitiş noktası yapılandırma adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1df0a-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="1df0a-114">Bu parametrenin değeri ya da olmamalıdır **null** veya boş.</span><span class="sxs-lookup"><span data-stu-id="1df0a-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="1df0a-115">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="1df0a-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="1df0a-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="1df0a-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="1df0a-117">İşlem için hizmet ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1df0a-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="1df0a-118">Bu parametrenin değeri ya da olmamalıdır **null** veya boş.</span><span class="sxs-lookup"><span data-stu-id="1df0a-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="1df0a-119">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="1df0a-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df0a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1df0a-120">See Also</span></span>  
 [<span data-ttu-id="1df0a-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="1df0a-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
