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
ms.openlocfilehash: 7ef944fd06d07dc8c4e49061a5e72d8acc4d0465
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436352"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="8f274-102">ICeeGen::GetIlSection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f274-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="8f274-103">Belirtilen tanıtıcı tarafından başvurulan ara dil kodu tabanının bölümünü alır.</span><span class="sxs-lookup"><span data-stu-id="8f274-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="8f274-104">Bu yöntem kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f274-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f274-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f274-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f274-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f274-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="8f274-107">'ndaki Alınacak bölüm için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="8f274-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f274-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f274-108">Requirements</span></span>  
 <span data-ttu-id="8f274-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f274-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f274-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8f274-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f274-111">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8f274-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f274-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f274-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f274-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f274-113">See also</span></span>

- [<span data-ttu-id="8f274-114">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f274-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
