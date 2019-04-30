---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: eb060cfa79b75452deae67705126a24b7ca9ffef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782050"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="f37a1-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="f37a1-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="f37a1-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f37a1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f37a1-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f37a1-104">ID</span></span>|<span data-ttu-id="f37a1-105">204</span><span class="sxs-lookup"><span data-stu-id="f37a1-105">204</span></span>|  
|<span data-ttu-id="f37a1-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f37a1-106">Keywords</span></span>|<span data-ttu-id="f37a1-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f37a1-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f37a1-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f37a1-108">Level</span></span>|<span data-ttu-id="f37a1-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f37a1-109">Information</span></span>|  
|<span data-ttu-id="f37a1-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f37a1-110">Channel</span></span>|<span data-ttu-id="f37a1-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f37a1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f37a1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f37a1-112">Description</span></span>  
 <span data-ttu-id="f37a1-113">Bu olay, hizmet modeli çağırdığı sonra yayıldığını `BeforeCall` istemci parametresi denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f37a1-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f37a1-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f37a1-114">Message</span></span>  
 <span data-ttu-id="f37a1-115">Dağıtıcı 'BeforeCall' üzerinde '%1' türünde bir ClientParameterInspector çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f37a1-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f37a1-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f37a1-116">Details</span></span>  
  
|<span data-ttu-id="f37a1-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f37a1-117">Data Item Name</span></span>|<span data-ttu-id="f37a1-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f37a1-118">Data Item Type</span></span>|<span data-ttu-id="f37a1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f37a1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f37a1-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="f37a1-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="f37a1-121">CLR FullName çağrılan denetçisinin türü.</span><span class="sxs-lookup"><span data-stu-id="f37a1-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="f37a1-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="f37a1-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="f37a1-123">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f37a1-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f37a1-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="f37a1-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f37a1-125">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="f37a1-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f37a1-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f37a1-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f37a1-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f37a1-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
