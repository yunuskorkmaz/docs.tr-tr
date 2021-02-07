---
description: ': CreateAssemblyNameObject Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 0eaa74bdb37a098ad58b81658229f8c04259b730
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761193"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="4637f-103">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="4637f-103">CreateAssemblyNameObject Function</span></span>

<span data-ttu-id="4637f-104">Belirtilen ada sahip derlemenin benzersiz kimliğini temsil eden bir [IAssemblyName](iassemblyname-interface.md) örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4637f-104">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4637f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4637f-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4637f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4637f-106">Parameters</span></span>  

 `ppAssemblyNameObj`  
 <span data-ttu-id="4637f-107">dışı Döndürülen `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="4637f-107">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="4637f-108">'ndaki Yeni örneğin oluşturulacağı derlemenin adı `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="4637f-108">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4637f-109">'ndaki Nesne oluşturucusuna geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="4637f-109">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4637f-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4637f-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4637f-111">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4637f-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4637f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4637f-112">Requirements</span></span>  

 <span data-ttu-id="4637f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4637f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4637f-114">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4637f-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4637f-115">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4637f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4637f-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4637f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4637f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4637f-117">See also</span></span>

- [<span data-ttu-id="4637f-118">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4637f-118">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="4637f-119">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4637f-119">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
