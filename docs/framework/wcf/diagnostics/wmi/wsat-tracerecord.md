---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194780"
---
# <a name="wsattracerecord"></a><span data-ttu-id="04368-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="04368-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="04368-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="04368-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04368-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04368-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="04368-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="04368-105">Methods</span></span>  
 <span data-ttu-id="04368-106">WSAT_TraceRecord sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="04368-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="04368-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="04368-107">Properties</span></span>  
 <span data-ttu-id="04368-108">WSAT_TraceRecord sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="04368-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="04368-109">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="04368-109">ActivityID</span></span>  
 <span data-ttu-id="04368-110">Veri türü: nesne</span><span class="sxs-lookup"><span data-stu-id="04368-110">Data type: object</span></span>  
<span data-ttu-id="04368-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="04368-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04368-112">İzleme kayıt etkinlik kimliği.</span><span class="sxs-lookup"><span data-stu-id="04368-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="04368-113">EventID</span><span class="sxs-lookup"><span data-stu-id="04368-113">EventID</span></span>  
 <span data-ttu-id="04368-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="04368-114">Data type: sint32</span></span>  
<span data-ttu-id="04368-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="04368-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04368-116">İzleme kayıt olay kimliği.</span><span class="sxs-lookup"><span data-stu-id="04368-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="04368-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="04368-117">TraceRecord</span></span>  
 <span data-ttu-id="04368-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="04368-118">Data type: string</span></span>  
<span data-ttu-id="04368-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="04368-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04368-120">Kayıt izleme</span><span class="sxs-lookup"><span data-stu-id="04368-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04368-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04368-121">Requirements</span></span>  
  
|<span data-ttu-id="04368-122">MOF</span><span class="sxs-lookup"><span data-stu-id="04368-122">MOF</span></span>|<span data-ttu-id="04368-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="04368-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="04368-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="04368-124">Namespace</span></span>|<span data-ttu-id="04368-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="04368-125">Defined in root\ServiceModel</span></span>|
