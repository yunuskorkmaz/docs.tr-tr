---
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458825"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="0d01b-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="0d01b-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="0d01b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0d01b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d01b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0d01b-104">ID</span></span>|<span data-ttu-id="0d01b-105">206</span><span class="sxs-lookup"><span data-stu-id="0d01b-105">206</span></span>|  
|<span data-ttu-id="0d01b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="0d01b-106">Keywords</span></span>|<span data-ttu-id="0d01b-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0d01b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0d01b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="0d01b-108">Level</span></span>|<span data-ttu-id="0d01b-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="0d01b-109">Information</span></span>|  
|<span data-ttu-id="0d01b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="0d01b-110">Channel</span></span>|<span data-ttu-id="0d01b-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="0d01b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0d01b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d01b-112">Description</span></span>  
 <span data-ttu-id="0d01b-113">Bu olay sonra yayılan bir `ErrorHandler` bir hizmet işlemi oluştu özel bir durumu işlemek için bir fırsat oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="0d01b-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0d01b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="0d01b-114">Message</span></span>  
 <span data-ttu-id="0d01b-115">Dağıtıcı '%3' türünde bir özel durum ile '%1' türünde bir ErrorHandler çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0d01b-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="0d01b-116">ErrorHandled == '%2'.</span><span class="sxs-lookup"><span data-stu-id="0d01b-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0d01b-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0d01b-117">Details</span></span>  
  
|<span data-ttu-id="0d01b-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0d01b-118">Data Item Name</span></span>|<span data-ttu-id="0d01b-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0d01b-119">Data Item Type</span></span>|<span data-ttu-id="0d01b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d01b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0d01b-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="0d01b-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="0d01b-122">Çağrılan türünün CLR FullName `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="0d01b-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="0d01b-123">İşlenmiş</span><span class="sxs-lookup"><span data-stu-id="0d01b-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="0d01b-124">`true` hata işleyicisine hatası, aksi takdirde işleniyorsa `false`.</span><span class="sxs-lookup"><span data-stu-id="0d01b-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="0d01b-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="0d01b-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="0d01b-126">İşlenen özel durum CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="0d01b-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="0d01b-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="0d01b-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="0d01b-128">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0d01b-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0d01b-129">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="0d01b-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0d01b-130">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="0d01b-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0d01b-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0d01b-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0d01b-132">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0d01b-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
