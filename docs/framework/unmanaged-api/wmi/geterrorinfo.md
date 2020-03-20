---
title: GetErrorInfo işlevi (Yönetilmeyen API Başvurusu)
description: GetErrorInfo işlevi önceki işlev çağrısından hata bilgilerini alır.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 802ee66a5be213ac7a599b193ec6de589773ea17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176818"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="88493-103">GetErrorInfo fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="88493-103">GetErrorInfo function</span></span>
<span data-ttu-id="88493-104">Önceki işlev çağrısından hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="88493-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="88493-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88493-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="88493-106">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="88493-106">Return value</span></span>

<span data-ttu-id="88493-107">İşlev çağrısı başarılı olursa veya `null` başarısız olursa [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) nesnesine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88493-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="88493-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88493-108">Remarks</span></span>

<span data-ttu-id="88493-109">Bu [işlev, IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="88493-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="88493-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88493-110">Requirements</span></span>  
 <span data-ttu-id="88493-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88493-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88493-112">**Üstbilgi:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="88493-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="88493-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="88493-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88493-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88493-114">See also</span></span>

- [<span data-ttu-id="88493-115">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="88493-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
