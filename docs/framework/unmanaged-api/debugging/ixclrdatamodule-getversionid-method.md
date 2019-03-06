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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366051"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="83b95-102">IXCLRDataModule::GetVersionId yöntemi</span><span class="sxs-lookup"><span data-stu-id="83b95-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="83b95-103">Modülün sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="83b95-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="83b95-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83b95-104">Syntax</span></span>

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="83b95-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83b95-105">Parameters</span></span>

`vid`\
<span data-ttu-id="83b95-106">[out] Modülün sürüm tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="83b95-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="83b95-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83b95-107">Remarks</span></span>

<span data-ttu-id="83b95-108">Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 40th yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="83b95-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="83b95-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83b95-109">Requirements</span></span>

<span data-ttu-id="83b95-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83b95-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="83b95-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="83b95-111">**Header:** None</span></span>  
<span data-ttu-id="83b95-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="83b95-112">**Library:** None</span></span>  
<span data-ttu-id="83b95-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="83b95-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="83b95-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83b95-114">See also</span></span>

- [<span data-ttu-id="83b95-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="83b95-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="83b95-116">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="83b95-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)