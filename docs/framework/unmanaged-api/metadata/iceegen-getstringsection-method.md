---
title: ICeeGen::GetStringSection Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68dc80c657c3794a416f6e142f70cfb05bee2c77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745898"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="338ff-102">ICeeGen::GetStringSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="338ff-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="338ff-103">Belirtilen tanıtıcı tarafından başvurulan kod bölümünde dize gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="338ff-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="338ff-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="338ff-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="338ff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="338ff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="338ff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="338ff-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="338ff-107">[out içinde] Kod bölümüne tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="338ff-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="338ff-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="338ff-108">Requirements</span></span>  
 <span data-ttu-id="338ff-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="338ff-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="338ff-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="338ff-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="338ff-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="338ff-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="338ff-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="338ff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="338ff-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="338ff-113">See also</span></span>

- [<span data-ttu-id="338ff-114">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="338ff-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
