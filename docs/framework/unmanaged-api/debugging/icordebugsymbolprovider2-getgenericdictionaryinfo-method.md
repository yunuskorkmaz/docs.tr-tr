---
title: "ICorDebugSymbolProvider2::GetGenericDictionaryInfo yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63126e4f34ea7ea7dee7dd0b9cae0dc0fea57ed9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="1a95a-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a95a-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>
<span data-ttu-id="1a95a-103">Genel bir sözlük harita alır.</span><span class="sxs-lookup"><span data-stu-id="1a95a-103">Retrieves a generic dictionary map.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a95a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a95a-104">Syntax</span></span>  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a95a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a95a-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="1a95a-106">[out] Adresine bir işaretçi bir [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) genel sözlük eşleme içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="1a95a-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="1a95a-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1a95a-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a95a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a95a-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a95a-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a95a-109">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="1a95a-110">Harita en üst düzey iki bölümden oluşur:</span><span class="sxs-lookup"><span data-stu-id="1a95a-110">The map consists of two top-level sections:</span></span>  
  
-   <span data-ttu-id="1a95a-111">A [directory](#Directory) bu eşlemesinde dahil tüm sözlükleri, göreli sanal adresleri (RAV) içeren.</span><span class="sxs-lookup"><span data-stu-id="1a95a-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>  
  
-   <span data-ttu-id="1a95a-112">Bayt hizalı [yığın](#Heap) nesne örneğini oluşturmada bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1a95a-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="1a95a-113">Son dizin girişinin hemen sonra başlar.</span><span class="sxs-lookup"><span data-stu-id="1a95a-113">It starts immediately after the last directory entry.</span></span>  
  
<a name="Directory"></a>   
## <a name="the-directory"></a><span data-ttu-id="1a95a-114">Dizini</span><span class="sxs-lookup"><span data-stu-id="1a95a-114">The Directory</span></span>  
 <span data-ttu-id="1a95a-115">Her giriş dizininde öbek içinde uzaklığı gösterir; diğer bir deyişle, öbek başlangıç göreli bir uzaklık dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a95a-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="1a95a-116">Girişler değeri mutlaka benzersiz değil; aynı uzaklık yığınındaki işaret etmek birden çok dizin girdisi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1a95a-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>  
  
 <span data-ttu-id="1a95a-117">Genel bir sözlük harita dizin bölümü aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1a95a-117">The directory portion of the generic dictionary map has the following structure:</span></span>  
  
-   <span data-ttu-id="1a95a-118">İlk 4 bayt dictionary girişlerinin (diğer bir deyişle, göreli sanal adresleri sözlükteki sayısı) sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="1a95a-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="1a95a-119">Bu değere başvurur *N*. Yüksek bit ayarlanmışsa girişleri artan düzende göreli sanal adres göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="1a95a-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>  
  
-   <span data-ttu-id="1a95a-120">*N* dizin girişlerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="1a95a-120">The *N* directory entries follow.</span></span> <span data-ttu-id="1a95a-121">Her giriş iki 4 baytlık kesimi 8 bayt oluşur:</span><span class="sxs-lookup"><span data-stu-id="1a95a-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>  
  
    -   <span data-ttu-id="1a95a-122">Bayt 0-3: RVA; sözlüğün göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="1a95a-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>  
  
    -   <span data-ttu-id="1a95a-123">Bayt 4-7: uzaklığı; Öbek başlangıcı göre uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="1a95a-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>  
  
<a name="Heap"></a>   
## <a name="the-heap"></a><span data-ttu-id="1a95a-124">Öbek</span><span class="sxs-lookup"><span data-stu-id="1a95a-124">The Heap</span></span>  
 <span data-ttu-id="1a95a-125">Yığın 's boyutu dizin boyutu + 4 akış uzunluğu çıkarılmasıyla akış okuyucu tarafından hesaplanabilir.</span><span class="sxs-lookup"><span data-stu-id="1a95a-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="1a95a-126">Diğer bir deyişle:</span><span class="sxs-lookup"><span data-stu-id="1a95a-126">In other words:</span></span>  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 <span data-ttu-id="1a95a-127">dizin boyutu olduğu `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="1a95a-127">where the directory size is `N * 8`.</span></span>  
  
 <span data-ttu-id="1a95a-128">Her örneklemesi bilgi öğesi yığında biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="1a95a-128">The format for each instantiation information item on the heap is:</span></span>  
  
-   <span data-ttu-id="1a95a-129">Bu örnek oluşturma bilgi öğesi sıkıştırılmış ECMA meta veri biçimi bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1a95a-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="1a95a-130">Değer bu uzunluğu bilgileri dışlar.</span><span class="sxs-lookup"><span data-stu-id="1a95a-130">The value excludes this length information.</span></span>  
  
-   <span data-ttu-id="1a95a-131">Genel olgu türlerinin sayısı veya *T*, sıkıştırılmış ECMA meta veri biçiminde.</span><span class="sxs-lookup"><span data-stu-id="1a95a-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>  
  
-   <span data-ttu-id="1a95a-132">*T* türleri, her temsil ECMA türü imza biçiminde.</span><span class="sxs-lookup"><span data-stu-id="1a95a-132">*T* types, each represented in ECMA type signature format.</span></span>  
  
 <span data-ttu-id="1a95a-133">Her yığın öğesi için uzunluk eklenmesi, Basit Dizin bölümü öbek etkilemeden sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a95a-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a95a-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a95a-134">Requirements</span></span>  
 <span data-ttu-id="1a95a-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a95a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a95a-136">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a95a-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a95a-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a95a-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a95a-138">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a95a-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a95a-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a95a-139">See Also</span></span>  
 [<span data-ttu-id="1a95a-140">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a95a-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="1a95a-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1a95a-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
