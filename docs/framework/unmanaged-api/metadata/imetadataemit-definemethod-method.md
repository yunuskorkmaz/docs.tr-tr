---
title: "IMetaDataEmit::DefineMethod Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMethod
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de55ee714dcba512befae3d2311a9880a08ba29f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="314aa-102">IMetaDataEmit::DefineMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="314aa-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="314aa-103">Belirtilen imzayla yöntemi veya genel işlevi için bir tanım oluşturur ve bu yöntem tanımı için bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="314aa-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="314aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="314aa-104">Syntax</span></span>  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="314aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="314aa-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="314aa-106">[in] `mdTypedef` Üst sınıf veya yöntemin üst arabirimi belirteci.</span><span class="sxs-lookup"><span data-stu-id="314aa-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="314aa-107">Ayarlama `td` için `mdTokenNil`, genel bir işlev tanımlıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="314aa-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="314aa-108">[in] Unicode üye adı.</span><span class="sxs-lookup"><span data-stu-id="314aa-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="314aa-109">[in] Değerini [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) yöntemi veya genel işlev özniteliklerini belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="314aa-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="314aa-110">[in] Yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="314aa-110">[in] The method signature.</span></span> <span data-ttu-id="314aa-111">İmza verdiği kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="314aa-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="314aa-112">Ek bilgi için herhangi bir parametre belirtmeniz gerekiyorsa, kullanın [Imetadataemit::setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="314aa-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="314aa-113">[in] Bayt sayısı `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="314aa-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="314aa-114">[in] Kod adresi.</span><span class="sxs-lookup"><span data-stu-id="314aa-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="314aa-115">[in] Değerini [Cormethodımpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) yöntemi uygulama özelliklerini belirten numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="314aa-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="314aa-116">[out] Üye belirteci.</span><span class="sxs-lookup"><span data-stu-id="314aa-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="314aa-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="314aa-117">Remarks</span></span>  
 <span data-ttu-id="314aa-118">Arayan bunları verilen kapsayan sınıf veya belirtilen arabirimi için gösterdiği gibi yöntemleri aynı sırayla kalıcı hale getirmek API meta verileri garanti `td` parametresi.</span><span class="sxs-lookup"><span data-stu-id="314aa-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="314aa-119">Kullanımı ile ilgili ek bilgiler `DefineMethod` ve belirli parametre ayarları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="314aa-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="314aa-120">V tablosundaki yuvaları</span><span class="sxs-lookup"><span data-stu-id="314aa-120">Slots in the V-table</span></span>  
 <span data-ttu-id="314aa-121">Çalışma zamanı yöntemi tanımları v tablo yuvaları ayarlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="314aa-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="314aa-122">Burada bir veya daha fazla yuvaları Atlanan, bu tür gerekecektir durumda bir COM arabirimi Düzen eşlikli korumak için bir kukla yöntemi yuvası ya da v tablosundaki yuvası kaplayan için tanımlanmış bir; ayarlama `dwMethodFlags` için `mdRTSpecialName` değerini [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırma ve farklı bir ad belirtin:</span><span class="sxs-lookup"><span data-stu-id="314aa-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="314aa-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="314aa-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>  
  
 <span data-ttu-id="314aa-124">Burada *SequenceNumber* yöntemi sıra sayısı ve *CountOfSlots* v tabloda atlamak için yuva sayısı.</span><span class="sxs-lookup"><span data-stu-id="314aa-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="314aa-125">Varsa *CountOfSlots* olan atlanırsa, 1 varsayılır.</span><span class="sxs-lookup"><span data-stu-id="314aa-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="314aa-126">Bu kukla yöntemleri yönetilen veya yönetilmeyen koddan aranabilir değildir ve bunları yönetilen veya yönetilmeyen koddan çağırma girişimi herhangi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="314aa-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="314aa-127">COM tümleştirme için çalışma zamanı oluşturur v tablo yer yalnızca amaçlarına gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="314aa-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="314aa-128">Yinelenen yöntemleri</span><span class="sxs-lookup"><span data-stu-id="314aa-128">Duplicate Methods</span></span>  
 <span data-ttu-id="314aa-129">Yinelenen yöntemleri tanımlamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="314aa-129">You should not define duplicate methods.</span></span> <span data-ttu-id="314aa-130">Diğer bir deyişle, değil çağırmalısınız `DefineMethod` yinelenen değerler kümesiyle `td`, `wzName`, ve `pvSig` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="314aa-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="314aa-131">(Şu üç parametreyi birlikte benzersiz olarak yöntemi tanımlayın.).</span><span class="sxs-lookup"><span data-stu-id="314aa-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="314aa-132">Ancak, yöntem tanımlarını biri için ayarladığınız olması koşuluyla, yinelenen Üçlü kullanabilirsiniz `mdPrivateScope` içinde bit `dwMethodFlags` parametresi.</span><span class="sxs-lookup"><span data-stu-id="314aa-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="314aa-133">( `mdPrivateScope` Bit anlamına gelir derleyici bu yöntem tanımını başvuru yayma değil.)</span><span class="sxs-lookup"><span data-stu-id="314aa-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="314aa-134">Yöntemi uygulama bilgileri</span><span class="sxs-lookup"><span data-stu-id="314aa-134">Method Implementation Information</span></span>  
 <span data-ttu-id="314aa-135">Yöntem uygulaması hakkında bilgi yöntemi bildirilmiş aynı anda bilinmiyor genellikle.</span><span class="sxs-lookup"><span data-stu-id="314aa-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="314aa-136">Bu nedenle, değerleri geçirmek gerekmez `ulCodeRVA` ve `dwImplFlags` çağrılırken parametreleri `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="314aa-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="314aa-137">Değerleri daha sonra aracılığıyla sağlanabilir [Imetadataemit::setmethodımplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) veya [Imetadataemit::setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="314aa-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="314aa-138">Platform çağırma (PInvoke) veya COM birlikte çalışma senaryoları gibi bazı durumlarda, yöntem gövdesi sunulacaktır değil, ve `ulCodeRVA` sıfır olarak ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="314aa-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="314aa-139">Çalışma zamanı uygulama bulur çünkü bu gibi durumlarda yöntemi soyut olarak etiketlenmesi gerektiğine değil.</span><span class="sxs-lookup"><span data-stu-id="314aa-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="314aa-140">PInvoke için bir yöntem tanımlama</span><span class="sxs-lookup"><span data-stu-id="314aa-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="314aa-141">Yönetilmeyen her işlev PInvoke aracılığıyla çağrılacak bilgi için yönetilmeyen hedef işlevi temsil eden bir yönetilen yöntemi tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="314aa-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="314aa-142">Yönetilen yöntemi tanımlamak için `DefineMethod` bazı PInvoke kullanılır şekilde bağlı olarak belirli değerler için ayarlanan parametreler:</span><span class="sxs-lookup"><span data-stu-id="314aa-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
-   <span data-ttu-id="314aa-143">TRUE PInvoke - yönetilmeyen DLL içinde bulunduğu bir dış yönetilmeyen yöntemi çağrıldı içerir.</span><span class="sxs-lookup"><span data-stu-id="314aa-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
-   <span data-ttu-id="314aa-144">Yerel PInvoke - geçerli yönetilen modül katıştırılmış yerel bir yönetilmeyen yöntemi çağrıldı içerir.</span><span class="sxs-lookup"><span data-stu-id="314aa-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="314aa-145">Parametre ayarları aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="314aa-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="314aa-146">Parametre</span><span class="sxs-lookup"><span data-stu-id="314aa-146">Parameter</span></span>|<span data-ttu-id="314aa-147">Doğru PInvoke değerleri</span><span class="sxs-lookup"><span data-stu-id="314aa-147">Values for true PInvoke</span></span>|<span data-ttu-id="314aa-148">Yerel PInvoke değerleri</span><span class="sxs-lookup"><span data-stu-id="314aa-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="314aa-149">Ayarlama `mdStatic`; clear `mdSynchronized` ve `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="314aa-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="314aa-150">Yönetilen türler geçerli bir ortak dil çalışma zamanı (CLR) yöntemi imzası geçerli parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="314aa-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="314aa-151">Yönetilen türler geçerli parametrelere sahip geçerli bir CLR yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="314aa-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="314aa-152">0</span><span class="sxs-lookup"><span data-stu-id="314aa-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="314aa-153">Ayarlama `miCil` ve `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="314aa-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="314aa-154">Ayarlama `miNative` ve `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="314aa-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="314aa-155">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="314aa-155">Requirements</span></span>  
 <span data-ttu-id="314aa-156">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="314aa-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="314aa-157">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="314aa-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="314aa-158">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="314aa-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="314aa-159">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="314aa-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314aa-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="314aa-160">See Also</span></span>  
 [<span data-ttu-id="314aa-161">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="314aa-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="314aa-162">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="314aa-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
