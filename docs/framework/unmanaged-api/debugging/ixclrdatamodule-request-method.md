---
title: IXCLRDataModule::Request yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0226a11b142515296d976e3d645cb2475d634420
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416149"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="56265-102">IXCLRDataModule::Request yöntemi</span><span class="sxs-lookup"><span data-stu-id="56265-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="56265-103">Modülün verilerle verilen arabelleği doldurmak için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="56265-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="56265-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56265-104">Syntax</span></span>
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

### <a name="parameters"></a><span data-ttu-id="56265-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56265-105">Parameters</span></span>

<span data-ttu-id="56265-106">`reqCode` [in] İstek gönderilmesine izin türü.</span><span class="sxs-lookup"><span data-stu-id="56265-106">`reqCode` [in] Request type to be sent.</span></span>

<span data-ttu-id="56265-107">`inBufferSize` [in] geçirilmesi giriş arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="56265-107">`inBufferSize` [in] size of the input buffer to be passed in.</span></span>

<span data-ttu-id="56265-108">`inBuffer` [size_is(inBufferSize)] İstekte gönderilmek üzere ham verileri arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="56265-108">`inBuffer` [in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

<span data-ttu-id="56265-109">`outBufferSize` [in] Çıkış arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="56265-109">`outBufferSize` [in] Size of the output buffer.</span></span>

<span data-ttu-id="56265-110">`outBuffer` [out, size_is(outBufferSize)] İstek yanıt depolamak için kullanılan arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="56265-110">`outBuffer` [out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="56265-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56265-111">Remarks</span></span>

<span data-ttu-id="56265-112">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 36th yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="56265-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="56265-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56265-113">Requirements</span></span>

<span data-ttu-id="56265-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56265-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="56265-115">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="56265-115">**Header:** None</span></span>   
<span data-ttu-id="56265-116">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="56265-116">**Library:** None</span></span>  
<span data-ttu-id="56265-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="56265-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="56265-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56265-118">See Also</span></span>
- [<span data-ttu-id="56265-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="56265-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="56265-120">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="56265-120">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
