---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8f80af782c474ccf3a232ab353125fa223d4f5d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486903"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="8ec59-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="8ec59-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="8ec59-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="8ec59-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec59-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ec59-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8ec59-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8ec59-105">Methods</span></span>  
 <span data-ttu-id="8ec59-106">LocalServiceSecuritySettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="8ec59-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8ec59-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8ec59-107">Properties</span></span>  
 <span data-ttu-id="8ec59-108">LocalServiceSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8ec59-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="8ec59-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="8ec59-109">DetectReplays</span></span>  
 <span data-ttu-id="8ec59-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8ec59-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="8ec59-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-112">Yeniden yürütme saldırılarına karşı kanal algılandı ve otomatik olarak ele olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8ec59-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="8ec59-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="8ec59-113">InactivityTimeout</span></span>  
 <span data-ttu-id="8ec59-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="8ec59-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-116">Hizmeti destekler güvenlik oturumları bekleyen maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="8ec59-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="8ec59-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="8ec59-118">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="8ec59-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-120">Tüm yeni güvenlik tanımlama bilgilerine verilen ömür süresini belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="8ec59-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="8ec59-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="8ec59-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="8ec59-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="8ec59-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="8ec59-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-124">Önbelleğe alınacak tanımlama bilgisi maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="8ec59-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="8ec59-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="8ec59-125">MaxClockSkew</span></span>  
 <span data-ttu-id="8ec59-126">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="8ec59-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-128">İki iletişim kuran tarafların sistem saatlerinin arasındaki en büyük zaman farkı belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="8ec59-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="8ec59-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="8ec59-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="8ec59-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="8ec59-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="8ec59-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-132">Hizmet bağlantılarında bekleyen maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="8ec59-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="8ec59-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="8ec59-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="8ec59-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="8ec59-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="8ec59-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-136">Aynı anda etkin olabilen güvenlik anlaşmaları sayısı.</span><span class="sxs-lookup"><span data-stu-id="8ec59-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="8ec59-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="8ec59-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="8ec59-138">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="8ec59-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-140">Sunucu ve istemci arasındaki güvenlik anlaşması aşaması için en fazla süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="8ec59-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="8ec59-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="8ec59-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="8ec59-142">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8ec59-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="8ec59-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-144">WS güvenilir Mesajlaşma kullanarak bağlantıları aktarım hataları sonra yeniden bağlanmayı denemek olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8ec59-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="8ec59-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="8ec59-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="8ec59-146">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="8ec59-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="8ec59-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-148">Yeniden yürütme algılaması için önbelleğe alınan nonce sayısı.</span><span class="sxs-lookup"><span data-stu-id="8ec59-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="8ec59-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="8ec59-149">ReplayWindow</span></span>  
 <span data-ttu-id="8ec59-150">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="8ec59-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-152">Tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="8ec59-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="8ec59-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="8ec59-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="8ec59-154">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="8ec59-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-156">Sonra ve Başlatıcı anahtarı için güvenlik oturumu yeniler süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="8ec59-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="8ec59-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="8ec59-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="8ec59-158">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="8ec59-159">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-160">Zaman aralığını belirten bir TimeSpan anahtar yenileme sırasında bir önceki oturum anahtarı gelen iletileri geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="8ec59-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="8ec59-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="8ec59-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="8ec59-162">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8ec59-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="8ec59-163">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ec59-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ec59-164">Zaman damgası geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="8ec59-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ec59-165">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ec59-165">Requirements</span></span>  
  
|<span data-ttu-id="8ec59-166">MOF</span><span class="sxs-lookup"><span data-stu-id="8ec59-166">MOF</span></span>|<span data-ttu-id="8ec59-167">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8ec59-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8ec59-168">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="8ec59-168">Namespace</span></span>|<span data-ttu-id="8ec59-169">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8ec59-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ec59-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ec59-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
