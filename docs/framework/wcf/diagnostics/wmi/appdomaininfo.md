---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76fee9673514287dd120a215fc843e4d995e68c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="f195f-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="f195f-102">AppDomainInfo</span></span>
<span data-ttu-id="f195f-103">Uygulama etki alanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="f195f-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f195f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f195f-104">Syntax</span></span>  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f195f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f195f-105">Methods</span></span>  
 <span data-ttu-id="f195f-106">AppDomainInfo sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="f195f-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f195f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f195f-107">Properties</span></span>  
 <span data-ttu-id="f195f-108">AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f195f-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="f195f-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="f195f-109">AppDomainId</span></span>  
 <span data-ttu-id="f195f-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="f195f-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="f195f-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f195f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f195f-112">Appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="f195f-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="f195f-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="f195f-113">IsDefault</span></span>  
 <span data-ttu-id="f195f-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="f195f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="f195f-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f195f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f195f-116">Appdomain varsayılan appdomain olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f195f-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="f195f-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="f195f-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="f195f-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="f195f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f195f-119">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="f195f-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="f195f-120">Hatalı biçimlendirilmiş iletileri günlüğe olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f195f-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="f195f-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="f195f-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="f195f-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="f195f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f195f-123">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="f195f-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="f195f-124">İletiler (şifreleme ve taşımayla ilgili Dönüşümlerde önce) hizmet düzeyinde izlenip izlenmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f195f-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="f195f-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="f195f-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="f195f-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="f195f-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="f195f-127">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="f195f-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="f195f-128">İletileri aktarım düzeyinde izlenip izlenmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f195f-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="f195f-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="f195f-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="f195f-130">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="f195f-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="f195f-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f195f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f195f-132">System.Wmi.MessageLogging izleme kaynağını dinleyen izleme dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f195f-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f195f-133">Ad</span><span class="sxs-lookup"><span data-stu-id="f195f-133">Name</span></span>  
 <span data-ttu-id="f195f-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f195f-134">Data type: string</span></span>  
  
 <span data-ttu-id="f195f-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f195f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f195f-136">Uygulama etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="f195f-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="f195f-137">performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="f195f-137">PerformanceCounters</span></span>  
 <span data-ttu-id="f195f-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f195f-138">Data type: string</span></span>  
  
 <span data-ttu-id="f195f-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f195f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f195f-140">Appdomain'deki etkin performans sayaçlarının kapsamı.</span><span class="sxs-lookup"><span data-stu-id="f195f-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="f195f-141">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="f195f-141">ProcessId</span></span>  
 <span data-ttu-id="f195f-142">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="f195f-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="f195f-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f195f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f195f-144">İşlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="f195f-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="f195f-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="f195f-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="f195f-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f195f-146">Data type: string</span></span>  
  
 <span data-ttu-id="f195f-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f195f-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f195f-148">Hizmet yapılandırma yolu.</span><span class="sxs-lookup"><span data-stu-id="f195f-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="f195f-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="f195f-149">TraceLevel</span></span>  
 <span data-ttu-id="f195f-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f195f-150">Data type: string</span></span>  
  
 <span data-ttu-id="f195f-151">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="f195f-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="f195f-152">System.Wmi izleme kaynağına izleme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="f195f-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="f195f-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="f195f-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="f195f-154">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="f195f-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="f195f-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f195f-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f195f-156">System.ServiceModel izleme kaynağından dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f195f-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f195f-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f195f-157">Requirements</span></span>  
  
|<span data-ttu-id="f195f-158">MOF</span><span class="sxs-lookup"><span data-stu-id="f195f-158">MOF</span></span>|<span data-ttu-id="f195f-159">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f195f-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f195f-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f195f-160">Namespace</span></span>|<span data-ttu-id="f195f-161">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f195f-161">Defined in root\ServiceModel</span></span>|
