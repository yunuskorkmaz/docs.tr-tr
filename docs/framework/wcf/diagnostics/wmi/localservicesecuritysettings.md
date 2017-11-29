---
title: LocalServiceSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74eff3a6193e6507c1049accf4c43c3ecc8d30a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="e7a41-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e7a41-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="e7a41-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e7a41-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a41-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7a41-104">Syntax</span></span>  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e7a41-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e7a41-105">Methods</span></span>  
 <span data-ttu-id="e7a41-106">LocalServiceSecuritySettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e7a41-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e7a41-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e7a41-107">Properties</span></span>  
 <span data-ttu-id="e7a41-108">LocalServiceSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e7a41-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="e7a41-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="e7a41-109">DetectReplays</span></span>  
 <span data-ttu-id="e7a41-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="e7a41-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e7a41-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-112">Yeniden yürütme saldırılarına karşı kanal algılandı ve otomatik olarak ele olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e7a41-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="e7a41-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="e7a41-113">InactivityTimeout</span></span>  
 <span data-ttu-id="e7a41-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7a41-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-116">Hizmeti destekler güvenlik oturumları bekleyen maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="e7a41-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="e7a41-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="e7a41-118">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7a41-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-120">Tüm yeni güvenlik tanımlama bilgilerine verilen ömür süresini belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="e7a41-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="e7a41-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="e7a41-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="e7a41-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e7a41-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="e7a41-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-124">Önbelleğe alınacak tanımlama bilgisi maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="e7a41-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="e7a41-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="e7a41-125">MaxClockSkew</span></span>  
 <span data-ttu-id="e7a41-126">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7a41-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-128">İki iletişim kuran tarafların sistem saatlerinin arasındaki en büyük zaman farkı belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="e7a41-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="e7a41-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="e7a41-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="e7a41-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e7a41-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="e7a41-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-132">Hizmet bağlantılarında bekleyen maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="e7a41-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="e7a41-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="e7a41-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="e7a41-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e7a41-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="e7a41-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-136">Aynı anda etkin olabilen güvenlik anlaşmaları sayısı.</span><span class="sxs-lookup"><span data-stu-id="e7a41-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="e7a41-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="e7a41-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="e7a41-138">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7a41-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-140">Sunucu ve istemci arasındaki güvenlik anlaşması aşaması için en fazla süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="e7a41-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="e7a41-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="e7a41-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="e7a41-142">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="e7a41-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="e7a41-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-144">WS güvenilir Mesajlaşma kullanarak bağlantıları aktarım hataları sonra yeniden bağlanmayı denemek olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e7a41-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="e7a41-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="e7a41-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="e7a41-146">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e7a41-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="e7a41-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-148">Yeniden yürütme algılaması için önbelleğe alınan nonce sayısı.</span><span class="sxs-lookup"><span data-stu-id="e7a41-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="e7a41-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="e7a41-149">ReplayWindow</span></span>  
 <span data-ttu-id="e7a41-150">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7a41-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-152">Tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="e7a41-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="e7a41-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="e7a41-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="e7a41-154">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7a41-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-156">Sonra ve Başlatıcı anahtarı için güvenlik oturumu yeniler süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="e7a41-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="e7a41-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="e7a41-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="e7a41-158">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7a41-159">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-160">Zaman aralığını belirten bir TimeSpan anahtar yenileme sırasında bir önceki oturum anahtarı gelen iletileri geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e7a41-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="e7a41-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="e7a41-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="e7a41-162">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e7a41-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7a41-163">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7a41-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7a41-164">Zaman damgası geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="e7a41-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a41-165">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7a41-165">Requirements</span></span>  
  
|<span data-ttu-id="e7a41-166">MOF</span><span class="sxs-lookup"><span data-stu-id="e7a41-166">MOF</span></span>|<span data-ttu-id="e7a41-167">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e7a41-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e7a41-168">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e7a41-168">Namespace</span></span>|<span data-ttu-id="e7a41-169">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e7a41-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7a41-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7a41-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
