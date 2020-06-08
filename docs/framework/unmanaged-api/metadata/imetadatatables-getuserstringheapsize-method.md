---
title: IMetaDataTables::GetUserStringHeapSize Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 1aea017f17e29544e9288e1f57e6f84f9a2f6dae
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501111"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="25f83-102">IMetaDataTables::GetUserStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25f83-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="25f83-103">Kullanıcı dizesi yığınının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="25f83-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f83-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="25f83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25f83-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25f83-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="25f83-106">dışı Kullanıcı dizesi yığınının bayt cinsinden boyutu işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="25f83-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f83-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25f83-107">Requirements</span></span>  
 <span data-ttu-id="25f83-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25f83-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f83-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="25f83-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25f83-110">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="25f83-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25f83-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f83-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f83-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25f83-112">See also</span></span>

- [<span data-ttu-id="25f83-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25f83-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="25f83-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25f83-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
