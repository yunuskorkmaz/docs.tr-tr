---
title: IXCLRDataModule::GetMethodDefinitionByToken Yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 294c5340caf2217f9337d654a11a63a43d46febd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176675"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="eeda3-102">IXCLRDataModule::GetMethodDefinitionByToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eeda3-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="eeda3-103">Belirli bir meta veri belirtecikarşılık gelen yöntem tanımıalır.</span><span class="sxs-lookup"><span data-stu-id="eeda3-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="eeda3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eeda3-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="eeda3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eeda3-105">Parameters</span></span>

`token`\
<span data-ttu-id="eeda3-106">[içinde] Yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="eeda3-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="eeda3-107">[çıkış] Yöntem tanımı.</span><span class="sxs-lookup"><span data-stu-id="eeda3-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="eeda3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eeda3-108">Remarks</span></span>

<span data-ttu-id="eeda3-109">Sağlanan yöntem `IXCLRDataModule` arabirimin bir parçasıdır ve sanal yöntem tablosunun 25 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="eeda3-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="eeda3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eeda3-110">Requirements</span></span>

<span data-ttu-id="eeda3-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeda3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="eeda3-112">**Üstbilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="eeda3-112">**Header:** None</span></span>  
<span data-ttu-id="eeda3-113">**Kütüphane:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="eeda3-113">**Library:** None</span></span>  
<span data-ttu-id="eeda3-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eeda3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="eeda3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eeda3-115">See also</span></span>

- [<span data-ttu-id="eeda3-116">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eeda3-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="eeda3-117">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eeda3-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
