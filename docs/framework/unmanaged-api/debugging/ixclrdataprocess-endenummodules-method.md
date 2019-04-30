---
title: IXCLRDataProcess::EndEnumModules yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: de30384b4c12c4fcac3eafe580484685f8a43fa4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775433"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="79ba2-102">IXCLRDataProcess::EndEnumModules yöntemi</span><span class="sxs-lookup"><span data-stu-id="79ba2-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="79ba2-103">Modül numaralandırma sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="79ba2-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="79ba2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79ba2-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="79ba2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79ba2-105">Parameters</span></span>

`handle`\
<span data-ttu-id="79ba2-106">[out] Modülleri numaralandırma tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="79ba2-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="79ba2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79ba2-107">Remarks</span></span>

<span data-ttu-id="79ba2-108">Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 26 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="79ba2-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="79ba2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79ba2-109">Requirements</span></span>

<span data-ttu-id="79ba2-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79ba2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="79ba2-111">**Üst bilgi:** Hiçbiri **kitaplığı:** Hiçbiri **.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="79ba2-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="79ba2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79ba2-112">See also</span></span>

- [<span data-ttu-id="79ba2-113">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="79ba2-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="79ba2-114">IXCLRDataProcess arabirimi</span><span class="sxs-lookup"><span data-stu-id="79ba2-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
