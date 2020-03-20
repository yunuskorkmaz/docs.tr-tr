---
title: ICorDebugProcess::EnumerateAppDomains Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
ms.openlocfilehash: 4489238df05edef384b4073ee738a184ff8809ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178666"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="a7c16-102">ICorDebugProcess::EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7c16-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="a7c16-103">Bu işlemdeki tüm uygulama etki alanlarını oyalar.</span><span class="sxs-lookup"><span data-stu-id="a7c16-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c16-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7c16-104">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7c16-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7c16-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="a7c16-106">[çıkış] Bu işlemde uygulama etki alanları için bir sayısallaştırıcı bir [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) adresine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7c16-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7c16-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7c16-107">Remarks</span></span>  
 <span data-ttu-id="a7c16-108">Bu yöntem [ICorDebugManagedCallback önce kullanılabilir::CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri arama.</span><span class="sxs-lookup"><span data-stu-id="a7c16-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7c16-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7c16-109">Requirements</span></span>  
 <span data-ttu-id="a7c16-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7c16-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7c16-111">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7c16-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7c16-112">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7c16-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7c16-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c16-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
