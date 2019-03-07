---
title: IMetaDataAssemblyImport::GetAssemblyFromScope Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fc82ad87721c31337002dcfc5bbfdb9300afb31
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479746"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="6b996-102">IMetaDataAssemblyImport::GetAssemblyFromScope Metodu</span><span class="sxs-lookup"><span data-stu-id="6b996-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="6b996-103">Bir işaretçi geçerli kapsamda derlemeye alır.</span><span class="sxs-lookup"><span data-stu-id="6b996-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b996-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b996-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b996-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b996-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="6b996-106">[out] Alınan bir işaretçi `mdAssembly` derleme tanımlayan belirteci.</span><span class="sxs-lookup"><span data-stu-id="6b996-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b996-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b996-107">Requirements</span></span>  
 <span data-ttu-id="6b996-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b996-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b996-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6b996-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b996-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6b996-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b996-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b996-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b996-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b996-112">See also</span></span>
- [<span data-ttu-id="6b996-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b996-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
