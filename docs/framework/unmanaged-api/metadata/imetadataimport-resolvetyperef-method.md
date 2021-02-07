---
description: ': IMetaDataImport:: ResolveTypeRef yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::ResolveTypeRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 0634bac77f457432948d0c2887d676e95430d05d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677569"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="d5d6e-103">IMetaDataImport::ResolveTypeRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5d6e-103">IMetaDataImport::ResolveTypeRef Method</span></span>

<span data-ttu-id="d5d6e-104"><xref:System.Type>Belirtilen TypeRef belirteci ile temsil edilen bir başvuruyu çözümler.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-104">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d6e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5d6e-105">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5d6e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5d6e-106">Parameters</span></span>  

 `tr`  
 <span data-ttu-id="d5d6e-107">'ndaki İçin başvurulan tür bilgilerini döndürecek olan TypeRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-107">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="d5d6e-108">'ndaki Döndürülecek arabirimin IID 'si `ppIScope` .</span><span class="sxs-lookup"><span data-stu-id="d5d6e-108">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="d5d6e-109">Genellikle bu IID_IMetaDataImport olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-109">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="d5d6e-110">dışı Başvurulan türün tanımlandığı modül kapsamına yönelik arabirim.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-110">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="d5d6e-111">dışı Başvurulan türü temsil eden bir TypeDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-111">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5d6e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5d6e-112">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d5d6e-113">Birden çok uygulama etki alanı yüklenmişse bu yöntemi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-113">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="d5d6e-114">Yöntem, uygulama etki alanı sınırlarına uymaz.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-114">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="d5d6e-115">Bir derlemenin birden çok sürümü yüklüyse ve aynı ad alanıyla aynı türü içeriyorsa, yöntemi bulduğu ilk türün modül kapsamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-115">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="d5d6e-116">`ResolveTypeRef`Yöntemi, diğer modüllerde tür tanımını arar.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-116">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="d5d6e-117">Tür tanımı bulunursa, `ResolveTypeRef` Bu modül kapsamına ve tür Için typedef belirtecine bir arabirim döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-117">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="d5d6e-118">Çözümlenecek tür başvurusunun AssemblyRef bir çözüm kapsamı varsa, `ResolveTypeRef` yöntemi yalnızca [ımetadatadağıtıcı:: OpenScope](imetadatadispenser-openscope-method.md) yöntemi veya [ımetadatadağıtıcı:: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) metoduna yapılan çağrılarla zaten açılmış olan meta veri kapsamlarındaki eşleşmeyi arar.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-118">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="d5d6e-119">Bunun nedeni, `ResolveTypeRef` yalnızca diskte veya derlemenin depolandığı genel derleme önbelleğinde bulunan AssemblyRef kapsamından saptanamıyor.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-119">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d6e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5d6e-120">Requirements</span></span>  

 <span data-ttu-id="d5d6e-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5d6e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5d6e-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d5d6e-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5d6e-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d5d6e-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5d6e-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5d6e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d6e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5d6e-125">See also</span></span>

- [<span data-ttu-id="d5d6e-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5d6e-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d5d6e-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5d6e-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
