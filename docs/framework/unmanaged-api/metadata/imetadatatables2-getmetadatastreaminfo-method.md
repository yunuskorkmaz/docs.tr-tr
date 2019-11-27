---
title: IMetaDataTables2::GetMetaDataStreamInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 279e34689169d31ad89772e90155e7f50bdbac08
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426221"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="0baff-102">IMetaDataTables2::GetMetaDataStreamInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="0baff-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="0baff-103">Belirtilen dizindeki meta veri akışının adını, boyutunu ve içeriğini alır.</span><span class="sxs-lookup"><span data-stu-id="0baff-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0baff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0baff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0baff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0baff-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="0baff-106">'ndaki İstenen meta veri akışının dizini.</span><span class="sxs-lookup"><span data-stu-id="0baff-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="0baff-107">dışı Akışın adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0baff-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0baff-108">dışı Meta veri akışına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0baff-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="0baff-109">dışı `ppv`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0baff-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0baff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0baff-110">Requirements</span></span>  
 <span data-ttu-id="0baff-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0baff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0baff-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0baff-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0baff-113">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0baff-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0baff-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0baff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0baff-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0baff-115">See also</span></span>

- [<span data-ttu-id="0baff-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0baff-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="0baff-117">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0baff-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
