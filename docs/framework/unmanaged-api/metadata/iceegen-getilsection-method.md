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
ms.openlocfilehash: 05f39befa8966046cd71db82da37c44f20992cff
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008813"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="a6e7d-102">ICeeGen::GetIlSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6e7d-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="a6e7d-103">Belirtilen tanıtıcı tarafından başvurulan ara dil kodu tabanının bölümünü alır.</span><span class="sxs-lookup"><span data-stu-id="a6e7d-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="a6e7d-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6e7d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6e7d-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a6e7d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6e7d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6e7d-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="a6e7d-107">'ndaki Alınacak bölüm için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="a6e7d-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6e7d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6e7d-108">Requirements</span></span>  
 <span data-ttu-id="a6e7d-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6e7d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6e7d-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a6e7d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6e7d-111">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a6e7d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6e7d-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6e7d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e7d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6e7d-113">See also</span></span>

- [<span data-ttu-id="a6e7d-114">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6e7d-114">ICeeGen Interface</span></span>](iceegen-interface.md)
