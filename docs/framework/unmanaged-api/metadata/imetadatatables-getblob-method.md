---
title: IMetaDataTables::GetBlob Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: 32f32625ee40d50249ce3e009add543c4137b196
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726476"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="3845e-102">IMetaDataTables::GetBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="3845e-102">IMetaDataTables::GetBlob Method</span></span>

<span data-ttu-id="3845e-103">Belirtilen sütun dizininde ikili büyük nesne (BLOB) için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="3845e-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3845e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3845e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3845e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3845e-105">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="3845e-106">'ndaki Alınacak bellek adresi `ppData` .</span><span class="sxs-lookup"><span data-stu-id="3845e-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="3845e-107">dışı Boyutu için bayt cinsinden bir işaretçi `ppData` .</span><span class="sxs-lookup"><span data-stu-id="3845e-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="3845e-108">dışı Alınan ikili verilerin işaretçisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3845e-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3845e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3845e-109">Requirements</span></span>  

 <span data-ttu-id="3845e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3845e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3845e-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3845e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3845e-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3845e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3845e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3845e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3845e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3845e-114">See also</span></span>

- [<span data-ttu-id="3845e-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3845e-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="3845e-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3845e-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
