---
title: IMetaDataTables2::GetMetaDataStorage Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: 55fcde6c47705e515eb2d20f25ac870e257b92c0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501137"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="ec67c-102">IMetaDataTables2::GetMetaDataStorage Metodu</span><span class="sxs-lookup"><span data-stu-id="ec67c-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="ec67c-103">Belirtilen bölümde depolanan meta verilerin boyutunu ve içeriğini alır.</span><span class="sxs-lookup"><span data-stu-id="ec67c-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec67c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ec67c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec67c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec67c-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="ec67c-106">[in, out] Meta veri bölümüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec67c-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="ec67c-107">dışı Meta veri akışının boyutu.</span><span class="sxs-lookup"><span data-stu-id="ec67c-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec67c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec67c-108">Requirements</span></span>  
 <span data-ttu-id="ec67c-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec67c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec67c-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec67c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec67c-111">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ec67c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec67c-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec67c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec67c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec67c-113">See also</span></span>

- [<span data-ttu-id="ec67c-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec67c-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="ec67c-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec67c-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
