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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: babe098b16729cfcd41b48075a49b9ae9be7dfdc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117189"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="15ab9-102">IMetaDataTables::GetBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="15ab9-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="15ab9-103">Bir işaretçi ikili büyük nesne (BLOB) için belirtilen sütun dizini alır.</span><span class="sxs-lookup"><span data-stu-id="15ab9-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15ab9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15ab9-104">Syntax</span></span>  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15ab9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15ab9-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="15ab9-106">[in] Bellek adresi alınmaya başlanacağı `ppData`.</span><span class="sxs-lookup"><span data-stu-id="15ab9-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="15ab9-107">[out] Bayt cinsinden boyutu için bir işaretçi, `ppData`.</span><span class="sxs-lookup"><span data-stu-id="15ab9-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="15ab9-108">[out] İkili veriler için bir işaretçi işaretçisi alınır.</span><span class="sxs-lookup"><span data-stu-id="15ab9-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15ab9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15ab9-109">Requirements</span></span>  
 <span data-ttu-id="15ab9-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15ab9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15ab9-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="15ab9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15ab9-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="15ab9-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="15ab9-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="15ab9-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="15ab9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15ab9-114">See also</span></span>

- [<span data-ttu-id="15ab9-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15ab9-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="15ab9-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15ab9-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
