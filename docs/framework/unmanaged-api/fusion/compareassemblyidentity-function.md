---
title: CompareAssemblyIdentity İşlevi
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 652000367c19572f73296c704047830ce1c74574
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231051"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="f4201-102">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="f4201-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="f4201-103">Eşdeğer olup olmadığını belirlemek için iki derleme kimlikleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="f4201-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4201-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4201-104">Syntax</span></span>  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4201-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4201-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="f4201-106">[in] Metinsel karşılaştırma ilk derlemesinde kimliği.</span><span class="sxs-lookup"><span data-stu-id="f4201-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="f4201-107">[in] Kullanıcı tanımlı Birleştirici için gösteren bir Boole bayrağı `pwzAssemblyIdentity1`.</span><span class="sxs-lookup"><span data-stu-id="f4201-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="f4201-108">[in] Metinsel karşılaştırma ikinci derlemesinde kimliği.</span><span class="sxs-lookup"><span data-stu-id="f4201-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="f4201-109">[in] Kullanıcı tanımlı Birleştirici için gösteren bir Boole bayrağı `pwzAssemblyIdentity2`.</span><span class="sxs-lookup"><span data-stu-id="f4201-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="f4201-110">[out] İki derlemeyi eşdeğer olup olmadığını belirten bir Boole bayrağı.</span><span class="sxs-lookup"><span data-stu-id="f4201-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="f4201-111">[out] Bir [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) karşılaştırma hakkında ayrıntılı bilgi içeren bir sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f4201-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4201-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f4201-112">Return Value</span></span>  
 `pfEquivalent` <span data-ttu-id="f4201-113">iki derlemeyi eşdeğer olup olmadığını gösteren bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4201-113">returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> `pResult` <span data-ttu-id="f4201-114">döndürür `AssemblyComparisonResult` değerine ilişkin daha ayrıntılı bir neden vermek için değerleri `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="f4201-114">returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4201-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4201-115">Remarks</span></span>  
 `CompareAssemblyIdentity` <span data-ttu-id="f4201-116">denetler olmadığını `pwzAssemblyIdentity1` ve `pwzAssemblyIdentity2` eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="f4201-116">checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> `pfEquivalent` <span data-ttu-id="f4201-117">ayarlanır `true` altında bir veya daha fazla aşağıdaki koşullardan biri:</span><span class="sxs-lookup"><span data-stu-id="f4201-117">is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="f4201-118">İki derleme kimlikleri büyük/küçük harf eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="f4201-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="f4201-119">Kesin adlandırılmış derlemelerin için denkliği derleme adı, sürüm, ortak anahtar belirteci ve kültür aynı olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f4201-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="f4201-120">Yalnızca adlandırılmış derlemeler için derleme adı ve kültür bir eşleşme denkliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f4201-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="f4201-121">Derleme kimlikleri'hem de .NET Framework derlemelerini bakın.</span><span class="sxs-lookup"><span data-stu-id="f4201-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="f4201-122">Bu durum döndürür `true` bile derleme sürüm numaraları eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="f4201-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="f4201-123">İki derlemenin Yönetilen derlemeler değildir ancak `fUnified1` veya `fUnified2` ayarlandı `true`.</span><span class="sxs-lookup"><span data-stu-id="f4201-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="f4201-124">`fUnified` Bayrağı belirten kesin adlandırılmış bütünleştirilmiş kod sürümü sayısı kadar tüm sürüm numaraları için kesin adlandırılmış derlemeyi eşdeğer olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f4201-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="f4201-125">Örneğin, varsa değerini `pwzAssemblyIndentity1` olan "MyAssembly, sürüm 3.0.0.0, culture = neutral, publicKeyToken = =..." ve değerini `fUnified1` olduğu `true`, bu sürüm için 0.0.0.0 3.0.0.0 MyAssembly tüm sürümlerini gerektiğini gösterir eşdeğer olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f4201-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="f4201-126">Böyle bir durumda ise `pwzAssemblyIndentity2` aynı derlemenin başvurduğu `pwzAssemblyIndentity1`, onu daha düşük bir sürüm numarası olan `pfEquivalent` ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="f4201-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="f4201-127">Varsa `pwzAssemblyIdentity2` daha yüksek bir sürüm numarası, başvuran `pfEquivalent` ayarlanır `true` yalnızca değerini `fUnified2` olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="f4201-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="f4201-128">`pResult` Parametresi neden iki derlemeyi eşdeğer veya eşdeğer değil olarak kabul edilir hakkında ayrıntılı bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f4201-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="f4201-129">Daha fazla bilgi için [AssemblyComparisonResult numaralandırması](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f4201-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4201-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4201-130">Requirements</span></span>  
 <span data-ttu-id="f4201-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4201-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4201-132">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f4201-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f4201-133">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f4201-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f4201-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f4201-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4201-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4201-135">See also</span></span>

- [<span data-ttu-id="f4201-136">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f4201-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="f4201-137">AssemblyComparisonResult Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f4201-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
