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
ms.openlocfilehash: ac7ab7bf207cc1474090bab19818ca17fc068d3a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479226"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="9ed5d-102">IXCLRDataModule::Request yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ed5d-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="9ed5d-103">Modülün verilerle verilen arabelleği doldurmak için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="9ed5d-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9ed5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ed5d-104">Syntax</span></span>
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="9ed5d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ed5d-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="9ed5d-106">[in] İstek gönderilmesine izin türü.</span><span class="sxs-lookup"><span data-stu-id="9ed5d-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="9ed5d-107">[in] geçirilmesi giriş arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="9ed5d-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="9ed5d-108">[size_is(inBufferSize)] İstekte gönderilmek üzere ham verileri arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9ed5d-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="9ed5d-109">[in] Çıkış arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="9ed5d-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="9ed5d-110">[out, size_is(outBufferSize)] İstek yanıt depolamak için kullanılan arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9ed5d-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ed5d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ed5d-111">Remarks</span></span>

<span data-ttu-id="9ed5d-112">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 36th yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9ed5d-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ed5d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ed5d-113">Requirements</span></span>

<span data-ttu-id="9ed5d-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed5d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9ed5d-115">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9ed5d-115">**Header:** None</span></span>   
<span data-ttu-id="9ed5d-116">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9ed5d-116">**Library:** None</span></span>  
<span data-ttu-id="9ed5d-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed5d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9ed5d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ed5d-118">See also</span></span>
- [<span data-ttu-id="9ed5d-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9ed5d-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="9ed5d-120">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ed5d-120">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)