---
title: IXCLRDataModule::GetVersionId yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5184db00b10b53011f24c5096b470608e84546b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567431"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="61313-102">IXCLRDataModule::GetVersionId yöntemi</span><span class="sxs-lookup"><span data-stu-id="61313-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="61313-103">Modülün sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="61313-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="61313-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61313-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

### <a name="parameters"></a><span data-ttu-id="61313-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61313-105">Parameters</span></span>

<span data-ttu-id="61313-106">`vid` [out] Modülün sürüm tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="61313-106">`vid` [out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="61313-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61313-107">Remarks</span></span>

<span data-ttu-id="61313-108">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 40th yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="61313-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="61313-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61313-109">Requirements</span></span>

<span data-ttu-id="61313-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61313-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="61313-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="61313-111">**Header:** None</span></span>  
<span data-ttu-id="61313-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="61313-112">**Library:** None</span></span>  
<span data-ttu-id="61313-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="61313-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="61313-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61313-114">See also</span></span>

- [<span data-ttu-id="61313-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="61313-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="61313-116">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="61313-116">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
