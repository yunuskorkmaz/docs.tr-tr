---
description: 'Şu konuda daha fazla bilgi edinin: CLRDataCreateInstance Işlevi'
title: CLRDataCreateInstance İşlevi
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- DLLExport
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: 923b0c687d2b337eacb475973927452e3b47ad0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747263"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="1d280-103">CLRDataCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="1d280-103">CLRDataCreateInstance Function</span></span>

<span data-ttu-id="1d280-104">Belirtilen hedef öğe için bir arabirim nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1d280-104">Creates an interface object for the specified target item.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d280-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d280-105">Syntax</span></span>

```cpp
HRESULT CLRDataCreateInstance (
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d280-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d280-106">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="1d280-107">'ndaki Oluşturulacak arabirimin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1d280-107">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="1d280-108">'ndaki Arabirim nesnesinin oluşturulacağı hedef öğeyi temsil eden, Kullanıcı tarafından uygulanan [ICLRDataTarget](iclrdatatarget-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d280-108">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="1d280-109">dışı Döndürülen arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d280-109">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d280-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d280-110">Remarks</span></span>  

 <span data-ttu-id="1d280-111">`ICLRDataTarget`Nesnesi, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1d280-111">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="1d280-112">Uygulama, temsil edilen hedef öğe türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d280-112">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="1d280-113">Hedef öğe bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d280-113">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d280-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d280-114">Requirements</span></span>  

 <span data-ttu-id="1d280-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d280-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d280-116">**Üst bilgi:** ClrData. IDL</span><span class="sxs-lookup"><span data-stu-id="1d280-116">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="1d280-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1d280-117">**Library:** CorGuids.lib</span></span>  

 <span data-ttu-id="1d280-118">**Bütünleştirilmiş kod**: mscordacwks.dll, mscordbi.dll</span><span class="sxs-lookup"><span data-stu-id="1d280-118">**Assembly**: mscordacwks.dll, mscordbi.dll</span></span>
  
 <span data-ttu-id="1d280-119">**.NET Framework sürümleri:** .NET Framework 2,0 tarihinden itibaren kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="1d280-119">**.NET Framework Versions:** Available since .NET Framework 2.0</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1d280-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d280-120">See also</span></span>

- [<span data-ttu-id="1d280-121">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1d280-121">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
