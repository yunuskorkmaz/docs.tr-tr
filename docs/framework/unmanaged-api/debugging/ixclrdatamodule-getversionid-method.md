---
title: 'IXCLRDataModule:: Getversionıd yöntemi'
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
ms.openlocfilehash: ff8ccf42d1131fb15d7473ae12ecefde9d55177f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395287"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="81879-102">IXCLRDataModule:: Getversionıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="81879-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="81879-103">Modülün sürüm tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="81879-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="81879-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81879-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="81879-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81879-105">Parameters</span></span>

`vid`\
<span data-ttu-id="81879-106">dışı Modülün sürüm tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="81879-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="81879-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81879-107">Remarks</span></span>

<span data-ttu-id="81879-108">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 41 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="81879-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="81879-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81879-109">Requirements</span></span>

<span data-ttu-id="81879-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81879-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="81879-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="81879-111">**Header:** None</span></span>  
<span data-ttu-id="81879-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="81879-112">**Library:** None</span></span>  
<span data-ttu-id="81879-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="81879-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="81879-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81879-114">See also</span></span>

- [<span data-ttu-id="81879-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="81879-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="81879-116">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81879-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
