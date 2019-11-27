---
title: IMetaDataEmit::DefineMethod Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431810"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="6c05b-102">IMetaDataEmit::DefineMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c05b-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="6c05b-103">Belirtilen imzaya sahip bir yöntem veya genel işlev için tanım oluşturur ve bu yöntem tanımına bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c05b-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c05b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c05b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="6c05b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c05b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6c05b-106">'ndaki Metodun üst sınıfının veya üst arabiriminin `mdTypedef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="6c05b-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="6c05b-107">Genel bir işlev tanımlıyorsanız `td` `mdTokenNil`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6c05b-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="6c05b-108">'ndaki Unicode 'daki üye adı.</span><span class="sxs-lookup"><span data-stu-id="6c05b-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="6c05b-109">'ndaki Metodun veya genel işlevin özniteliklerini belirten [Cormethodadttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="6c05b-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6c05b-110">'ndaki Yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="6c05b-110">[in] The method signature.</span></span> <span data-ttu-id="6c05b-111">İmza, belirtilen şekilde kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="6c05b-112">Herhangi bir parametre için ek bilgi belirtmeniz gerekiyorsa, [ımetadatayayma:: SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6c05b-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6c05b-113">'ndaki `pvSigBlob`bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="6c05b-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="6c05b-114">'ndaki Kodun adresi.</span><span class="sxs-lookup"><span data-stu-id="6c05b-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="6c05b-115">'ndaki Metodun uygulama özelliklerini belirten [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="6c05b-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="6c05b-116">dışı Üye belirteci.</span><span class="sxs-lookup"><span data-stu-id="6c05b-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c05b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c05b-117">Remarks</span></span>  
 <span data-ttu-id="6c05b-118">Meta veri API 'SI, çağıran bunları, `td` parametresinde belirtilen bir kapsayan sınıf veya arabirim için arayanla aynı sırada kalıcı hale getirme garantisi verir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="6c05b-119">`DefineMethod` ve belirli parametre ayarlarının kullanımıyla ilgili ek bilgiler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="6c05b-120">V tablosundaki yuvalar</span><span class="sxs-lookup"><span data-stu-id="6c05b-120">Slots in the V-table</span></span>  
 <span data-ttu-id="6c05b-121">Çalışma zamanı, v tablosu yuvaları ayarlamak için yöntem tanımlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c05b-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="6c05b-122">Bir veya daha fazla yuvanın bir COM arabirim düzeniyle eşlik koruması olması gibi bir veya daha fazla yuva atlanması gerektiği durumlarda, v tablosundaki yuva veya yuvaları almak için bir kukla Yöntem tanımlanmıştır; `dwMethodFlags` [Cormethodadttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırmasının `mdRTSpecialName` değerine ayarlayın ve adı şu şekilde belirtin:</span><span class="sxs-lookup"><span data-stu-id="6c05b-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="6c05b-123">_VtblGap\<*SequenceNumber*>\<\_*Countofslotlar*></span><span class="sxs-lookup"><span data-stu-id="6c05b-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="6c05b-124">Burada *SequenceNumber* , yöntemin dizi numarasıdır ve *Countofslotlar* , v tablosundaki atlanacak yuva sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="6c05b-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="6c05b-125">*Countofslotlar* atlanırsa, 1 varsayılır.</span><span class="sxs-lookup"><span data-stu-id="6c05b-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="6c05b-126">Bu kukla Yöntemler yönetilen veya yönetilmeyen koddan çağrılabilir değildir ve bunları, yönetilen veya yönetilmeyen koddan çağırma girişimleri bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c05b-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="6c05b-127">Tek amacı, çalışma zamanının COM tümleştirmesi için oluşturduğu v tablosunda yer kaplamesidir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="6c05b-128">Yinelenen Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6c05b-128">Duplicate Methods</span></span>  
 <span data-ttu-id="6c05b-129">Yinelenen yöntemleri tanımlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="6c05b-129">You should not define duplicate methods.</span></span> <span data-ttu-id="6c05b-130">Diğer bir deyişle, `td`, `wzName`ve `pvSig` parametrelerde yinelenen bir değer kümesiyle `DefineMethod` çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c05b-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="6c05b-131">(Bu üç parametre birlikte, yöntemini benzersiz bir şekilde tanımlar.).</span><span class="sxs-lookup"><span data-stu-id="6c05b-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="6c05b-132">Ancak, yöntem tanımlarından biri için `dwMethodFlags` parametresinde `mdPrivateScope` bitini ayarlamanız için yinelenen bir üçlü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c05b-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="6c05b-133">(`mdPrivateScope` bit, derleyicinin bu yöntem tanımına bir başvuru yaymayacağı anlamına gelir.)</span><span class="sxs-lookup"><span data-stu-id="6c05b-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="6c05b-134">Yöntem uygulama bilgileri</span><span class="sxs-lookup"><span data-stu-id="6c05b-134">Method Implementation Information</span></span>  
 <span data-ttu-id="6c05b-135">Yöntem uygulamasıyla ilgili bilgiler genellikle yöntemin bildirildiği sırada bilinmez.</span><span class="sxs-lookup"><span data-stu-id="6c05b-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="6c05b-136">Bu nedenle, `DefineMethod`çağırırken `ulCodeRVA` ve `dwImplFlags` parametrelere değer geçirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6c05b-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="6c05b-137">Değerler, daha sonra [ımetadatayayma:: SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) veya [ımetadatayayma:: SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)aracılığıyla uygun şekilde sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="6c05b-138">Platform çağrısı (PInvoke) veya COM birlikte çalışma senaryoları gibi bazı durumlarda, Yöntem gövdesi sağlanmaz ve `ulCodeRVA` sıfır olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c05b-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="6c05b-139">Bu durumlarda, çalışma zamanı uygulamayı bulacağından yöntem soyut olarak etiketlenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="6c05b-140">PInvoke için bir yöntem tanımlama</span><span class="sxs-lookup"><span data-stu-id="6c05b-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="6c05b-141">Her yönetilmeyen işlevin PInvoke aracılığıyla çağrılması için, hedef yönetilmeyen işlevi temsil eden bir yönetilen yöntem tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="6c05b-142">Yönetilen yöntemi tanımlamak için, PInvoke 'un kullanıldığı yönteme bağlı olarak belirli değerlere ayarlanan bazı parametrelerle `DefineMethod` kullanın:</span><span class="sxs-lookup"><span data-stu-id="6c05b-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="6c05b-143">Doğru PInvoke-yönetilmeyen bir DLL 'de bulunan harici bir yönetilmeyen yöntemin çağrılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="6c05b-144">Yerel PInvoke-geçerli yönetilen modüle eklenmiş yerel bir yönetilmeyen yöntemin çağrılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="6c05b-145">Parametre ayarları aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c05b-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="6c05b-146">Parametre</span><span class="sxs-lookup"><span data-stu-id="6c05b-146">Parameter</span></span>|<span data-ttu-id="6c05b-147">Doğru PInvoke için değerler</span><span class="sxs-lookup"><span data-stu-id="6c05b-147">Values for true PInvoke</span></span>|<span data-ttu-id="6c05b-148">Yerel PInvoke için değerler</span><span class="sxs-lookup"><span data-stu-id="6c05b-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="6c05b-149">`mdStatic`ayarla; `mdSynchronized` ve `mdAbstract`temizleyin.</span><span class="sxs-lookup"><span data-stu-id="6c05b-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="6c05b-150">Geçerli yönetilen türler içeren parametrelere sahip geçerli bir ortak dil çalışma zamanı (CLR) yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="6c05b-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="6c05b-151">Geçerli yönetilen türler içeren parametrelere sahip geçerli bir CLR yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="6c05b-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="6c05b-152">0</span><span class="sxs-lookup"><span data-stu-id="6c05b-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="6c05b-153">`miCil` ve `miManaged`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6c05b-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="6c05b-154">`miNative` ve `miUnmanaged`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6c05b-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c05b-155">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c05b-155">Requirements</span></span>  
 <span data-ttu-id="6c05b-156">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c05b-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c05b-157">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6c05b-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c05b-158">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6c05b-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c05b-159">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c05b-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c05b-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c05b-160">See also</span></span>

- [<span data-ttu-id="6c05b-161">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c05b-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6c05b-162">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c05b-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
