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
ms.openlocfilehash: 340d2de09562ea9b767203a7fa839cdc6b729b3b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860896"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="83349-102">CreateCordbObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="83349-102">CreateCordbObject Function</span></span>
<span data-ttu-id="83349-103">Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi ([ICorDebug](icordebug-interface.md)) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83349-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83349-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83349-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83349-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83349-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="83349-106">'ndaki Hedef işlemin hata ayıklayıcı sürümü.</span><span class="sxs-lookup"><span data-stu-id="83349-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="83349-107">Bu parametre, uzaktan hata ayıklama için CorDebugVersion_2_0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83349-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="83349-108">dışı [ICorDebug](icordebug-interface.md) arabirimine verilecek ve döndürülen bir nesne işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="83349-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83349-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="83349-109">Return Value</span></span>  
 <span data-ttu-id="83349-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83349-110">S_OK</span></span>  
 <span data-ttu-id="83349-111">İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="83349-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="83349-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="83349-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="83349-113">`ppCordb`null veya `iDebuggerVersion` CorDebugVersion_2_0 değil.</span><span class="sxs-lookup"><span data-stu-id="83349-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="83349-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="83349-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="83349-115">İçin yeterli bellek ayrılamıyor`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="83349-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="83349-116">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="83349-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="83349-117">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="83349-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83349-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83349-118">Remarks</span></span>  
 <span data-ttu-id="83349-119">' De `ppCordb` döndürülen [ICorDebug](icordebug-interface.md) arabirimi, tüm yönetilen hata ayıklama Hizmetleri için en üst düzey hata ayıklama arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="83349-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83349-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83349-120">Requirements</span></span>  
 <span data-ttu-id="83349-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83349-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83349-122">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="83349-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="83349-123">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="83349-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="83349-124">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="83349-124">**.NET Framework Versions:** 3.5 SP1</span></span>
