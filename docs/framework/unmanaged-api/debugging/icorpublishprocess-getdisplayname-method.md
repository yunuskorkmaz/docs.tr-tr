---
title: ICorPublishProcess::GetDisplayName Metodu
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
ms.openlocfilehash: 77e801b048709949c384f642fc0d0ecb5d7eb512
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178383"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="58ac4-102">ICorPublishProcess::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="58ac4-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="58ac4-103">Bu [ICorPublishProcess](icorpublishprocess-interface.md)tarafından başvurulan işlem için yürütülebilir tam yolu alır.</span><span class="sxs-lookup"><span data-stu-id="58ac4-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ac4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58ac4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58ac4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58ac4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="58ac4-106">[içinde] `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="58ac4-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="58ac4-107">[çıkış] `szName` Dizide döndürülen geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="58ac4-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="58ac4-108">[çıkış] Yürütülebilir in tam yolu da dahil olmak üzere adı depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="58ac4-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="58ac4-109">Ad geçersiz sayılabilir.</span><span class="sxs-lookup"><span data-stu-id="58ac4-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ac4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58ac4-110">Requirements</span></span>  
 <span data-ttu-id="58ac4-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ac4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ac4-112">**Üstbilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="58ac4-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="58ac4-113">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58ac4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58ac4-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ac4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ac4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58ac4-115">See also</span></span>

- [<span data-ttu-id="58ac4-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58ac4-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
