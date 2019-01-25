---
title: ICeeGen::GetIlSection Metodu
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
ms.openlocfilehash: e75f46d73e068c6bdaac6ae01740ecf589c97d42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635916"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="04af8-102">ICeeGen::GetIlSection Metodu</span><span class="sxs-lookup"><span data-stu-id="04af8-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="04af8-103">Belirtilen tanıtıcı tarafından başvurulan temel Ara dil kodu bölümünü alır.</span><span class="sxs-lookup"><span data-stu-id="04af8-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="04af8-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="04af8-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04af8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04af8-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04af8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04af8-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="04af8-107">[in] Alınacak bölümüne tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="04af8-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04af8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04af8-108">Requirements</span></span>  
 <span data-ttu-id="04af8-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04af8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04af8-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="04af8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04af8-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="04af8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04af8-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04af8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04af8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04af8-113">See also</span></span>
- [<span data-ttu-id="04af8-114">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04af8-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
