---
title: ICorDebugSymbolProvider Arabirimi
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa30391f10a5f9540090e90500c1cb0a9a410b1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955527"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="8b66e-102">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b66e-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="8b66e-103">Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b66e-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b66e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8b66e-104">Methods</span></span>  
  
|<span data-ttu-id="8b66e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8b66e-105">Method</span></span>|<span data-ttu-id="8b66e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b66e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b66e-107">GetAssemblyImageBytes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-107">GetAssemblyImageBytes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="8b66e-108">Birleştirilen derlemede göreli bir sanal adres (RVA) verilen birleştirilmiş bir derlemeden verileri okur.</span><span class="sxs-lookup"><span data-stu-id="8b66e-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="8b66e-109">GetAssemblyImageMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-109">GetAssemblyImageMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="8b66e-110">Birleştirilmiş bir derlemeden meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b66e-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="8b66e-111">GetCodeRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-111">GetCodeRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="8b66e-112">Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="8b66e-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="8b66e-113">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-113">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="8b66e-114">TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="8b66e-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="8b66e-115">GetMergedAssemblyRecords Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-115">GetMergedAssemblyRecords Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="8b66e-116">Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.</span><span class="sxs-lookup"><span data-stu-id="8b66e-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="8b66e-117">GetMethodLocalSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-117">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="8b66e-118">Yöntemin yerel sembollerini, bu yöntemin göreli sanal adresi (RVA) verildiğinde alır.</span><span class="sxs-lookup"><span data-stu-id="8b66e-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="8b66e-119">GetMethodParameterSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-119">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="8b66e-120">Yöntemin parametre sembollerini, bu yöntemin göreli sanal adresi (RVA) verilen şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="8b66e-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="8b66e-121">GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="8b66e-122">Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b66e-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="8b66e-123">GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-123">GetObjectSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="8b66e-124">Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b66e-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="8b66e-125">GetStaticFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-125">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="8b66e-126">TypeSpec imzasına karşılık gelen statik alan sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="8b66e-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="8b66e-127">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b66e-127">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="8b66e-128">Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b66e-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b66e-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b66e-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b66e-130">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b66e-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8b66e-131">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="8b66e-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b66e-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b66e-132">Requirements</span></span>  
 <span data-ttu-id="8b66e-133">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b66e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b66e-134">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8b66e-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b66e-135">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8b66e-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b66e-136">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b66e-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b66e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b66e-137">See also</span></span>

- [<span data-ttu-id="8b66e-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b66e-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8b66e-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8b66e-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
