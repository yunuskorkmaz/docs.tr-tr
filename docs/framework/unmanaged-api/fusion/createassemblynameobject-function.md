---
title: CreateAssemblyNameObject İşlevi
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 00345f6c95c67f0494aa721c662f56a9e98cdd7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108709"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="469c9-102">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="469c9-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="469c9-103">Belirtilen ada sahip derlemenin benzersiz kimliğini temsil eden bir [IAssemblyName](iassemblyname-interface.md) örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="469c9-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="469c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="469c9-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="469c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="469c9-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="469c9-106">dışı Döndürülen `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="469c9-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="469c9-107">'ndaki Yeni `IAssemblyName` örneğinin oluşturulacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="469c9-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="469c9-108">'ndaki Nesne oluşturucusuna geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="469c9-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="469c9-109">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="469c9-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="469c9-110">`pvReserved`, null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="469c9-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="469c9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="469c9-111">Requirements</span></span>  
 <span data-ttu-id="469c9-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="469c9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="469c9-113">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="469c9-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="469c9-114">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="469c9-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="469c9-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="469c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469c9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="469c9-116">See also</span></span>

- [<span data-ttu-id="469c9-117">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="469c9-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="469c9-118">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="469c9-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
