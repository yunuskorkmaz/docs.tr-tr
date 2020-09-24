---
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
ms.openlocfilehash: 4e7595efd3037a525d272dbcd60243db29f2efa6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150836"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="a610c-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="a610c-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>

<span data-ttu-id="a610c-103">[Microsoft. VisualStudio. Activities. ASR. ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a610c-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a610c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a610c-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a610c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a610c-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="a610c-106">ParameTRe değerleri</span><span class="sxs-lookup"><span data-stu-id="a610c-106">Parameter Values</span></span>  

 <span data-ttu-id="a610c-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="a610c-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="a610c-108">İşlem adı, dönüş türü ve parameTRe bilgileri de dahil olmak üzere oluşturulması için iş akışı etkinlikte gerçekleştirilecek işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a610c-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="a610c-109">Bu parametrenin değeri **null**olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a610c-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="a610c-110">İleti anlaşması kullanan ve bir ileti içeren bir bağımsız değişken alan zaman uyumlu bir işlem tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a610c-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="a610c-111">Bu koşullar karşılanmıyorsa, oluşturucuyu ve bu sınıfın diğer yöntemlerini kullanmanın çalışma zamanı sonucu tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="a610c-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="a610c-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="a610c-112">*configurationName*</span></span>  
  
 <span data-ttu-id="a610c-113">Bitiş noktası yapılandırma adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a610c-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="a610c-114">Bu parametrenin değeri **null** ya da boş olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a610c-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="a610c-115">Bu koşullar karşılanmıyorsa, oluşturucuyu ve bu sınıfın diğer yöntemlerini kullanmanın çalışma zamanı sonucu tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="a610c-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="a610c-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="a610c-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="a610c-117">İşlem için hizmet ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a610c-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="a610c-118">Bu parametrenin değeri **null** ya da boş olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a610c-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="a610c-119">Bu koşullar karşılanmıyorsa, oluşturucuyu ve bu sınıfın diğer yöntemlerini kullanmanın çalışma zamanı sonucu tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="a610c-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a610c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a610c-120">See also</span></span>

- [<span data-ttu-id="a610c-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="a610c-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
