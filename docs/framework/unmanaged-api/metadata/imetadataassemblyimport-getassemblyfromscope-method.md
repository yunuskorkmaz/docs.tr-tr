---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: GetAssemblyFromScope yöntemi'
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
ms.openlocfilehash: 78e2862fca80dc06c37436f3d81db4b19c4ec332
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784164"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="912c3-103">IMetaDataAssemblyImport::GetAssemblyFromScope Metodu</span><span class="sxs-lookup"><span data-stu-id="912c3-103">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>

<span data-ttu-id="912c3-104">Geçerli kapsamdaki derleme için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="912c3-104">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912c3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="912c3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="912c3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="912c3-106">Parameters</span></span>  

 `ptkAssembly`  
 <span data-ttu-id="912c3-107">dışı `mdAssembly` Derlemeyi tanımlayan alınan belirtecin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="912c3-107">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="912c3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="912c3-108">Requirements</span></span>  

 <span data-ttu-id="912c3-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="912c3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="912c3-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="912c3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="912c3-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="912c3-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="912c3-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912c3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912c3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="912c3-113">See also</span></span>

- [<span data-ttu-id="912c3-114">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="912c3-114">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
