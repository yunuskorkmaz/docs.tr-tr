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
ms.openlocfilehash: 0ce9be30182f9181bcb6449529d9b9796aadbc2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794530"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="cf9c4-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="cf9c4-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="cf9c4-103">Örneği oluşturur [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf9c4-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf9c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf9c4-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="cf9c4-106">ParameTRe değerleri</span><span class="sxs-lookup"><span data-stu-id="cf9c4-106">Parameter Values</span></span>  
 <span data-ttu-id="cf9c4-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="cf9c4-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="cf9c4-108">İşlem adı, dönüş türü ve parameTRe bilgileri de dahil olmak üzere oluşturulması için iş akışı etkinlikte gerçekleştirilecek işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="cf9c4-109">Bu parametrenin değeri olmamalıdır **null**.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="cf9c4-110">Bu ileti sözleşmesi kullanan ve bir ileti ile bir bağımsız değişken alıyor eşzamanlı bir işlem açıklaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="cf9c4-111">Bu koşullar tatmin edici değil, oluşturucuya ve diğer bu sınıftaki yöntemleri kullanılarak çalışma zamanı sonucu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="cf9c4-112">*ConfigurationName*</span><span class="sxs-lookup"><span data-stu-id="cf9c4-112">*configurationName*</span></span>  
  
 <span data-ttu-id="cf9c4-113">Bitiş noktası yapılandırma adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="cf9c4-114">Bu parametrenin değeri ya da olmamalıdır **null** veya boş.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="cf9c4-115">Bu koşullar tatmin edici değil, oluşturucuya ve diğer bu sınıftaki yöntemleri kullanılarak çalışma zamanı sonucu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="cf9c4-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="cf9c4-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="cf9c4-117">İşlem için hizmet ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="cf9c4-118">Bu parametrenin değeri ya da olmamalıdır **null** veya boş.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="cf9c4-119">Bu koşullar tatmin edici değil, oluşturucuya ve diğer bu sınıftaki yöntemleri kullanılarak çalışma zamanı sonucu tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9c4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf9c4-120">See also</span></span>

- [<span data-ttu-id="cf9c4-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="cf9c4-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
