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
ms.openlocfilehash: 0e9d71edc580591b698ad039f8ee73e49c4e1d6a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489052"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="72709-102">ICeeGen::GetIlSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72709-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="72709-103">Belirtilen tanıtıcı tarafından başvurulan temel Ara dil kodu bölümünü alır.</span><span class="sxs-lookup"><span data-stu-id="72709-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="72709-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="72709-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72709-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72709-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72709-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72709-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="72709-107">[in] Alınacak bölümüne tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="72709-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72709-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72709-108">Requirements</span></span>  
 <span data-ttu-id="72709-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72709-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72709-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="72709-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72709-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="72709-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72709-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72709-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72709-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72709-113">See also</span></span>
- [<span data-ttu-id="72709-114">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72709-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
