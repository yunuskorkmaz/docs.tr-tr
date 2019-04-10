---
title: ICorDebugMergedAssemblyRecord::GetCulture yöntemi
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 093b21a439b96c9fe2f971300f314d1b75527f1f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207207"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="d9eff-102">ICorDebugMergedAssemblyRecord::GetCulture yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9eff-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="d9eff-103">Derlemenin kültür adı dizesi alır.</span><span class="sxs-lookup"><span data-stu-id="d9eff-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9eff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9eff-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9eff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9eff-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="d9eff-106">[in] Karakter sayısı `szCulture` arabellek.</span><span class="sxs-lookup"><span data-stu-id="d9eff-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="d9eff-107">[out] Gerçekte yazılan karakter sayısını `szCulture` arabellek.</span><span class="sxs-lookup"><span data-stu-id="d9eff-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="d9eff-108">[out] Kültür adı içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="d9eff-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9eff-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9eff-109">Remarks</span></span>  
 <span data-ttu-id="d9eff-110">Kültür adı "en-US" (için İngilizce (ABD) kültürünün) veya "belirsiz" (için bağımsız bir kültür) gibi bir kültür tanımlayan benzersiz bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d9eff-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9eff-111">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9eff-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9eff-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9eff-112">Requirements</span></span>  
 <span data-ttu-id="d9eff-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9eff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9eff-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9eff-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9eff-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9eff-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d9eff-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d9eff-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9eff-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9eff-117">See also</span></span>

- [<span data-ttu-id="d9eff-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9eff-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="d9eff-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d9eff-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
