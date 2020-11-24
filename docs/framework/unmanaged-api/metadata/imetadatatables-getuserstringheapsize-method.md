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
ms.openlocfilehash: 048010f00f6581a29c6b1a3150bf5ae8822b5664
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672467"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="fe957-102">IMetaDataTables::GetUserStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe957-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>

<span data-ttu-id="fe957-103">Kullanıcı dizesi yığınının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="fe957-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe957-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe957-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe957-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe957-105">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="fe957-106">dışı Kullanıcı dizesi yığınının bayt cinsinden boyutu işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fe957-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe957-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe957-107">Requirements</span></span>  

 <span data-ttu-id="fe957-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe957-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe957-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fe957-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe957-110">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="fe957-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe957-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe957-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe957-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe957-112">See also</span></span>

- [<span data-ttu-id="fe957-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe957-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="fe957-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe957-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
