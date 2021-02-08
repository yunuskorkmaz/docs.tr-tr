---
description: ': ICorDebugAppDomain:: GetName metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 56995f544e1576534e35b899a659ed409972305f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772438"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="b8f37-103">ICorDebugAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8f37-103">ICorDebugAppDomain::GetName Method</span></span>

<span data-ttu-id="b8f37-104">Uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="b8f37-104">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f37-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8f37-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8f37-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8f37-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="b8f37-107">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="b8f37-107">[in] The size of the `szName` array.</span></span> <span data-ttu-id="b8f37-108">Bu yöntemi sorgu moduna almak için bu değeri sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b8f37-108">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b8f37-109">dışı Adın boyutuna veya aslında ' de döndürülen karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="b8f37-109">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="b8f37-110">Sorgu modunda, bu değer çağıranın ad için ne kadar büyük bir arabellek ayrılacağını bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8f37-110">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="b8f37-111">dışı Uygulama etki alanının adını depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="b8f37-111">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8f37-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8f37-112">Remarks</span></span>  

 <span data-ttu-id="b8f37-113">Bir hata ayıklayıcı, `GetName` ad için gereken bir arabellek boyutunu almak üzere yöntemi bir kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="b8f37-113">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="b8f37-114">Hata ayıklayıcı arabelleği ayırır ve sonra arabelleği dolduracak ikinci kez yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b8f37-114">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="b8f37-115">Adın boyutunu almak için ilk çağrı *sorgu modu* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b8f37-115">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8f37-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8f37-116">Requirements</span></span>  

 <span data-ttu-id="b8f37-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8f37-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8f37-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8f37-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8f37-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b8f37-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8f37-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8f37-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
