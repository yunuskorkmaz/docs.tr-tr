---
title: ICeeGen::GetIlSection Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bddb782e13b4e7400c7e4a8128dc333efc8141d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746183"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="50cca-102">ICeeGen::GetIlSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50cca-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="50cca-103">Belirtilen tanıtıcı tarafından başvurulan temel Ara dil kodu bölümünü alır.</span><span class="sxs-lookup"><span data-stu-id="50cca-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="50cca-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="50cca-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50cca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50cca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50cca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50cca-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="50cca-107">[in] Alınacak bölümüne tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="50cca-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50cca-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50cca-108">Requirements</span></span>  
 <span data-ttu-id="50cca-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50cca-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50cca-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="50cca-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50cca-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="50cca-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50cca-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50cca-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50cca-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50cca-113">See also</span></span>

- [<span data-ttu-id="50cca-114">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50cca-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
