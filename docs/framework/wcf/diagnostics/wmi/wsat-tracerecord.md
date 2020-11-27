---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 0409277821a7cca3f97fcec1bb383aba9583a1f6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262222"
---
# <a name="wsat_tracerecord"></a><span data-ttu-id="b04c6-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="b04c6-102">WSAT_TraceRecord</span></span>

<span data-ttu-id="b04c6-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="b04c6-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04c6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b04c6-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b04c6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b04c6-105">Methods</span></span>  

 <span data-ttu-id="b04c6-106">WSAT_TraceRecord sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b04c6-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b04c6-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b04c6-107">Properties</span></span>  

 <span data-ttu-id="b04c6-108">WSAT_TraceRecord sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b04c6-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="b04c6-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="b04c6-109">ActivityID</span></span>  

 <span data-ttu-id="b04c6-110">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="b04c6-110">Data type: object</span></span>  
<span data-ttu-id="b04c6-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b04c6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b04c6-112">İzleme kaydının etkinlik KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b04c6-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="b04c6-113">EventID</span><span class="sxs-lookup"><span data-stu-id="b04c6-113">EventID</span></span>  

 <span data-ttu-id="b04c6-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="b04c6-114">Data type: sint32</span></span>  
<span data-ttu-id="b04c6-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b04c6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b04c6-116">İzleme kaydının olay KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b04c6-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="b04c6-117">Izleme kaydı</span><span class="sxs-lookup"><span data-stu-id="b04c6-117">TraceRecord</span></span>  

 <span data-ttu-id="b04c6-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b04c6-118">Data type: string</span></span>  
<span data-ttu-id="b04c6-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b04c6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b04c6-120">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="b04c6-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b04c6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b04c6-121">Requirements</span></span>  
  
|<span data-ttu-id="b04c6-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b04c6-122">MOF</span></span>|<span data-ttu-id="b04c6-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b04c6-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b04c6-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b04c6-124">Namespace</span></span>|<span data-ttu-id="b04c6-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="b04c6-125">Defined in root\ServiceModel</span></span>|
