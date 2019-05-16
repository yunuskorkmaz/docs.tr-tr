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
ms.openlocfilehash: 7d04e5630bd196ef534f72a0c3924019315f3774
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632220"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="7b233-102">IXCLRDataModule::Request yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b233-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="7b233-103">Modülün verilerle verilen arabelleği doldurmak için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="7b233-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7b233-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b233-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="7b233-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b233-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="7b233-106">[in] İstek gönderilmesine izin türü.</span><span class="sxs-lookup"><span data-stu-id="7b233-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="7b233-107">[in] geçirilmesi giriş arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="7b233-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="7b233-108">[size_is(inBufferSize)] İstekte gönderilmek üzere ham verileri arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7b233-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="7b233-109">[in] Çıkış arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="7b233-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="7b233-110">[out, size_is(outBufferSize)] İstek yanıt depolamak için kullanılan arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7b233-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b233-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b233-111">Remarks</span></span>

<span data-ttu-id="7b233-112">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 36th yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7b233-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b233-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b233-113">Requirements</span></span>

<span data-ttu-id="7b233-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b233-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="7b233-115">**Üst bilgi:** Hiçbiri **kitaplığı:** Hiçbiri **.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7b233-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7b233-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b233-116">See also</span></span>

- [<span data-ttu-id="7b233-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7b233-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="7b233-118">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b233-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
