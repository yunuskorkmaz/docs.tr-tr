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
ms.openlocfilehash: adcaac02526c7d72ffb75ba6c7552632173032cf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009047"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="cb748-102">IMetaDataAssemblyImport::GetAssemblyFromScope Metodu</span><span class="sxs-lookup"><span data-stu-id="cb748-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="cb748-103">Geçerli kapsamdaki derleme için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="cb748-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb748-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cb748-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb748-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb748-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="cb748-106">dışı `mdAssembly`Derlemeyi tanımlayan alınan belirtecin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cb748-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb748-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb748-107">Requirements</span></span>  
 <span data-ttu-id="cb748-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb748-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb748-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb748-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb748-110">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cb748-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb748-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb748-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb748-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb748-112">See also</span></span>

- [<span data-ttu-id="cb748-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb748-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
