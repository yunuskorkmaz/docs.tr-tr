---
title: GetDemultiplexedStub fonksiyonu (Yönetilmeyen API Başvurusu)
description: GetDemultiplexedStub işlevi, istemcinin Windows Yönetimi'nden eşzamanlı çağrılar almasına yardımcı olmak için bir nesne iletme lavabosu oluşturur.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d15fed261db2ca2cda6dbf824dc9cb0d5c56eed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174972"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="e5dbe-103">GetDemultiplexedStub fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="e5dbe-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="e5dbe-104">Windows Yönetimi'nden eşzamanlı çağrılar almada istemciye yardımcı olmak için bir nesne ilemör lavabosu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5dbe-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e5dbe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5dbe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a><span data-ttu-id="e5dbe-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5dbe-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="e5dbe-107">[içinde] [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)istemcinin süreç içinde uygulanması için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5dbe-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="e5dbe-108">[içinde] Olayın yerel olup olmadığını belirten`true`bir bayrak ( ); aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="e5dbe-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="e5dbe-109">[çıkış] Windows Yönetimi'nden eşzamanlı çağrılar almada istemciye yardımcı olmak için bir nesne iletme lavabosu.</span><span class="sxs-lookup"><span data-stu-id="e5dbe-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5dbe-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="e5dbe-110">Return value</span></span>

<span data-ttu-id="e5dbe-111">İşlev başarılı olursa, iade `S_OK` değeri (0) olur.</span><span class="sxs-lookup"><span data-stu-id="e5dbe-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="e5dbe-112">İşlev başarısız olursa, iade değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="e5dbe-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="e5dbe-113">Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini arayın.</span><span class="sxs-lookup"><span data-stu-id="e5dbe-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5dbe-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5dbe-114">Requirements</span></span>  
 <span data-ttu-id="e5dbe-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5dbe-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5dbe-116">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e5dbe-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e5dbe-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5dbe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5dbe-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5dbe-118">See also</span></span>

- [<span data-ttu-id="e5dbe-119">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e5dbe-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
