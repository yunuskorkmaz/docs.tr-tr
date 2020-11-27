---
title: Hizmet
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: aa4eecbcc8a2ef818cd99d777b0e3c2f1f222e46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273288"
---
# <a name="service"></a><span data-ttu-id="e963a-102">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e963a-102">Service</span></span>

<span data-ttu-id="e963a-103">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e963a-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e963a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e963a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="e963a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e963a-105">Methods</span></span>  

 <span data-ttu-id="e963a-106">Hizmet sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e963a-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e963a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e963a-107">Properties</span></span>  

 <span data-ttu-id="e963a-108">Hizmet sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e963a-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="e963a-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="e963a-109">BaseAddresses</span></span>  

 <span data-ttu-id="e963a-110">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="e963a-110">Data type: string array</span></span>  
  
 <span data-ttu-id="e963a-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-112">Hizmet tarafından kullanılan taban adresler.</span><span class="sxs-lookup"><span data-stu-id="e963a-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="e963a-113">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="e963a-113">Behaviors</span></span>  

 <span data-ttu-id="e963a-114">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="e963a-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="e963a-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-116">Bu hizmetle ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="e963a-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="e963a-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="e963a-117">ConfigurationName</span></span>  

 <span data-ttu-id="e963a-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e963a-118">Data type: string</span></span>  
  
 <span data-ttu-id="e963a-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e963a-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="e963a-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="e963a-121">CounterInstanceName</span></span>  

 <span data-ttu-id="e963a-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e963a-122">Data type: string</span></span>  
  
 <span data-ttu-id="e963a-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-124">Hizmetin performans sayaçları örneğinin örnek adı.</span><span class="sxs-lookup"><span data-stu-id="e963a-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="e963a-125">DistinguishedName 'dir</span><span class="sxs-lookup"><span data-stu-id="e963a-125">DistinguishedName</span></span>  

 <span data-ttu-id="e963a-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e963a-126">Data type: string</span></span>  
  
 <span data-ttu-id="e963a-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-128">Adreste hizmet adı.</span><span class="sxs-lookup"><span data-stu-id="e963a-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="e963a-129">Uzantıları</span><span class="sxs-lookup"><span data-stu-id="e963a-129">Extensions</span></span>  

 <span data-ttu-id="e963a-130">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="e963a-130">Data type: string array</span></span>  
  
 <span data-ttu-id="e963a-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-132">Hizmet örneği uzantılarının örnek bağlamları.</span><span class="sxs-lookup"><span data-stu-id="e963a-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="e963a-133">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="e963a-133">Metadata</span></span>  

 <span data-ttu-id="e963a-134">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="e963a-134">Data type: string array</span></span>  
  
 <span data-ttu-id="e963a-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-136">Hizmet meta verileri ayarları.</span><span class="sxs-lookup"><span data-stu-id="e963a-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="e963a-137">Adı</span><span class="sxs-lookup"><span data-stu-id="e963a-137">Name</span></span>  

 <span data-ttu-id="e963a-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e963a-138">Data type: string</span></span>  
  
 <span data-ttu-id="e963a-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-140">Bu hizmetin benzersiz adı.</span><span class="sxs-lookup"><span data-stu-id="e963a-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="e963a-141">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e963a-141">Namespace</span></span>  

 <span data-ttu-id="e963a-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e963a-142">Data type: string</span></span>  
  
 <span data-ttu-id="e963a-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-144">Hizmetin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e963a-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="e963a-145">Makta</span><span class="sxs-lookup"><span data-stu-id="e963a-145">Opened</span></span>  

 <span data-ttu-id="e963a-146">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="e963a-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="e963a-147">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-148">Hizmetin açıldığı zaman.</span><span class="sxs-lookup"><span data-stu-id="e963a-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="e963a-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="e963a-149">OutgoingChannels</span></span>  

 <span data-ttu-id="e963a-150">Veri türü: Kanal dizisi</span><span class="sxs-lookup"><span data-stu-id="e963a-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="e963a-151">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-152">Hizmet örneğinden giden kanallar.</span><span class="sxs-lookup"><span data-stu-id="e963a-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="e963a-153">Işlem</span><span class="sxs-lookup"><span data-stu-id="e963a-153">ProcessId</span></span>  

 <span data-ttu-id="e963a-154">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="e963a-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="e963a-155">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e963a-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e963a-156">Hizmeti barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="e963a-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e963a-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e963a-157">Requirements</span></span>  
  
|<span data-ttu-id="e963a-158">MOF</span><span class="sxs-lookup"><span data-stu-id="e963a-158">MOF</span></span>|<span data-ttu-id="e963a-159">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e963a-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e963a-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e963a-160">Namespace</span></span>|<span data-ttu-id="e963a-161">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="e963a-161">Defined in root\ServiceModel</span></span>|
