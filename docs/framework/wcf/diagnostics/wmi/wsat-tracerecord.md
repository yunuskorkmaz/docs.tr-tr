---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24f74d4086a5499d3bfd4ef6183d377528acc21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="f76ee-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f76ee-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="f76ee-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f76ee-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f76ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f76ee-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f76ee-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f76ee-105">Methods</span></span>  
 <span data-ttu-id="f76ee-106">WSAT_TraceRecord sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="f76ee-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f76ee-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f76ee-107">Properties</span></span>  
 <span data-ttu-id="f76ee-108">WSAT_TraceRecord sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f76ee-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="f76ee-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="f76ee-109">ActivityID</span></span>  
 <span data-ttu-id="f76ee-110">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="f76ee-110">Data type: object</span></span>  
<span data-ttu-id="f76ee-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f76ee-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76ee-112">İzleme kaydı etkinlik kimliği.</span><span class="sxs-lookup"><span data-stu-id="f76ee-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="f76ee-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="f76ee-113">EventID</span></span>  
 <span data-ttu-id="f76ee-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="f76ee-114">Data type: sint32</span></span>  
<span data-ttu-id="f76ee-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f76ee-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76ee-116">İzleme kaydı olay kimliği.</span><span class="sxs-lookup"><span data-stu-id="f76ee-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="f76ee-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f76ee-117">TraceRecord</span></span>  
 <span data-ttu-id="f76ee-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f76ee-118">Data type: string</span></span>  
<span data-ttu-id="f76ee-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f76ee-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f76ee-120">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="f76ee-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f76ee-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f76ee-121">Requirements</span></span>  
  
|<span data-ttu-id="f76ee-122">MOF</span><span class="sxs-lookup"><span data-stu-id="f76ee-122">MOF</span></span>|<span data-ttu-id="f76ee-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f76ee-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f76ee-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f76ee-124">Namespace</span></span>|<span data-ttu-id="f76ee-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f76ee-125">Defined in root\ServiceModel</span></span>|
