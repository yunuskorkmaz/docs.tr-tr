---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineMethod yöntemi'
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
ms.openlocfilehash: b0ba2bb68f1d4387229767f6f2550d64b9008898
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677972"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="c7045-103">IMetaDataEmit::DefineMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7045-103">IMetaDataEmit::DefineMethod Method</span></span>

<span data-ttu-id="c7045-104">Belirtilen imzaya sahip bir yöntem veya genel işlev için tanım oluşturur ve bu yöntem tanımına bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7045-104">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7045-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7045-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c7045-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7045-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="c7045-107">'ndaki `mdTypedef` Metodun üst sınıfının veya üst arabiriminin belirteci.</span><span class="sxs-lookup"><span data-stu-id="c7045-107">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="c7045-108">`td` `mdTokenNil` Genel bir işlev tanımlıyorsanız, olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c7045-108">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="c7045-109">'ndaki Unicode 'daki üye adı.</span><span class="sxs-lookup"><span data-stu-id="c7045-109">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="c7045-110">'ndaki Metodun veya genel işlevin özniteliklerini belirten [Cormethodadttr](cormethodattr-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="c7045-110">[in] A value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c7045-111">'ndaki Yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="c7045-111">[in] The method signature.</span></span> <span data-ttu-id="c7045-112">İmza, belirtilen şekilde kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="c7045-112">The signature is persisted as supplied.</span></span> <span data-ttu-id="c7045-113">Herhangi bir parametre için ek bilgi belirtmeniz gerekiyorsa, [ımetadatayayma:: SetParamProps](imetadataemit-setparamprops-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7045-113">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c7045-114">'ndaki İçindeki bayt sayısı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="c7045-114">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="c7045-115">'ndaki Kodun adresi.</span><span class="sxs-lookup"><span data-stu-id="c7045-115">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="c7045-116">'ndaki Metodun uygulama özelliklerini belirten [CorMethodImpl](cormethodimpl-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="c7045-116">[in] A value of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="c7045-117">dışı Üye belirteci.</span><span class="sxs-lookup"><span data-stu-id="c7045-117">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7045-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7045-118">Remarks</span></span>  

 <span data-ttu-id="c7045-119">Meta veri API 'SI, bu yöntemleri, bu parametre içinde belirtilen bir kapsayan sınıf veya arabirim için arayanla aynı sırada kalıcı hale getirme garantisi verir `td` .</span><span class="sxs-lookup"><span data-stu-id="c7045-119">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="c7045-120">`DefineMethod`Ve belirli parametre ayarlarının kullanımıyla ilgili ek bilgiler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7045-120">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="c7045-121">V tablosundaki yuvalar</span><span class="sxs-lookup"><span data-stu-id="c7045-121">Slots in the V-table</span></span>  

 <span data-ttu-id="c7045-122">Çalışma zamanı, v tablosu yuvaları ayarlamak için yöntem tanımlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7045-122">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="c7045-123">Bir veya daha fazla yuvanın bir COM arabirim düzeniyle eşlik koruması olması gibi bir veya daha fazla yuva atlanması gerektiği durumlarda, v tablosundaki yuva veya yuvaları almak için bir kukla Yöntem tanımlanmıştır; öğesini `dwMethodFlags` `mdRTSpecialName` [Cormethodadttr](cormethodattr-enumeration.md) numaralandırmasının değerine ayarlayın ve adı şu şekilde belirtin:</span><span class="sxs-lookup"><span data-stu-id="c7045-123">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="c7045-124">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="c7045-124">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="c7045-125">Burada *SequenceNumber* , yöntemin dizi numarasıdır ve *Countofslotlar* , v tablosundaki atlanacak yuva sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="c7045-125">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="c7045-126">*Countofslotlar* atlanırsa, 1 varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c7045-126">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="c7045-127">Bu kukla Yöntemler yönetilen veya yönetilmeyen koddan çağrılabilir değildir ve bunları, yönetilen veya yönetilmeyen koddan çağırma girişimleri bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7045-127">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="c7045-128">Tek amacı, çalışma zamanının COM tümleştirmesi için oluşturduğu v tablosunda yer kaplamesidir.</span><span class="sxs-lookup"><span data-stu-id="c7045-128">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="c7045-129">Yinelenen Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c7045-129">Duplicate Methods</span></span>  

 <span data-ttu-id="c7045-130">Yinelenen yöntemleri tanımlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="c7045-130">You should not define duplicate methods.</span></span> <span data-ttu-id="c7045-131">Diğer bir deyişle,, `DefineMethod` ve parametrelerinde yinelenen bir değer kümesiyle çağırmamalıdır `td` `wzName` `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="c7045-131">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="c7045-132">(Bu üç parametre birlikte, yöntemini benzersiz bir şekilde tanımlar.).</span><span class="sxs-lookup"><span data-stu-id="c7045-132">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="c7045-133">Ancak, yöntem tanımlarından biri için `mdPrivateScope` parametreyi parametre içinde ayarlayabilmeniz için yinelenen bir üçlü kullanabilirsiniz `dwMethodFlags` .</span><span class="sxs-lookup"><span data-stu-id="c7045-133">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="c7045-134">( `mdPrivateScope` Bit, derleyicinin bu yöntem tanımına bir başvuru yaymayacağı anlamına gelir.)</span><span class="sxs-lookup"><span data-stu-id="c7045-134">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="c7045-135">Yöntem uygulama bilgileri</span><span class="sxs-lookup"><span data-stu-id="c7045-135">Method Implementation Information</span></span>  

 <span data-ttu-id="c7045-136">Yöntem uygulamasıyla ilgili bilgiler genellikle yöntemin bildirildiği sırada bilinmez.</span><span class="sxs-lookup"><span data-stu-id="c7045-136">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="c7045-137">Bu nedenle, `ulCodeRVA` çağırma sırasında ve parametrelerinde değerleri geçirmeniz gerekmez `dwImplFlags` `DefineMethod` .</span><span class="sxs-lookup"><span data-stu-id="c7045-137">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="c7045-138">Değerler, daha sonra [ımetadatayayma:: SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) veya [ımetadatayayma:: SetRVA](imetadataemit-setrva-method.md)aracılığıyla uygun şekilde sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7045-138">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="c7045-139">Platform çağrısı (PInvoke) veya COM birlikte çalışma senaryoları gibi bazı durumlarda, Yöntem gövdesi sağlanmaz ve `ulCodeRVA` sıfıra ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7045-139">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="c7045-140">Bu durumlarda, çalışma zamanı uygulamayı bulacağından yöntem soyut olarak etiketlenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="c7045-140">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="c7045-141">PInvoke için bir yöntem tanımlama</span><span class="sxs-lookup"><span data-stu-id="c7045-141">Defining a Method for PInvoke</span></span>  

 <span data-ttu-id="c7045-142">Her yönetilmeyen işlevin PInvoke aracılığıyla çağrılması için, hedef yönetilmeyen işlevi temsil eden bir yönetilen yöntem tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7045-142">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="c7045-143">Yönetilen yöntemi tanımlamak için, `DefineMethod` PInvoke 'un kullanıldığı yönteme bağlı olarak belirli değerlere ayarlanmış parametrelerden bazıları ile kullanın:</span><span class="sxs-lookup"><span data-stu-id="c7045-143">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="c7045-144">Doğru PInvoke-yönetilmeyen bir DLL 'de bulunan harici bir yönetilmeyen yöntemin çağrılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="c7045-144">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="c7045-145">Yerel PInvoke-geçerli yönetilen modüle eklenmiş yerel bir yönetilmeyen yöntemin çağrılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="c7045-145">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="c7045-146">Parametre ayarları aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7045-146">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="c7045-147">Parametre</span><span class="sxs-lookup"><span data-stu-id="c7045-147">Parameter</span></span>|<span data-ttu-id="c7045-148">Doğru PInvoke için değerler</span><span class="sxs-lookup"><span data-stu-id="c7045-148">Values for true PInvoke</span></span>|<span data-ttu-id="c7045-149">Yerel PInvoke için değerler</span><span class="sxs-lookup"><span data-stu-id="c7045-149">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="c7045-150">Ayarla `mdStatic` ; clear `mdSynchronized` ve `mdAbstract` .</span><span class="sxs-lookup"><span data-stu-id="c7045-150">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="c7045-151">Geçerli yönetilen türler içeren parametrelere sahip geçerli bir ortak dil çalışma zamanı (CLR) yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="c7045-151">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="c7045-152">Geçerli yönetilen türler içeren parametrelere sahip geçerli bir CLR yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="c7045-152">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="c7045-153">0</span><span class="sxs-lookup"><span data-stu-id="c7045-153">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="c7045-154">`miCil`Ve ayarlayın `miManaged` .</span><span class="sxs-lookup"><span data-stu-id="c7045-154">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="c7045-155">`miNative`Ve ayarlayın `miUnmanaged` .</span><span class="sxs-lookup"><span data-stu-id="c7045-155">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7045-156">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7045-156">Requirements</span></span>  

 <span data-ttu-id="c7045-157">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7045-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7045-158">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c7045-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7045-159">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c7045-159">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7045-160">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7045-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7045-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7045-161">See also</span></span>

- [<span data-ttu-id="c7045-162">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7045-162">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c7045-163">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7045-163">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
