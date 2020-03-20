---
title: CLRDataCreateInstance İşlevi
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179357"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="1a819-102">CLRDataCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="1a819-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="1a819-103">Belirtilen hedef öğe için bir arabirim nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1a819-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a819-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a819-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a819-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a819-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="1a819-106">[içinde] Arabirimin tanımlayıcısı anında alınacak.</span><span class="sxs-lookup"><span data-stu-id="1a819-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="1a819-107">[içinde] Arabirim nesnesini oluşturmak için hedef öğeyi temsil eden kullanıcı tarafından uygulanan [ICLRDataTarget](iclrdatatarget-interface.md) nesnesine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a819-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="1a819-108">[çıkış] Döndürülen arabirim nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a819-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a819-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a819-109">Remarks</span></span>  
 <span data-ttu-id="1a819-110">Nesne `ICLRDataTarget` hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1a819-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="1a819-111">Uygulama, temsil edilen hedef öğenin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1a819-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="1a819-112">Hedef öğe bir işlem, bellek dökümü, uzak makine ve benzeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a819-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a819-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a819-113">Requirements</span></span>  
 <span data-ttu-id="1a819-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a819-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a819-115">**Üstbilgi:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="1a819-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="1a819-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a819-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a819-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a819-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a819-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a819-118">See also</span></span>

- [<span data-ttu-id="1a819-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1a819-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
