---
title: ICorDebugAppDomain::GetName Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f895e749fc8f2520dbce3caf9e6c11fda78a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405775"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="1d23e-102">ICorDebugAppDomain::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="1d23e-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="1d23e-103">Uygulama etki alanı adını alır.</span><span class="sxs-lookup"><span data-stu-id="1d23e-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d23e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d23e-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d23e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d23e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1d23e-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="1d23e-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="1d23e-107">Bu yöntem sorgu moduna sıfıra bu değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d23e-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1d23e-108">[out] Boyutu adı ya da gerçekte döndürülen karakter sayısını gösteren bir işaretçi `szName`.</span><span class="sxs-lookup"><span data-stu-id="1d23e-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="1d23e-109">Sorgu modunda bu değer ne kadar büyük bir arabellek bilmeniz çağıran sağlar adını ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="1d23e-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="1d23e-110">[out] Uygulama etki alanı adını depolar bir dizi.</span><span class="sxs-lookup"><span data-stu-id="1d23e-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d23e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d23e-111">Remarks</span></span>  
 <span data-ttu-id="1d23e-112">Bir hata ayıklayıcısı çağırır `GetName` adı gerekli bir arabellek boyutu almak için bir kez yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1d23e-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="1d23e-113">Hata ayıklayıcı arabellek ayırır ve ardından arabellek doldurmak için ikinci kez yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="1d23e-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="1d23e-114">Ad boyutunu almak için ilk çağrı olarak adlandırılır *sorgu modunu*.</span><span class="sxs-lookup"><span data-stu-id="1d23e-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d23e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d23e-115">Requirements</span></span>  
 <span data-ttu-id="1d23e-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d23e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d23e-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d23e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d23e-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d23e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d23e-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d23e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
