---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781738"
---
# <a name="219---serviceexception"></a><span data-ttu-id="db24f-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="db24f-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="db24f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="db24f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db24f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="db24f-104">ID</span></span>|<span data-ttu-id="db24f-105">219</span><span class="sxs-lookup"><span data-stu-id="db24f-105">219</span></span>|  
|<span data-ttu-id="db24f-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="db24f-106">Keywords</span></span>|<span data-ttu-id="db24f-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="db24f-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="db24f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="db24f-108">Level</span></span>|<span data-ttu-id="db24f-109">Hata</span><span class="sxs-lookup"><span data-stu-id="db24f-109">Error</span></span>|  
|<span data-ttu-id="db24f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="db24f-110">Channel</span></span>|<span data-ttu-id="db24f-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="db24f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db24f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db24f-112">Description</span></span>  
 <span data-ttu-id="db24f-113">Bir WCF Hizmeti işlenmeyen bir özel durumla karşılaştığında bu olay yayılır.</span><span class="sxs-lookup"><span data-stu-id="db24f-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="db24f-114">Bu ileti işleme sırasında ve kullanıcı kodunda etkinleştirme sırasında işlenmeyen özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="db24f-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="db24f-115">İleti</span><span class="sxs-lookup"><span data-stu-id="db24f-115">Message</span></span>  
 <span data-ttu-id="db24f-116">İleti işleme sırasında '%2' türünde yakalanamayan bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="db24f-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="db24f-117">ToString tam özel durum: %1.</span><span class="sxs-lookup"><span data-stu-id="db24f-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="db24f-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="db24f-118">Details</span></span>  
  
|<span data-ttu-id="db24f-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="db24f-119">Data Item Name</span></span>|<span data-ttu-id="db24f-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="db24f-120">Data Item Type</span></span>|<span data-ttu-id="db24f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db24f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="db24f-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="db24f-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="db24f-123">Arama sonucu `ToString`(CLR özel durumda).</span><span class="sxs-lookup"><span data-stu-id="db24f-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="db24f-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="db24f-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="db24f-125">CLR FullName özel durumun türü.</span><span class="sxs-lookup"><span data-stu-id="db24f-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="db24f-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="db24f-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="db24f-127">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="db24f-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="db24f-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="db24f-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="db24f-129">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="db24f-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="db24f-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="db24f-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="db24f-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="db24f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
