---
title: IMetaDataAssemblyImport::CloseEnum Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5477578491c3cbc3f5fce694820971e99b45079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444106"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="d9626-102">IMetaDataAssemblyImport::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9626-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="d9626-103">Belirtilen numaralandırma örneğine başvuru serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="d9626-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9626-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9626-104">Syntax</span></span>  
  
```  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9626-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9626-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="d9626-106">[in] Kapatılması numaralandırması örneği.</span><span class="sxs-lookup"><span data-stu-id="d9626-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9626-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9626-107">Requirements</span></span>  
 <span data-ttu-id="d9626-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9626-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9626-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d9626-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9626-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d9626-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9626-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9626-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9626-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9626-112">See Also</span></span>  
 [<span data-ttu-id="d9626-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9626-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
