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
ms.openlocfilehash: a02a60668ae6caaad1940395822758331b93f550
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119801"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="d6816-102">IXCLRDataModule::Request yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6816-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="d6816-103">Modülün verilerle verilen arabelleği doldurmak için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="d6816-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d6816-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6816-104">Syntax</span></span>
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="d6816-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6816-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="d6816-106">[in] İstek gönderilmesine izin türü.</span><span class="sxs-lookup"><span data-stu-id="d6816-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="d6816-107">[in] geçirilmesi giriş arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="d6816-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="d6816-108">[size_is(inBufferSize)] İstekte gönderilmek üzere ham verileri arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d6816-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="d6816-109">[in] Çıkış arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="d6816-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="d6816-110">[out, size_is(outBufferSize)] İstek yanıt depolamak için kullanılan arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d6816-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6816-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6816-111">Remarks</span></span>

<span data-ttu-id="d6816-112">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 36th yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d6816-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6816-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6816-113">Requirements</span></span>

<span data-ttu-id="d6816-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6816-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d6816-115">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="d6816-115">**Header:** None</span></span>   
<span data-ttu-id="d6816-116">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="d6816-116">**Library:** None</span></span>  
**<span data-ttu-id="d6816-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d6816-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="d6816-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6816-118">See also</span></span>

- [<span data-ttu-id="d6816-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d6816-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="d6816-120">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6816-120">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)