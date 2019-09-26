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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d44f9b5dc42147959d3f1d127a64d39258f515
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274271"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="d22f6-102">CLRDataCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="d22f6-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="d22f6-103">Belirtilen hedef öğe için bir arabirim nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d22f6-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d22f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d22f6-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d22f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d22f6-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="d22f6-106">'ndaki Oluşturulacak arabirimin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d22f6-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="d22f6-107">'ndaki Arabirim nesnesinin oluşturulacağı hedef öğeyi temsil eden, Kullanıcı tarafından uygulanan [ICLRDataTarget](iclrdatatarget-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d22f6-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="d22f6-108">dışı Döndürülen arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d22f6-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d22f6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d22f6-109">Remarks</span></span>  
 <span data-ttu-id="d22f6-110">`ICLRDataTarget` Nesnesi, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d22f6-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="d22f6-111">Uygulama, temsil edilen hedef öğe türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d22f6-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="d22f6-112">Hedef öğe bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="d22f6-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d22f6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d22f6-113">Requirements</span></span>  
 <span data-ttu-id="d22f6-114">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d22f6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d22f6-115">**Üst bilgi** ClrData. IDL</span><span class="sxs-lookup"><span data-stu-id="d22f6-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="d22f6-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d22f6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d22f6-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d22f6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22f6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d22f6-118">See also</span></span>

- [<span data-ttu-id="d22f6-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d22f6-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
