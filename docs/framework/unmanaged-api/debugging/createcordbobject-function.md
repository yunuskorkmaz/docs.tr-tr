---
title: CreateCordbObject İşlevi
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179229"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="0240a-102">CreateCordbObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="0240a-102">CreateCordbObject Function</span></span>
<span data-ttu-id="0240a-103">Yönetilen hata ayıklama oturumunu uzak bir işlemde anında algılamak için işlevsellik sağlayan bir hata ayıklama arabirimi[(ICorDebug)](icordebug-interface.md)oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0240a-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0240a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0240a-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0240a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0240a-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="0240a-106">[içinde] Hedef işlemin hata ayıklayıcı sürümü.</span><span class="sxs-lookup"><span data-stu-id="0240a-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="0240a-107">Bu parametre uzaktan hata ayıklama için CorDebugVersion_2_0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0240a-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="0240a-108">[çıkış] [ICorDebug](icordebug-interface.md) arabirimine atılacak ve döndürülecek bir nesneye işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0240a-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0240a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0240a-109">Return Value</span></span>  
 <span data-ttu-id="0240a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0240a-110">S_OK</span></span>  
 <span data-ttu-id="0240a-111">İşlemdeki CLR sayısı başarıyla belirlendi ve karşılık gelen tutamaç ve yol dizileri düzgün şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="0240a-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="0240a-112">E_ınvalıdarg</span><span class="sxs-lookup"><span data-stu-id="0240a-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="0240a-113">`ppCordb`null veya `iDebuggerVersion` CorDebugVersion_2_0 değildir.</span><span class="sxs-lookup"><span data-stu-id="0240a-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="0240a-114">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="0240a-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="0240a-115">Için yeterli bellek ayrılamıyor`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="0240a-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="0240a-116">E_FAIL (veya diğer E_ iade kodları)</span><span class="sxs-lookup"><span data-stu-id="0240a-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="0240a-117">Diğer başarısızlıklar.</span><span class="sxs-lookup"><span data-stu-id="0240a-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0240a-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0240a-118">Remarks</span></span>  
 <span data-ttu-id="0240a-119">Döndürülen [ICorDebug](icordebug-interface.md) `ppCordb` arabirimi, yönetilen tüm hata ayıklama hizmetleri için üst düzey hata ayıklama arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="0240a-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0240a-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0240a-120">Requirements</span></span>  
 <span data-ttu-id="0240a-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0240a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0240a-122">**Üstbilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="0240a-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0240a-123">**Kütüphane:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="0240a-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0240a-124">**.NET Çerçeve Sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="0240a-124">**.NET Framework Versions:** 3.5 SP1</span></span>
