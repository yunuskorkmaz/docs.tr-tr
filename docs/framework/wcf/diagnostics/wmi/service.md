---
title: Hizmet
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: 0cfeb178e26f6c93e29210accf5d7866cc1fca02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487153"
---
# <a name="service"></a><span data-ttu-id="aa819-102">Hizmet</span><span class="sxs-lookup"><span data-stu-id="aa819-102">Service</span></span>
<span data-ttu-id="aa819-103">Hizmet</span><span class="sxs-lookup"><span data-stu-id="aa819-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa819-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa819-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="aa819-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aa819-105">Methods</span></span>  
 <span data-ttu-id="aa819-106">Hizmet sınıfı, herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="aa819-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aa819-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aa819-107">Properties</span></span>  
 <span data-ttu-id="aa819-108">Hizmet sınıfı, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="aa819-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="aa819-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="aa819-109">BaseAddresses</span></span>  
 <span data-ttu-id="aa819-110">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="aa819-110">Data type: string array</span></span>  
  
 <span data-ttu-id="aa819-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-112">Hizmet tarafından kullanılan temel adres.</span><span class="sxs-lookup"><span data-stu-id="aa819-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="aa819-113">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="aa819-113">Behaviors</span></span>  
 <span data-ttu-id="aa819-114">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="aa819-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="aa819-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-116">Bu hizmetle ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="aa819-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="aa819-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="aa819-117">ConfigurationName</span></span>  
 <span data-ttu-id="aa819-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aa819-118">Data type: string</span></span>  
  
 <span data-ttu-id="aa819-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="aa819-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="aa819-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="aa819-121">CounterInstanceName</span></span>  
 <span data-ttu-id="aa819-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aa819-122">Data type: string</span></span>  
  
 <span data-ttu-id="aa819-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-124">Hizmetinin performans sayaçları örneğinin örnek adı.</span><span class="sxs-lookup"><span data-stu-id="aa819-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="aa819-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="aa819-125">DistinguishedName</span></span>  
 <span data-ttu-id="aa819-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aa819-126">Data type: string</span></span>  
  
 <span data-ttu-id="aa819-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-128">Adresteki hizmet adı.</span><span class="sxs-lookup"><span data-stu-id="aa819-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="aa819-129">Uzantıları</span><span class="sxs-lookup"><span data-stu-id="aa819-129">Extensions</span></span>  
 <span data-ttu-id="aa819-130">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="aa819-130">Data type: string array</span></span>  
  
 <span data-ttu-id="aa819-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-132">Hizmet örneği uzantıları için örnek bağlamı.</span><span class="sxs-lookup"><span data-stu-id="aa819-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="aa819-133">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="aa819-133">Metadata</span></span>  
 <span data-ttu-id="aa819-134">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="aa819-134">Data type: string array</span></span>  
  
 <span data-ttu-id="aa819-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-136">Hizmet meta veri ayarları.</span><span class="sxs-lookup"><span data-stu-id="aa819-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="aa819-137">Ad</span><span class="sxs-lookup"><span data-stu-id="aa819-137">Name</span></span>  
 <span data-ttu-id="aa819-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aa819-138">Data type: string</span></span>  
  
 <span data-ttu-id="aa819-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-140">Bu hizmetin benzersiz adı.</span><span class="sxs-lookup"><span data-stu-id="aa819-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="aa819-141">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="aa819-141">Namespace</span></span>  
 <span data-ttu-id="aa819-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aa819-142">Data type: string</span></span>  
  
 <span data-ttu-id="aa819-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-144">Hizmet ad alanı.</span><span class="sxs-lookup"><span data-stu-id="aa819-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="aa819-145">Açılan</span><span class="sxs-lookup"><span data-stu-id="aa819-145">Opened</span></span>  
 <span data-ttu-id="aa819-146">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="aa819-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="aa819-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-148">Hizmetin açıldığı zaman.</span><span class="sxs-lookup"><span data-stu-id="aa819-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="aa819-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="aa819-149">OutgoingChannels</span></span>  
 <span data-ttu-id="aa819-150">Veri türü: kanal dizisi</span><span class="sxs-lookup"><span data-stu-id="aa819-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="aa819-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-152">Hizmet örneğinden giden kanallar.</span><span class="sxs-lookup"><span data-stu-id="aa819-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="aa819-153">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="aa819-153">ProcessId</span></span>  
 <span data-ttu-id="aa819-154">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="aa819-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="aa819-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa819-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa819-156">Hizmeti barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="aa819-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa819-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa819-157">Requirements</span></span>  
  
|<span data-ttu-id="aa819-158">MOF</span><span class="sxs-lookup"><span data-stu-id="aa819-158">MOF</span></span>|<span data-ttu-id="aa819-159">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="aa819-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aa819-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="aa819-160">Namespace</span></span>|<span data-ttu-id="aa819-161">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aa819-161">Defined in root\ServiceModel</span></span>|
