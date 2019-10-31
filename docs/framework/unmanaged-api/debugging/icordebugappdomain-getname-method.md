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
ms.openlocfilehash: 2c9aa6792885c685195049948a540453b1f5235e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110306"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="0764b-102">ICorDebugAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0764b-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="0764b-103">Uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="0764b-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0764b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0764b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0764b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0764b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0764b-106">'ndaki `szName` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="0764b-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="0764b-107">Bu yöntemi sorgu moduna almak için bu değeri sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0764b-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0764b-108">dışı Adın boyutuna veya aslında `szName`geri döndürülen karakterlerin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0764b-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="0764b-109">Sorgu modunda, bu değer çağıranın ad için ne kadar büyük bir arabellek ayrılacağını bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0764b-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="0764b-110">dışı Uygulama etki alanının adını depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="0764b-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0764b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0764b-111">Remarks</span></span>  
 <span data-ttu-id="0764b-112">Bir hata ayıklayıcı, ad için gereken bir arabellek boyutunu almak için `GetName` yöntemini bir kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="0764b-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="0764b-113">Hata ayıklayıcı arabelleği ayırır ve sonra arabelleği dolduracak ikinci kez yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0764b-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="0764b-114">Adın boyutunu almak için ilk çağrı *sorgu modu*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0764b-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0764b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0764b-115">Requirements</span></span>  
 <span data-ttu-id="0764b-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0764b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0764b-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0764b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0764b-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0764b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0764b-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0764b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
