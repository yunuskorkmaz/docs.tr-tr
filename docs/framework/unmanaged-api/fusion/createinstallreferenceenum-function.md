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
ms.openlocfilehash: d7820b33dcfacae5ede5235607e40d95940fc474
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092831"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="54e78-102">CreateInstallReferenceEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="54e78-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="54e78-103">Bir işaretçi alır bir [Iınstallreferenceenum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) uygulamanın belirtilen bütünleştirilmiş kod başvuruları listesini temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="54e78-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e78-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54e78-104">Syntax</span></span>  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="54e78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54e78-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="54e78-106">[out] Döndürülen `IInstallReferenceEnum` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54e78-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="54e78-107">[in] [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) derleme referanslarını listelemek istediğiniz tanımlar.</span><span class="sxs-lookup"><span data-stu-id="54e78-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="54e78-108">[in] Numaralandırıcının davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="54e78-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="54e78-109">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="54e78-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="54e78-110">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54e78-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54e78-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54e78-111">Requirements</span></span>  
 <span data-ttu-id="54e78-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54e78-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54e78-113">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="54e78-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="54e78-114">**Kitaplığı:** Fusion.dll ve kullanımda olan mscorwks.dll'ye.</span><span class="sxs-lookup"><span data-stu-id="54e78-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="54e78-115">Fusion.dll yerine Mscorwks.dll doğru .NET Framework sürümünü hedefleyen emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="54e78-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="54e78-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54e78-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e78-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e78-117">See also</span></span>

- [<span data-ttu-id="54e78-118">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e78-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
- [<span data-ttu-id="54e78-119">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54e78-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="54e78-120">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="54e78-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
