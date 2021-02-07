---
description: ': CreateInstallReferenceEnum Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: cc7551707cb46bcf0c475a0095684dbc790836e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761159"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="f6929-103">CreateInstallReferenceEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="f6929-103">CreateInstallReferenceEnum Function</span></span>

<span data-ttu-id="f6929-104">Belirtilen derlemeye ait başvuruların bir listesini temsil eden bir [IInstallReferenceEnum](iinstallreferenceenum-interface.md) örneği için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f6929-104">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6929-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6929-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6929-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6929-106">Parameters</span></span>  

 `ppRefEnum`  
 <span data-ttu-id="f6929-107">dışı Döndürülen `IInstallReferenceEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f6929-107">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="f6929-108">'ndaki Başvuruların numaralandırılacağı derlemeyi tanımlayan [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f6929-108">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f6929-109">'ndaki Numaralandırıcının davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="f6929-109">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f6929-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f6929-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f6929-111">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6929-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6929-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6929-112">Requirements</span></span>  

 <span data-ttu-id="f6929-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6929-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6929-114">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f6929-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f6929-115">**Kitaplık:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="f6929-115">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="f6929-116">Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6929-116">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f6929-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6929-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6929-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6929-118">See also</span></span>

- [<span data-ttu-id="f6929-119">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6929-119">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="f6929-120">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6929-120">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f6929-121">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f6929-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
