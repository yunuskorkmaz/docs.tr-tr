---
description: 'Daha fazla bilgi edinin: CreateCordbObject Işlevi'
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
ms.openlocfilehash: b6a585fc89f780b22f842127e1923414dbb8230f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801481"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="06734-103">CreateCordbObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="06734-103">CreateCordbObject Function</span></span>

<span data-ttu-id="06734-104">Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi ([ICorDebug](icordebug-interface.md)) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06734-104">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06734-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06734-105">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06734-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06734-106">Parameters</span></span>  

 `iDebuggerVersion`  
 <span data-ttu-id="06734-107">'ndaki Hedef işlemin hata ayıklayıcı sürümü.</span><span class="sxs-lookup"><span data-stu-id="06734-107">[in] Debugger version of the target process.</span></span> <span data-ttu-id="06734-108">Bu parametre, uzaktan hata ayıklama için CorDebugVersion_2_0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06734-108">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="06734-109">dışı [ICorDebug](icordebug-interface.md) arabirimine verilecek ve döndürülen bir nesne işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="06734-109">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06734-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06734-110">Return Value</span></span>  

 <span data-ttu-id="06734-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="06734-111">S_OK</span></span>  
 <span data-ttu-id="06734-112">İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.</span><span class="sxs-lookup"><span data-stu-id="06734-112">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="06734-113">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="06734-113">E_INVALIDARG</span></span>  
 <span data-ttu-id="06734-114">`ppCordb` null veya `iDebuggerVersion` CorDebugVersion_2_0 değil.</span><span class="sxs-lookup"><span data-stu-id="06734-114">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="06734-115">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="06734-115">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="06734-116">İçin yeterli bellek ayrılamıyor `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="06734-116">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="06734-117">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="06734-117">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="06734-118">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="06734-118">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06734-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06734-119">Remarks</span></span>  

 <span data-ttu-id="06734-120">' De döndürülen [ICorDebug](icordebug-interface.md) arabirimi, `ppCordb` tüm yönetilen hata ayıklama Hizmetleri için en üst düzey hata ayıklama arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="06734-120">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06734-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06734-121">Requirements</span></span>  

 <span data-ttu-id="06734-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06734-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06734-123">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="06734-123">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="06734-124">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="06734-124">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="06734-125">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="06734-125">**.NET Framework Versions:** 3.5 SP1</span></span>
