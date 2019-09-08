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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d696326ff8861ed8496474f76e9eaf89b4ead3e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795397"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="db744-102">CreateInstallReferenceEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="db744-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="db744-103">Belirtilen derlemeye ait başvuruların bir listesini temsil eden bir [IInstallReferenceEnum](iinstallreferenceenum-interface.md) örneği için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="db744-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db744-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db744-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="db744-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db744-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="db744-106">dışı Döndürülen `IInstallReferenceEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db744-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="db744-107">'ndaki Başvuruların numaralandırılacağı derlemeyi tanımlayan [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="db744-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="db744-108">'ndaki Numaralandırıcının davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="db744-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="db744-109">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="db744-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="db744-110">`pvReserved`null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db744-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db744-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db744-111">Requirements</span></span>  
 <span data-ttu-id="db744-112">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db744-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db744-113">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="db744-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="db744-114">**Kitaplığı** Fusion. dll ve mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="db744-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="db744-115">.NET Framework doğru sürümünü hedefliyorsanız emin olmak için mscorwks. dll yerine Fusion. dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="db744-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="db744-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db744-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db744-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db744-117">See also</span></span>

- [<span data-ttu-id="db744-118">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db744-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="db744-119">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db744-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="db744-120">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="db744-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
