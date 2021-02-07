---
description: ': Icordebugmergedassemblyrecord:: GetCulture yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetCulture yöntemi'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f530bb68a1e7e4c4bff53b8f3046f6ae9ca42aab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754010"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="eae88-103">Icordebugmergedassemblyrecord:: GetCulture yöntemi</span><span class="sxs-lookup"><span data-stu-id="eae88-103">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>

<span data-ttu-id="eae88-104">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="eae88-104">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eae88-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eae88-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eae88-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eae88-106">Parameters</span></span>  

 `cchCulture`  
 <span data-ttu-id="eae88-107">'ndaki Arabellekteki karakterlerin sayısı `szCulture` .</span><span class="sxs-lookup"><span data-stu-id="eae88-107">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="eae88-108">dışı Gerçekte arabelleğe yazılan karakterlerin sayısı `szCulture` .</span><span class="sxs-lookup"><span data-stu-id="eae88-108">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="eae88-109">dışı Kültür adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="eae88-109">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eae88-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eae88-110">Remarks</span></span>  

 <span data-ttu-id="eae88-111">Kültür adı, "en-US" (Ingilizce (Birleşik Devletler) kültürü için) veya "nötr" (nötr kültür için) gibi bir kültürü tanımlayan benzersiz bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="eae88-111">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eae88-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eae88-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eae88-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eae88-113">Requirements</span></span>  

 <span data-ttu-id="eae88-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eae88-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eae88-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eae88-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eae88-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eae88-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eae88-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eae88-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae88-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eae88-118">See also</span></span>

- [<span data-ttu-id="eae88-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eae88-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="eae88-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eae88-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
