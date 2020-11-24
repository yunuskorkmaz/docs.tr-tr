---
title: CreateInstallReferenceEnum İşlevi
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: 0f62b05ebbd8b27dba160c8281c1d40748c90fc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688841"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="bd10b-102">CreateInstallReferenceEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="bd10b-102">CreateInstallReferenceEnum Function</span></span>

<span data-ttu-id="bd10b-103">Belirtilen derlemeye ait başvuruların bir listesini temsil eden bir [IInstallReferenceEnum](iinstallreferenceenum-interface.md) örneği için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="bd10b-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd10b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bd10b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd10b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd10b-105">Parameters</span></span>  

 `ppRefEnum`  
 <span data-ttu-id="bd10b-106">dışı Döndürülen `IInstallReferenceEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bd10b-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="bd10b-107">'ndaki Başvuruların numaralandırılacağı derlemeyi tanımlayan [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bd10b-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bd10b-108">'ndaki Numaralandırıcının davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="bd10b-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="bd10b-109">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="bd10b-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="bd10b-110">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bd10b-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd10b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd10b-111">Requirements</span></span>  

 <span data-ttu-id="bd10b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd10b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd10b-113">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bd10b-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bd10b-114">**Kitaplık:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="bd10b-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="bd10b-115">Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd10b-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="bd10b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd10b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd10b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd10b-117">See also</span></span>

- [<span data-ttu-id="bd10b-118">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd10b-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="bd10b-119">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd10b-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="bd10b-120">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bd10b-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
