---
title: IMetaDataEmit::SaveToStream Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 515e925c9b086823450b73cfbb558d0409b4948a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576005"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="f72db-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f72db-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="f72db-103">Belirtilen geçerli kapsamdaki tüm meta verileri kaydeder `IStream`.</span><span class="sxs-lookup"><span data-stu-id="f72db-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f72db-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f72db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f72db-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="f72db-106">[in] Kaydetmek için yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="f72db-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="f72db-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="f72db-107">[in] Reserved.</span></span> <span data-ttu-id="f72db-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f72db-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f72db-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f72db-109">Requirements</span></span>  
 <span data-ttu-id="f72db-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f72db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f72db-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f72db-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f72db-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="f72db-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f72db-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f72db-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72db-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f72db-114">See also</span></span>
- [<span data-ttu-id="f72db-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f72db-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f72db-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f72db-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
