---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataModule:: Request Yöntemi'
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
ms.openlocfilehash: 96f4153c58a228cfb22a5cd25a53b6e60fc4dfd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800740"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="998d0-103">IXCLRDataModule:: Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="998d0-103">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="998d0-104">Modülün verileriyle verilen arabelleği doldurma istekleri.</span><span class="sxs-lookup"><span data-stu-id="998d0-104">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="998d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="998d0-105">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="998d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="998d0-106">Parameters</span></span>

`reqCode`\
<span data-ttu-id="998d0-107">'ndaki Gönderilecek istek türü.</span><span class="sxs-lookup"><span data-stu-id="998d0-107">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="998d0-108">[in] geçirilecek giriş arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="998d0-108">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="998d0-109">[in, size_is (InBufferSize)] İstekte ham verilerin gönderileceği arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="998d0-109">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="998d0-110">'ndaki Çıkış arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="998d0-110">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="998d0-111">[Out, size_is (outBufferSize)] İstek yanıtını depolamak için kullanılan arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="998d0-111">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="998d0-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="998d0-112">Remarks</span></span>

<span data-ttu-id="998d0-113">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 37yuvası yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="998d0-113">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="998d0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="998d0-114">Requirements</span></span>

<span data-ttu-id="998d0-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="998d0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="998d0-116">**Üst bilgi:** Hiçbiri **Kitaplığı:** hiçbiri **.NET Framework sürümler:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="998d0-116">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="998d0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="998d0-117">See also</span></span>

- [<span data-ttu-id="998d0-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="998d0-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="998d0-119">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="998d0-119">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
