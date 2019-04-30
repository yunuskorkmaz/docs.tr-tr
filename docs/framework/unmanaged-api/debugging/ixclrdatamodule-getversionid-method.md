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
ms.openlocfilehash: e863f14676acc84f4d9f59d0898dee5b291bd30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775446"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="30f6c-102">IXCLRDataModule::GetVersionId yöntemi</span><span class="sxs-lookup"><span data-stu-id="30f6c-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="30f6c-103">Modülün sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="30f6c-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="30f6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30f6c-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="30f6c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30f6c-105">Parameters</span></span>

`vid`\
<span data-ttu-id="30f6c-106">[out] Modülün sürüm tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="30f6c-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="30f6c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30f6c-107">Remarks</span></span>

<span data-ttu-id="30f6c-108">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 40th yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="30f6c-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="30f6c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30f6c-109">Requirements</span></span>

<span data-ttu-id="30f6c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30f6c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="30f6c-111">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="30f6c-111">**Header:** None</span></span>  
<span data-ttu-id="30f6c-112">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="30f6c-112">**Library:** None</span></span>  
<span data-ttu-id="30f6c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="30f6c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="30f6c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30f6c-114">See also</span></span>

- [<span data-ttu-id="30f6c-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="30f6c-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="30f6c-116">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="30f6c-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)