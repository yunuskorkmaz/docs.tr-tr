---
description: ': ICorPublishProcess:: GetDisplayName Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7aef55a40c24953766377f21e8291bceb1594480
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794591"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="60728-103">ICorPublishProcess::GetDisplayName Metodu</span><span class="sxs-lookup"><span data-stu-id="60728-103">ICorPublishProcess::GetDisplayName Method</span></span>

<span data-ttu-id="60728-104">Bu [ICorPublishProcess](icorpublishprocess-interface.md)tarafından başvurulan işlem için yürütülebilir dosyanın tam yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="60728-104">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60728-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60728-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60728-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60728-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="60728-107">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="60728-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="60728-108">dışı Dizide döndürülen geniş karakter sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="60728-108">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="60728-109">dışı Yürütülebilir dosyanın tam yolu da dahil olmak üzere, adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="60728-109">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="60728-110">Ad null ile sonlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="60728-110">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60728-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60728-111">Requirements</span></span>  

 <span data-ttu-id="60728-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60728-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60728-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="60728-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="60728-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="60728-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60728-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60728-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60728-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60728-116">See also</span></span>

- [<span data-ttu-id="60728-117">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60728-117">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
