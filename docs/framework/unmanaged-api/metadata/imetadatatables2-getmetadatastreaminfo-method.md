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
ms.openlocfilehash: 21fc79f62dba4b16a7a067dff8fb9dcc795c9d35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708731"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="a151e-102">IMetaDataTables2::GetMetaDataStreamInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="a151e-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>

<span data-ttu-id="a151e-103">Belirtilen dizindeki meta veri akışının adını, boyutunu ve içeriğini alır.</span><span class="sxs-lookup"><span data-stu-id="a151e-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a151e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a151e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a151e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a151e-105">Parameters</span></span>  

 `ix`  
 <span data-ttu-id="a151e-106">'ndaki İstenen meta veri akışının dizini.</span><span class="sxs-lookup"><span data-stu-id="a151e-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="a151e-107">dışı Akışın adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a151e-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a151e-108">dışı Meta veri akışına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a151e-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="a151e-109">dışı Bayt cinsinden boyutu `ppv` .</span><span class="sxs-lookup"><span data-stu-id="a151e-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a151e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a151e-110">Requirements</span></span>  

 <span data-ttu-id="a151e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a151e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a151e-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a151e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a151e-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a151e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a151e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a151e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a151e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a151e-115">See also</span></span>

- [<span data-ttu-id="a151e-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a151e-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="a151e-117">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a151e-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
