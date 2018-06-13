---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 1136647ce668dbb69bdb8acf8ed62343831464b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487782"
---
# <a name="wsattracerecord"></a><span data-ttu-id="cb31f-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="cb31f-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="cb31f-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="cb31f-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb31f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb31f-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cb31f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cb31f-105">Methods</span></span>  
 <span data-ttu-id="cb31f-106">WSAT_TraceRecord sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="cb31f-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cb31f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cb31f-107">Properties</span></span>  
 <span data-ttu-id="cb31f-108">WSAT_TraceRecord sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cb31f-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="cb31f-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="cb31f-109">ActivityID</span></span>  
 <span data-ttu-id="cb31f-110">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="cb31f-110">Data type: object</span></span>  
<span data-ttu-id="cb31f-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cb31f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb31f-112">İzleme kaydı etkinlik kimliği.</span><span class="sxs-lookup"><span data-stu-id="cb31f-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="cb31f-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="cb31f-113">EventID</span></span>  
 <span data-ttu-id="cb31f-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cb31f-114">Data type: sint32</span></span>  
<span data-ttu-id="cb31f-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cb31f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb31f-116">İzleme kaydı olay kimliği.</span><span class="sxs-lookup"><span data-stu-id="cb31f-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="cb31f-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="cb31f-117">TraceRecord</span></span>  
 <span data-ttu-id="cb31f-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cb31f-118">Data type: string</span></span>  
<span data-ttu-id="cb31f-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cb31f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb31f-120">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="cb31f-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb31f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb31f-121">Requirements</span></span>  
  
|<span data-ttu-id="cb31f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cb31f-122">MOF</span></span>|<span data-ttu-id="cb31f-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cb31f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cb31f-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cb31f-124">Namespace</span></span>|<span data-ttu-id="cb31f-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cb31f-125">Defined in root\ServiceModel</span></span>|
