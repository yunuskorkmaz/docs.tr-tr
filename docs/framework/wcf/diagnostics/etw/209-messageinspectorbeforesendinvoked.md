---
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 24184c24b9affdf3a56d7968c02cf5354d690749
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781892"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="376fd-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="376fd-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="376fd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="376fd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="376fd-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="376fd-104">ID</span></span>|<span data-ttu-id="376fd-105">209</span><span class="sxs-lookup"><span data-stu-id="376fd-105">209</span></span>|  
|<span data-ttu-id="376fd-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="376fd-106">Keywords</span></span>|<span data-ttu-id="376fd-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="376fd-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="376fd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="376fd-108">Level</span></span>|<span data-ttu-id="376fd-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="376fd-109">Information</span></span>|  
|<span data-ttu-id="376fd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="376fd-110">Channel</span></span>|<span data-ttu-id="376fd-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="376fd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="376fd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="376fd-112">Description</span></span>  
 <span data-ttu-id="376fd-113">Bu olay, hizmet modeli çağırdığı sonra yayıldığını `BeforeSend` ileti denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="376fd-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="376fd-114">İleti</span><span class="sxs-lookup"><span data-stu-id="376fd-114">Message</span></span>  
 <span data-ttu-id="376fd-115">Dağıtıcı 'BeforeSendRequest' üzerinde '%1' türünde bir MessageInspector çağrılır.</span><span class="sxs-lookup"><span data-stu-id="376fd-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="376fd-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="376fd-116">Details</span></span>  
  
|<span data-ttu-id="376fd-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="376fd-117">Data Item Name</span></span>|<span data-ttu-id="376fd-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="376fd-118">Data Item Type</span></span>|<span data-ttu-id="376fd-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="376fd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="376fd-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="376fd-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="376fd-121">Çağrılan türünün CLR FullName `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="376fd-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="376fd-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="376fd-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="376fd-123">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="376fd-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="376fd-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="376fd-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="376fd-125">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="376fd-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="376fd-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="376fd-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="376fd-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="376fd-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
