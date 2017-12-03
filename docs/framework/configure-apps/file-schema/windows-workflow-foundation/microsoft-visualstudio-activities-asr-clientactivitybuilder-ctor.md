---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... ctor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location: Microsoft.VisualStudio.Activities.dll
api_type: Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8d9e9bfb0967b6c41a3df0015bdd6b4101e0c06
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="0bf5a-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... ctor</span><span class="sxs-lookup"><span data-stu-id="0bf5a-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="0bf5a-103">Bir örneğini oluşturur [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf5a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bf5a-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bf5a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0bf5a-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="0bf5a-106">ParameTRe değerleri</span><span class="sxs-lookup"><span data-stu-id="0bf5a-106">Parameter Values</span></span>  
 <span data-ttu-id="0bf5a-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="0bf5a-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="0bf5a-108">İşlem adı, dönüş türü ve parameTRe bilgileri de dahil olmak üzere oluşturulması için iş akışı etkinlikte gerçekleştirilecek işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="0bf5a-109">Bu parametrenin değeri olmamalıdır **null**.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="0bf5a-110">İleti sözleşmesi kullanan ve bir bağımsız değişken bir ileti ile eşzamanlı bir işlem açıklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="0bf5a-111">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="0bf5a-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="0bf5a-112">*configurationName*</span></span>  
  
 <span data-ttu-id="0bf5a-113">Bitiş noktası yapılandırma adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="0bf5a-114">Bu parametrenin değeri ya da olmamalıdır **null** veya boş.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="0bf5a-115">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="0bf5a-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="0bf5a-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="0bf5a-117">İşlem için hizmet ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="0bf5a-118">Bu parametrenin değeri ya da olmamalıdır **null** veya boş.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="0bf5a-119">Bu koşullar memnun değil, oluşturucusu ve bu sınıfın başka yöntemler kullanarak çalışma zamanı sonucunu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf5a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0bf5a-120">See Also</span></span>  
 [<span data-ttu-id="0bf5a-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="0bf5a-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
