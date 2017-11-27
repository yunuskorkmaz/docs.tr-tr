---
title: ICeeGen::GetSectionDataLen Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionDataLen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7d119fdfe5c0202d08ca78026a6917bb4ef51422
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="ba3cc-102">ICeeGen::GetSectionDataLen Metodu</span><span class="sxs-lookup"><span data-stu-id="ba3cc-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="ba3cc-103">Belirtilen bölüm uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="ba3cc-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="ba3cc-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba3cc-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba3cc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba3cc-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba3cc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba3cc-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ba3cc-107">[in] Veri bölümü uzunluğunu alınır.</span><span class="sxs-lookup"><span data-stu-id="ba3cc-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="ba3cc-108">[out] Belirtilen bölüm döndürülen uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ba3cc-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba3cc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba3cc-109">Remarks</span></span>  
 <span data-ttu-id="ba3cc-110">Çağrı `GetSectionDataLen` yalnızca diğer yöntemler tarafından işlenmemiş özel bölümü gereksinimleri varsa.</span><span class="sxs-lookup"><span data-stu-id="ba3cc-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba3cc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba3cc-111">Requirements</span></span>  
 <span data-ttu-id="ba3cc-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba3cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba3cc-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ba3cc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba3cc-114">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ba3cc-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba3cc-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba3cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba3cc-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba3cc-116">See Also</span></span>  
 [<span data-ttu-id="ba3cc-117">Iceegen arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba3cc-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
