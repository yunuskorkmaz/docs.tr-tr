---
description: 'Daha fazla bilgi edinin: hizmet'
title: Hizmet
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: e66f9a23f8c182327899904c26ff6a6368b9bdc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715632"
---
# <a name="service"></a><span data-ttu-id="059e4-103">Hizmet</span><span class="sxs-lookup"><span data-stu-id="059e4-103">Service</span></span>

<span data-ttu-id="059e4-104">Hizmet</span><span class="sxs-lookup"><span data-stu-id="059e4-104">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059e4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="059e4-105">Syntax</span></span>  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="059e4-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="059e4-106">Methods</span></span>  

 <span data-ttu-id="059e4-107">Hizmet sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="059e4-107">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="059e4-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="059e4-108">Properties</span></span>  

 <span data-ttu-id="059e4-109">Hizmet sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="059e4-109">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="059e4-110">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="059e4-110">BaseAddresses</span></span>  

 <span data-ttu-id="059e4-111">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="059e4-111">Data type: string array</span></span>  
  
 <span data-ttu-id="059e4-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-113">Hizmet tarafından kullanılan taban adresler.</span><span class="sxs-lookup"><span data-stu-id="059e4-113">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="059e4-114">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="059e4-114">Behaviors</span></span>  

 <span data-ttu-id="059e4-115">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="059e4-115">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="059e4-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-117">Bu hizmetle ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="059e4-117">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="059e4-118">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="059e4-118">ConfigurationName</span></span>  

 <span data-ttu-id="059e4-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="059e4-119">Data type: string</span></span>  
  
 <span data-ttu-id="059e4-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-121">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="059e4-121">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="059e4-122">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="059e4-122">CounterInstanceName</span></span>  

 <span data-ttu-id="059e4-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="059e4-123">Data type: string</span></span>  
  
 <span data-ttu-id="059e4-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-125">Hizmetin performans sayaçları örneğinin örnek adı.</span><span class="sxs-lookup"><span data-stu-id="059e4-125">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="059e4-126">DistinguishedName 'dir</span><span class="sxs-lookup"><span data-stu-id="059e4-126">DistinguishedName</span></span>  

 <span data-ttu-id="059e4-127">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="059e4-127">Data type: string</span></span>  
  
 <span data-ttu-id="059e4-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-129">Adreste hizmet adı.</span><span class="sxs-lookup"><span data-stu-id="059e4-129">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="059e4-130">Uzantıları</span><span class="sxs-lookup"><span data-stu-id="059e4-130">Extensions</span></span>  

 <span data-ttu-id="059e4-131">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="059e4-131">Data type: string array</span></span>  
  
 <span data-ttu-id="059e4-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-133">Hizmet örneği uzantılarının örnek bağlamları.</span><span class="sxs-lookup"><span data-stu-id="059e4-133">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="059e4-134">Meta veri</span><span class="sxs-lookup"><span data-stu-id="059e4-134">Metadata</span></span>  

 <span data-ttu-id="059e4-135">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="059e4-135">Data type: string array</span></span>  
  
 <span data-ttu-id="059e4-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-137">Hizmet meta verileri ayarları.</span><span class="sxs-lookup"><span data-stu-id="059e4-137">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="059e4-138">Name</span><span class="sxs-lookup"><span data-stu-id="059e4-138">Name</span></span>  

 <span data-ttu-id="059e4-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="059e4-139">Data type: string</span></span>  
  
 <span data-ttu-id="059e4-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-141">Bu hizmetin benzersiz adı.</span><span class="sxs-lookup"><span data-stu-id="059e4-141">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="059e4-142">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="059e4-142">Namespace</span></span>  

 <span data-ttu-id="059e4-143">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="059e4-143">Data type: string</span></span>  
  
 <span data-ttu-id="059e4-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-145">Hizmetin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="059e4-145">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="059e4-146">Makta</span><span class="sxs-lookup"><span data-stu-id="059e4-146">Opened</span></span>  

 <span data-ttu-id="059e4-147">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="059e4-147">Data type: datetime</span></span>  
  
 <span data-ttu-id="059e4-148">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-149">Hizmetin açıldığı zaman.</span><span class="sxs-lookup"><span data-stu-id="059e4-149">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="059e4-150">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="059e4-150">OutgoingChannels</span></span>  

 <span data-ttu-id="059e4-151">Veri türü: Kanal dizisi</span><span class="sxs-lookup"><span data-stu-id="059e4-151">Data type: Channel array</span></span>  
  
 <span data-ttu-id="059e4-152">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-153">Hizmet örneğinden giden kanallar.</span><span class="sxs-lookup"><span data-stu-id="059e4-153">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="059e4-154">Işlem</span><span class="sxs-lookup"><span data-stu-id="059e4-154">ProcessId</span></span>  

 <span data-ttu-id="059e4-155">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="059e4-155">Data type: sint32</span></span>  
  
 <span data-ttu-id="059e4-156">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="059e4-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="059e4-157">Hizmeti barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="059e4-157">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="059e4-158">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="059e4-158">Requirements</span></span>  
  
|<span data-ttu-id="059e4-159">MOF</span><span class="sxs-lookup"><span data-stu-id="059e4-159">MOF</span></span>|<span data-ttu-id="059e4-160">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="059e4-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="059e4-161">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="059e4-161">Namespace</span></span>|<span data-ttu-id="059e4-162">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="059e4-162">Defined in root\ServiceModel</span></span>|
