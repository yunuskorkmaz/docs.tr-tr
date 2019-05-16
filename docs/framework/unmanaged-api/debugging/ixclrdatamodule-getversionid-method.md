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
ms.openlocfilehash: 6ec18bcf079c7687df4ac9b7c5db23b84383c517
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632304"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="d76bb-102">IXCLRDataModule::GetVersionId yöntemi</span><span class="sxs-lookup"><span data-stu-id="d76bb-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="d76bb-103">Modülün sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="d76bb-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d76bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d76bb-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="d76bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d76bb-105">Parameters</span></span>

`vid`\
<span data-ttu-id="d76bb-106">[out] Modülün sürüm tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d76bb-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="d76bb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d76bb-107">Remarks</span></span>

<span data-ttu-id="d76bb-108">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 40th yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d76bb-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d76bb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d76bb-109">Requirements</span></span>

<span data-ttu-id="d76bb-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d76bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d76bb-111">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="d76bb-111">**Header:** None</span></span>  
<span data-ttu-id="d76bb-112">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="d76bb-112">**Library:** None</span></span>  
<span data-ttu-id="d76bb-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d76bb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d76bb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d76bb-114">See also</span></span>

- [<span data-ttu-id="d76bb-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d76bb-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="d76bb-116">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="d76bb-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
