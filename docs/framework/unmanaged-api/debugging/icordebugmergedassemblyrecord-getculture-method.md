---
title: ICorDebugMergedAssemblyRecord::GetCulture Yöntemi
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: ad54a93b16e803170987dd56d8063669f7e67f94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178748"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="82d13-102">ICorDebugMergedAssemblyRecord::GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82d13-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="82d13-103">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="82d13-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82d13-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82d13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82d13-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="82d13-106">[içinde] `szCulture` Arabellekteki karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="82d13-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="82d13-107">[çıkış] `szCulture` Arabelleğe yazılan karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="82d13-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="82d13-108">[çıkış] Kültür adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="82d13-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82d13-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82d13-109">Remarks</span></span>  
 <span data-ttu-id="82d13-110">Kültür adı, "en-US" (İngilizce (ABD) kültürü veya "tarafsız" (tarafsız bir kültür için) gibi bir kültürü tanımlayan benzersiz bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="82d13-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82d13-111">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="82d13-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82d13-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82d13-112">Requirements</span></span>  
 <span data-ttu-id="82d13-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82d13-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82d13-114">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82d13-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82d13-115">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82d13-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82d13-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82d13-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d13-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82d13-117">See also</span></span>

- [<span data-ttu-id="82d13-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82d13-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="82d13-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="82d13-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
