---
title: 'Icordebugmergedassemblyrecord:: GetCulture yöntemi'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f39a1f17c80d27a38c0f2a8a516405f72c79bbcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131419"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="940af-102">Icordebugmergedassemblyrecord:: GetCulture yöntemi</span><span class="sxs-lookup"><span data-stu-id="940af-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="940af-103">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="940af-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="940af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="940af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="940af-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="940af-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="940af-106">'ndaki `szCulture` arabelleğindeki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="940af-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="940af-107">dışı Gerçekten `szCulture` arabelleğine yazılan karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="940af-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="940af-108">dışı Kültür adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="940af-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="940af-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="940af-109">Remarks</span></span>  
 <span data-ttu-id="940af-110">Kültür adı, "en-US" (Ingilizce (Birleşik Devletler) kültürü için) veya "nötr" (nötr kültür için) gibi bir kültürü tanımlayan benzersiz bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="940af-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="940af-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="940af-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="940af-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="940af-112">Requirements</span></span>  
 <span data-ttu-id="940af-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="940af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="940af-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="940af-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="940af-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="940af-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="940af-116">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="940af-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="940af-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="940af-117">See also</span></span>

- [<span data-ttu-id="940af-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="940af-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="940af-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="940af-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
