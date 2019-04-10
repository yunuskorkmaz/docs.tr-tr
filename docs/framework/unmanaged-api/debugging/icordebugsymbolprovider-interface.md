---
title: ICorDebugSymbolProvider Arabirimi
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc33018f68f9634a29e2f5c52123a0215b446de7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228971"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="1a5f6-102">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="1a5f6-103">Hata ayıklama bilgilerini almak için kullanılan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a5f6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1a5f6-104">Methods</span></span>  
  
|<span data-ttu-id="1a5f6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1a5f6-105">Method</span></span>|<span data-ttu-id="1a5f6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a5f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a5f6-107">GetAssemblyImageBytes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-107">GetAssemblyImageBytes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="1a5f6-108">Birleştirilmiş derlemeye göreli sanal adres (RVA) verilen birleştirilmiş bir bütünleştirilmiş koddan verileri okur.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="1a5f6-109">GetAssemblyImageMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-109">GetAssemblyImageMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="1a5f6-110">Birleştirilmiş bir derlemesinden meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="1a5f6-111">GetCodeRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-111">GetCodeRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="1a5f6-112">Yöntemi başlangıç adresi ve bir yöntemde göreli sanal adres (RVA) verilen boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="1a5f6-113">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-113">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="1a5f6-114">Örnek TypeSpec'te imza karşılık gelen alan simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="1a5f6-115">GetMergedAssemblyRecords Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-115">GetMergedAssemblyRecords Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="1a5f6-116">Birleştirilmiş tüm derlemeler için Sembol kayıtları alır.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="1a5f6-117">GetMethodLocalSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-117">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="1a5f6-118">Bu yöntemin göreli sanal adres (RVA) verilen bir yöntemin yerel simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="1a5f6-119">GetMethodParameterSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-119">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="1a5f6-120">Bu yöntemin göreli sanal adres (RVA) verilen bir yöntemin parametre simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="1a5f6-121">GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="1a5f6-122">Bu yönteme göreli sanal adres (RVA) verilen yöntemin meta veri belirteci ve kendi genel parametreler hakkında bilgi gibi yöntemi özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="1a5f6-123">GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-123">GetObjectSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="1a5f6-124">Kendi TypeSpec'te imzasına bağlı bir nesne için nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="1a5f6-125">GetStaticFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-125">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="1a5f6-126">TypeSpec'te imza karşılık gelen statik alan simgelerini alır.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="1a5f6-127">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a5f6-127">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="1a5f6-128">Göreli sanal adres (RVA) içinde bir vtable verilen imza, genel parametrelerinin sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a5f6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a5f6-129">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a5f6-130">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1a5f6-131">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a5f6-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a5f6-132">Requirements</span></span>  
 <span data-ttu-id="1a5f6-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a5f6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a5f6-134">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a5f6-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a5f6-135">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a5f6-135">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1a5f6-136">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1a5f6-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a5f6-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a5f6-137">See also</span></span>

- [<span data-ttu-id="1a5f6-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1a5f6-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1a5f6-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1a5f6-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
