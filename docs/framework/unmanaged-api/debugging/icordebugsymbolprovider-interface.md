---
description: ': ICorDebugSymbolProvider arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugSymbolProvider Arabirimi
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: bd47f294092ee87fc1f34bc68fe744b447e21f20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659588"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="99940-103">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99940-103">ICorDebugSymbolProvider Interface</span></span>

<span data-ttu-id="99940-104">Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="99940-104">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99940-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="99940-105">Methods</span></span>  
  
|<span data-ttu-id="99940-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="99940-106">Method</span></span>|<span data-ttu-id="99940-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99940-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99940-108">GetAssemblyImageBytes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-108">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="99940-109">Birleştirilen derlemede göreli bir sanal adres (RVA) verilen birleştirilmiş bir derlemeden verileri okur.</span><span class="sxs-lookup"><span data-stu-id="99940-109">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="99940-110">GetAssemblyImageMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-110">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="99940-111">Birleştirilmiş bir derlemeden meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="99940-111">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="99940-112">GetCodeRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-112">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="99940-113">Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="99940-113">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="99940-114">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-114">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="99940-115">TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="99940-115">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="99940-116">GetMergedAssemblyRecords Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-116">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="99940-117">Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.</span><span class="sxs-lookup"><span data-stu-id="99940-117">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="99940-118">GetMethodLocalSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-118">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="99940-119">Yöntemin yerel sembollerini, bu yöntemin göreli sanal adresi (RVA) verildiğinde alır.</span><span class="sxs-lookup"><span data-stu-id="99940-119">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="99940-120">GetMethodParameterSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-120">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="99940-121">Yöntemin parametre sembollerini, bu yöntemin göreli sanal adresi (RVA) verilen şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="99940-121">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="99940-122">GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-122">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="99940-123">Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="99940-123">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="99940-124">GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-124">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="99940-125">Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="99940-125">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="99940-126">GetStaticFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-126">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="99940-127">TypeSpec imzasına karşılık gelen statik alan sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="99940-127">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="99940-128">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99940-128">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="99940-129">Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="99940-129">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99940-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99940-130">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99940-131">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99940-131">This interface is available with .NET Native only.</span></span> <span data-ttu-id="99940-132">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="99940-132">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99940-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99940-133">Requirements</span></span>  

 <span data-ttu-id="99940-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99940-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99940-135">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="99940-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99940-136">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="99940-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99940-137">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99940-137">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99940-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99940-138">See also</span></span>

- [<span data-ttu-id="99940-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="99940-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="99940-140">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="99940-140">Debugging</span></span>](index.md)
