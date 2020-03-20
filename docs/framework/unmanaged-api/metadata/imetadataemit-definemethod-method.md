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
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177676"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="8c3ec-102">IMetaDataEmit::DefineMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c3ec-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="8c3ec-103">Belirtilen imzaile bir yöntem veya global işlev için bir tanım oluşturur ve bu yöntem tanımına bir belirteç döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c3ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c3ec-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8c3ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c3ec-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8c3ec-106">[içinde] Yöntemin `mdTypedef` üst sınıf veya üst arabiriminin belirteci.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="8c3ec-107">`td` Genel `mdTokenNil`bir işlev tanımlıyorsanız,</span><span class="sxs-lookup"><span data-stu-id="8c3ec-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="8c3ec-108">[içinde] Unicode'daki üye adı.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="8c3ec-109">[içinde] Yöntemin veya genel işlevin özniteliklerini belirten [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8c3ec-110">[içinde] Yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-110">[in] The method signature.</span></span> <span data-ttu-id="8c3ec-111">İmza verilen şekilde devam etti.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="8c3ec-112">Herhangi bir parametre için ek bilgi belirtmeniz gerekiyorsa, [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8c3ec-113">[içinde] Bayt `pvSigBlob`sayısı.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="8c3ec-114">[içinde] Kodun adresi.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="8c3ec-115">[içinde] Yöntemin uygulama özelliklerini belirten [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) numaralandırmadeğeri.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="8c3ec-116">[çıkış] Üye belirteci.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c3ec-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c3ec-117">Remarks</span></span>  
 <span data-ttu-id="8c3ec-118">Meta veri API' si, yöntemleri arayanın `td` parametrede belirtilen belirli bir çevreleyen sınıf veya arabirim için yayıdığı sırada devam etmesini garanti eder.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="8c3ec-119">Kullanımı `DefineMethod` ve belirli parametre ayarları ile ilgili ek bilgiler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="8c3ec-120">V tablosundaki yuvalar</span><span class="sxs-lookup"><span data-stu-id="8c3ec-120">Slots in the V-table</span></span>  
 <span data-ttu-id="8c3ec-121">Çalışma zamanı, v-table yuvalarını ayarlamak için yöntem tanımlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="8c3ec-122">Com arabirim düzeniyle pariteyi korumak gibi bir veya daha fazla yuvanın atlanmaları gerektiğinde, v-tablosundaki yuva veya yuvaları almak için sahte bir yöntem tanımlanır; CorMethodAttr numaralandırma değerini ayarlayın ve adını şu şekilde belirtin: [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) `dwMethodFlags` `mdRTSpecialName`</span><span class="sxs-lookup"><span data-stu-id="8c3ec-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="8c3ec-123">_VtblGap\<*DizisiSayı*>\<\_*Sayısı*></span><span class="sxs-lookup"><span data-stu-id="8c3ec-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="8c3ec-124">*SequenceNumber* yöntemin sıra numarası ve *CountOfSlots* v-tablosunda atlamak için yuva sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="8c3ec-125">*CountOfSlots* atlanırsa, 1 kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="8c3ec-126">Bu sahte yöntemler yönetilen veya yönetilmeyen koddan çağrılabilir değildir ve yönetilen veya yönetilmeyen koddan bunları çağırma girişimi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="8c3ec-127">Tek amaçları, çalışma zamanının COM tümleştirmesi için oluşturduğu v tablosunda yer açmaktır.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="8c3ec-128">Yinelenen Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8c3ec-128">Duplicate Methods</span></span>  
 <span data-ttu-id="8c3ec-129">Yinelenen yöntemleri tanımlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-129">You should not define duplicate methods.</span></span> <span data-ttu-id="8c3ec-130">Diğer bir deyişle, `DefineMethod` `td`, ve `wzName` `pvSig` parametreleri değerleri yinelenen bir dizi ile aramamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="8c3ec-131">(Bu üç parametre birlikte benzersiz yöntemi tanımlar.).</span><span class="sxs-lookup"><span data-stu-id="8c3ec-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="8c3ec-132">Ancak, yöntem tanımlarından biri için `mdPrivateScope` `dwMethodFlags` parametredeki biti ayarlamanız koşuluyla yinelenen üçlü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="8c3ec-133">(Bit, `mdPrivateScope` derleyicinin bu yöntem tanımına bir başvuru yayılmayacağı anlamına gelir.)</span><span class="sxs-lookup"><span data-stu-id="8c3ec-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="8c3ec-134">Yöntem Uygulama Bilgileri</span><span class="sxs-lookup"><span data-stu-id="8c3ec-134">Method Implementation Information</span></span>  
 <span data-ttu-id="8c3ec-135">Yöntem in ekinde yöntem uygulaması hakkında bilgiler genellikle bilinmemektedir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="8c3ec-136">Bu nedenle, ararken `ulCodeRVA` `dwImplFlags` `DefineMethod`değerleri ve parametreleri geçmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="8c3ec-137">Değerler daha sonra [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) veya [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), uygun şekilde sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="8c3ec-138">Platform çağırma (PInvoke) veya COM interop senaryoları gibi bazı durumlarda, yöntem gövdesi `ulCodeRVA` sağlanmaz ve sıfıra ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="8c3ec-139">Çalışma zamanı uygulamayı bulacağı için, bu gibi durumlarda yöntem soyut olarak etiketlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="8c3ec-140">PInvoke için Bir Yöntem Tanımlama</span><span class="sxs-lookup"><span data-stu-id="8c3ec-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="8c3ec-141">Yönetilmeyen her işlevin PInvoke aracılığıyla çağrılabilmesi için, hedef yönetilmeyen işlevi temsil eden yönetilen bir yöntem tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="8c3ec-142">Yönetilen yöntemi tanımlamak için, PInvoke'in nasıl kullanıldığına bağlı olarak belirli değerlere ayarlanmış bazı parametreleri kullanın: `DefineMethod`</span><span class="sxs-lookup"><span data-stu-id="8c3ec-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="8c3ec-143">True PInvoke - yönetilmeyen bir DLL'de bulunan harici yönetilmeyen bir yöntemin çağrılması içerir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="8c3ec-144">Yerel PInvoke - geçerli yönetilen modüle katıştırılmış yerel bir yönetilmeyen yöntem invocation içerir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="8c3ec-145">Parametre ayarları aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="8c3ec-146">Parametre</span><span class="sxs-lookup"><span data-stu-id="8c3ec-146">Parameter</span></span>|<span data-ttu-id="8c3ec-147">Gerçek PInvoke değerleri</span><span class="sxs-lookup"><span data-stu-id="8c3ec-147">Values for true PInvoke</span></span>|<span data-ttu-id="8c3ec-148">Yerel PInvoke değerleri</span><span class="sxs-lookup"><span data-stu-id="8c3ec-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="8c3ec-149">Set `mdStatic`; açık `mdSynchronized` `mdAbstract`ve .</span><span class="sxs-lookup"><span data-stu-id="8c3ec-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="8c3ec-150">Geçerli yönetilen türleri parametreleri ile geçerli bir ortak dil çalışma zamanı (CLR) yöntemi imza.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="8c3ec-151">Geçerli yönetilen türleri parametreleri ile geçerli bir CLR yöntemi imza.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="8c3ec-152">0</span><span class="sxs-lookup"><span data-stu-id="8c3ec-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="8c3ec-153">Ayarlayın `miCil` `miManaged`ve .</span><span class="sxs-lookup"><span data-stu-id="8c3ec-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="8c3ec-154">Ayarlayın `miNative` `miUnmanaged`ve .</span><span class="sxs-lookup"><span data-stu-id="8c3ec-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c3ec-155">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c3ec-155">Requirements</span></span>  
 <span data-ttu-id="8c3ec-156">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c3ec-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c3ec-157">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c3ec-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c3ec-158">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8c3ec-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c3ec-159">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c3ec-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3ec-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c3ec-160">See also</span></span>

- [<span data-ttu-id="8c3ec-161">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c3ec-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8c3ec-162">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c3ec-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
