---
title: 'IXCLRDataModule:: Request Yöntemi'
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
ms.openlocfilehash: 3c18fc5c947cbb89fc4e9aed60d3cedcbe22d749
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420818"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="570ad-102">IXCLRDataModule:: Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="570ad-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="570ad-103">Modülün verileriyle verilen arabelleği doldurma istekleri.</span><span class="sxs-lookup"><span data-stu-id="570ad-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="570ad-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="570ad-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="570ad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="570ad-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="570ad-106">'ndaki Gönderilecek istek türü.</span><span class="sxs-lookup"><span data-stu-id="570ad-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="570ad-107">[in] geçirilecek giriş arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="570ad-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="570ad-108">[in, size_is (InBufferSize)] İstekte ham verilerin gönderileceği arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="570ad-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="570ad-109">'ndaki Çıkış arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="570ad-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="570ad-110">[Out, size_is (outBufferSize)] İstek yanıtını depolamak için kullanılan arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="570ad-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="570ad-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="570ad-111">Remarks</span></span>

<span data-ttu-id="570ad-112">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 37yuvası yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="570ad-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="570ad-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="570ad-113">Requirements</span></span>

<span data-ttu-id="570ad-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="570ad-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="570ad-115">**Üst bilgi:** Hiçbiri **Kitaplığı:** hiçbiri **.NET Framework sürümler:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="570ad-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="570ad-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="570ad-116">See also</span></span>

- [<span data-ttu-id="570ad-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="570ad-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="570ad-118">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="570ad-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
