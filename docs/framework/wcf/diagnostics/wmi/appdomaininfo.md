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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97818cf1fc6fa1c59b8b0eeaab69a73b21360151
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="ac374-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="ac374-102">AppDomainInfo</span></span>
<span data-ttu-id="ac374-103">Uygulama etki alanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="ac374-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac374-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac374-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="ac374-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ac374-105">Methods</span></span>  
 <span data-ttu-id="ac374-106">AppDomainInfo sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="ac374-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ac374-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ac374-107">Properties</span></span>  
 <span data-ttu-id="ac374-108">AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ac374-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="ac374-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="ac374-109">AppDomainId</span></span>  
 <span data-ttu-id="ac374-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="ac374-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="ac374-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac374-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac374-112">Appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="ac374-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="ac374-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="ac374-113">IsDefault</span></span>  
 <span data-ttu-id="ac374-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="ac374-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac374-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac374-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac374-116">Appdomain varsayılan appdomain olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac374-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="ac374-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="ac374-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="ac374-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="ac374-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac374-119">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="ac374-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="ac374-120">Hatalı biçimlendirilmiş iletileri günlüğe olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ac374-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="ac374-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="ac374-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="ac374-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="ac374-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac374-123">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="ac374-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="ac374-124">İletiler (şifreleme ve taşımayla ilgili Dönüşümlerde önce) hizmet düzeyinde izlenip izlenmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ac374-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="ac374-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="ac374-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="ac374-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="ac374-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac374-127">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="ac374-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="ac374-128">İletileri aktarım düzeyinde izlenip izlenmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ac374-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="ac374-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="ac374-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="ac374-130">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="ac374-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="ac374-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac374-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac374-132">System.Wmi.MessageLogging izleme kaynağını dinleyen izleme dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ac374-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ac374-133">Ad</span><span class="sxs-lookup"><span data-stu-id="ac374-133">Name</span></span>  
 <span data-ttu-id="ac374-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ac374-134">Data type: string</span></span>  
  
 <span data-ttu-id="ac374-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac374-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac374-136">Uygulama etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="ac374-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="ac374-137">performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="ac374-137">PerformanceCounters</span></span>  
 <span data-ttu-id="ac374-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ac374-138">Data type: string</span></span>  
  
 <span data-ttu-id="ac374-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac374-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac374-140">Appdomain'deki etkin performans sayaçlarının kapsamı.</span><span class="sxs-lookup"><span data-stu-id="ac374-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="ac374-141">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="ac374-141">ProcessId</span></span>  
 <span data-ttu-id="ac374-142">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="ac374-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="ac374-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac374-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac374-144">İşlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="ac374-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="ac374-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="ac374-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="ac374-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ac374-146">Data type: string</span></span>  
  
 <span data-ttu-id="ac374-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac374-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac374-148">Hizmet yapılandırma yolu.</span><span class="sxs-lookup"><span data-stu-id="ac374-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="ac374-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="ac374-149">TraceLevel</span></span>  
 <span data-ttu-id="ac374-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ac374-150">Data type: string</span></span>  
  
 <span data-ttu-id="ac374-151">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="ac374-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="ac374-152">System.Wmi izleme kaynağına izleme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="ac374-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="ac374-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="ac374-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="ac374-154">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="ac374-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="ac374-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ac374-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac374-156">System.ServiceModel izleme kaynağından dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ac374-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac374-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac374-157">Requirements</span></span>  
  
|<span data-ttu-id="ac374-158">MOF</span><span class="sxs-lookup"><span data-stu-id="ac374-158">MOF</span></span>|<span data-ttu-id="ac374-159">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ac374-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ac374-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ac374-160">Namespace</span></span>|<span data-ttu-id="ac374-161">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ac374-161">Defined in root\ServiceModel</span></span>|
