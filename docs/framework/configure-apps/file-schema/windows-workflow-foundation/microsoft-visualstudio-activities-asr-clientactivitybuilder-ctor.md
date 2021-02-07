---
description: ": Microsoft. VisualStudio. Activities. ASR. ClientActivityBuilder hakkında daha fazla bilgi edinin.. 'u"
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: 1a1b436c2b15fdf07f924aa0db2a13598422e988
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739995"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="c4be7-103">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="c4be7-103">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>

<span data-ttu-id="c4be7-104">[Microsoft. VisualStudio. Activities. ASR. ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4be7-104">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4be7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4be7-105">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4be7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4be7-106">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="c4be7-107">ParameTRe değerleri</span><span class="sxs-lookup"><span data-stu-id="c4be7-107">Parameter Values</span></span>  

 <span data-ttu-id="c4be7-108">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="c4be7-108">*operationDescription*</span></span>  
  
 <span data-ttu-id="c4be7-109">İşlem adı, dönüş türü ve parameTRe bilgileri de dahil olmak üzere oluşturulması için iş akışı etkinlikte gerçekleştirilecek işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c4be7-109">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="c4be7-110">Bu parametrenin değeri **null** olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4be7-110">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="c4be7-111">İleti anlaşması kullanan ve bir ileti içeren bir bağımsız değişken alan zaman uyumlu bir işlem tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4be7-111">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="c4be7-112">Bu koşullar karşılanmıyorsa, oluşturucuyu ve bu sınıfın diğer yöntemlerini kullanmanın çalışma zamanı sonucu tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c4be7-112">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="c4be7-113">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="c4be7-113">*configurationName*</span></span>  
  
 <span data-ttu-id="c4be7-114">Bitiş noktası yapılandırma adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4be7-114">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="c4be7-115">Bu parametrenin değeri **null** ya da boş olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4be7-115">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="c4be7-116">Bu koşullar karşılanmıyorsa, oluşturucuyu ve bu sınıfın diğer yöntemlerini kullanmanın çalışma zamanı sonucu tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c4be7-116">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="c4be7-117">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="c4be7-117">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="c4be7-118">İşlem için hizmet ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4be7-118">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="c4be7-119">Bu parametrenin değeri **null** ya da boş olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4be7-119">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="c4be7-120">Bu koşullar karşılanmıyorsa, oluşturucuyu ve bu sınıfın diğer yöntemlerini kullanmanın çalışma zamanı sonucu tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c4be7-120">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4be7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4be7-121">See also</span></span>

- [<span data-ttu-id="c4be7-122">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="c4be7-122">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
