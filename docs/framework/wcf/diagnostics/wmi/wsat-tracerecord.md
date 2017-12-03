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
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="0899c-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="0899c-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="0899c-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="0899c-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0899c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0899c-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0899c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0899c-105">Methods</span></span>  
 <span data-ttu-id="0899c-106">WSAT_TraceRecord sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="0899c-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0899c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0899c-107">Properties</span></span>  
 <span data-ttu-id="0899c-108">WSAT_TraceRecord sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0899c-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="0899c-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="0899c-109">ActivityID</span></span>  
 <span data-ttu-id="0899c-110">Veri türü: nesnesi</span><span class="sxs-lookup"><span data-stu-id="0899c-110">Data type: object</span></span>  
<span data-ttu-id="0899c-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0899c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0899c-112">İzleme kaydı etkinlik kimliği.</span><span class="sxs-lookup"><span data-stu-id="0899c-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="0899c-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0899c-113">EventID</span></span>  
 <span data-ttu-id="0899c-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="0899c-114">Data type: sint32</span></span>  
<span data-ttu-id="0899c-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0899c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0899c-116">İzleme kaydı olay kimliği.</span><span class="sxs-lookup"><span data-stu-id="0899c-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="0899c-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="0899c-117">TraceRecord</span></span>  
 <span data-ttu-id="0899c-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="0899c-118">Data type: string</span></span>  
<span data-ttu-id="0899c-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0899c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0899c-120">İzleme kaydı</span><span class="sxs-lookup"><span data-stu-id="0899c-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0899c-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0899c-121">Requirements</span></span>  
  
|<span data-ttu-id="0899c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="0899c-122">MOF</span></span>|<span data-ttu-id="0899c-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0899c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0899c-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="0899c-124">Namespace</span></span>|<span data-ttu-id="0899c-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0899c-125">Defined in root\ServiceModel</span></span>|
