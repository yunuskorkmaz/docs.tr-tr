---
title: 'Icordebugmergedassemblyrecord:: GetCulture yöntemi'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: 77ad8ee7977096e87b9fd2e131920a042243560e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793152"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="5793b-102">Icordebugmergedassemblyrecord:: GetCulture yöntemi</span><span class="sxs-lookup"><span data-stu-id="5793b-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="5793b-103">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="5793b-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5793b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5793b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5793b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5793b-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="5793b-106">'ndaki `szCulture` arabelleğindeki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5793b-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="5793b-107">dışı Gerçekten `szCulture` arabelleğine yazılan karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5793b-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="5793b-108">dışı Kültür adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="5793b-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5793b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5793b-109">Remarks</span></span>  
 <span data-ttu-id="5793b-110">Kültür adı, "en-US" (Ingilizce (Birleşik Devletler) kültürü için) veya "nötr" (nötr kültür için) gibi bir kültürü tanımlayan benzersiz bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5793b-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5793b-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5793b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5793b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5793b-112">Requirements</span></span>  
 <span data-ttu-id="5793b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5793b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5793b-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5793b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5793b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5793b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5793b-116">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5793b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5793b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5793b-117">See also</span></span>

- [<span data-ttu-id="5793b-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5793b-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="5793b-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5793b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
