---
description: ': IMetaDataTables:: GetBlob Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 733f94c280283e00b644fe7811d450efbc7e1e7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688396"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="04e30-103">IMetaDataTables::GetBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="04e30-103">IMetaDataTables::GetBlob Method</span></span>

<span data-ttu-id="04e30-104">Belirtilen sütun dizininde ikili büyük nesne (BLOB) için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="04e30-104">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e30-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04e30-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04e30-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04e30-106">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="04e30-107">'ndaki Alınacak bellek adresi `ppData` .</span><span class="sxs-lookup"><span data-stu-id="04e30-107">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="04e30-108">dışı Boyutu için bayt cinsinden bir işaretçi `ppData` .</span><span class="sxs-lookup"><span data-stu-id="04e30-108">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="04e30-109">dışı Alınan ikili verilerin işaretçisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04e30-109">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e30-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04e30-110">Requirements</span></span>  

 <span data-ttu-id="04e30-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e30-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e30-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="04e30-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04e30-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="04e30-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04e30-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e30-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04e30-115">See also</span></span>

- [<span data-ttu-id="04e30-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e30-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="04e30-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e30-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
