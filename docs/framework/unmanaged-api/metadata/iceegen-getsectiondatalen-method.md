---
title: ICeeGen::GetSectionDataLen Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca01f78cf46d4f7543b949c820eb6b1971687e23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905482"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="97703-102">ICeeGen::GetSectionDataLen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97703-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="97703-103">Belirtilen bölüm uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="97703-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="97703-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="97703-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97703-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97703-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97703-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97703-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="97703-107">[in] Veri bölümü uzunluğunu alınır.</span><span class="sxs-lookup"><span data-stu-id="97703-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="97703-108">[out] Belirtilen bölüm döndürülen uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="97703-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97703-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97703-109">Remarks</span></span>  
 <span data-ttu-id="97703-110">Çağrı `GetSectionDataLen` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleriniz varsa.</span><span class="sxs-lookup"><span data-stu-id="97703-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97703-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97703-111">Requirements</span></span>  
 <span data-ttu-id="97703-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97703-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97703-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="97703-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97703-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="97703-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97703-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97703-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97703-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97703-116">See also</span></span>

- [<span data-ttu-id="97703-117">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97703-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
