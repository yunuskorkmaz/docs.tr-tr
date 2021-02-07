---
description: 'Hakkında daha fazla bilgi edinin: WSAT_TraceRecord'
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 67202c5d2910783c40b934d2da6108e6b514a728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756883"
---
# <a name="wsat_tracerecord"></a><span data-ttu-id="b4398-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="b4398-103">WSAT_TraceRecord</span></span>

<span data-ttu-id="b4398-104">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="b4398-104">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4398-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b4398-105">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b4398-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b4398-106">Methods</span></span>  

 <span data-ttu-id="b4398-107">WSAT_TraceRecord sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b4398-107">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b4398-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b4398-108">Properties</span></span>  

 <span data-ttu-id="b4398-109">WSAT_TraceRecord sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b4398-109">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="b4398-110">ActivityID</span><span class="sxs-lookup"><span data-stu-id="b4398-110">ActivityID</span></span>  

 <span data-ttu-id="b4398-111">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="b4398-111">Data type: object</span></span>  
<span data-ttu-id="b4398-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4398-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4398-113">İzleme kaydının etkinlik KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b4398-113">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="b4398-114">EventID</span><span class="sxs-lookup"><span data-stu-id="b4398-114">EventID</span></span>  

 <span data-ttu-id="b4398-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="b4398-115">Data type: sint32</span></span>  
<span data-ttu-id="b4398-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4398-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4398-117">İzleme kaydının olay KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b4398-117">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="b4398-118">Izleme kaydı</span><span class="sxs-lookup"><span data-stu-id="b4398-118">TraceRecord</span></span>  

 <span data-ttu-id="b4398-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b4398-119">Data type: string</span></span>  
<span data-ttu-id="b4398-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b4398-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4398-121">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="b4398-121">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4398-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4398-122">Requirements</span></span>  
  
|<span data-ttu-id="b4398-123">MOF</span><span class="sxs-lookup"><span data-stu-id="b4398-123">MOF</span></span>|<span data-ttu-id="b4398-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4398-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b4398-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b4398-125">Namespace</span></span>|<span data-ttu-id="b4398-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="b4398-126">Defined in root\ServiceModel</span></span>|
