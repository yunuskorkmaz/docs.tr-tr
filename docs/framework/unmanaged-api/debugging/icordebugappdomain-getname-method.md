---
title: ICorDebugAppDomain::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179085"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="79100-102">ICorDebugAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79100-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="79100-103">Uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="79100-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79100-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79100-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79100-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79100-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="79100-106">[içinde] `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="79100-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="79100-107">Bu yöntemi sorgu moduna koymak için bu değeri sıfıra ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="79100-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="79100-108">[çıkış] Adın boyutuna veya gerçekte döndürülen `szName`karakter sayısına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79100-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="79100-109">Sorgu modunda, bu değer arayan ada ne kadar büyük bir arabellek ayırmak için bildirin.</span><span class="sxs-lookup"><span data-stu-id="79100-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="79100-110">[çıkış] Uygulama etki alanının adını depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="79100-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79100-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79100-111">Remarks</span></span>  
 <span data-ttu-id="79100-112">Hata ayıklama, `GetName` ad için gereken arabellek boyutunu almak için yöntemi bir kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="79100-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="79100-113">Hata ayıklama arabelleği ayırır ve sonra arabellek doldurmak için yöntemi ikinci kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="79100-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="79100-114">Adın boyutunu almak için ilk arama, sorgu *modu*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="79100-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79100-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79100-115">Requirements</span></span>  
 <span data-ttu-id="79100-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79100-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79100-117">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79100-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79100-118">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79100-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79100-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79100-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
