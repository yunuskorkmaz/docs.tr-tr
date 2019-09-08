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
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795451"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="c6ae9-102">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="c6ae9-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="c6ae9-103">, Eşdeğer olup olmadıklarını anlamak için iki derleme kimliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ae9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6ae9-104">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6ae9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6ae9-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="c6ae9-106">'ndaki Karşılaştırmayla ilk derlemenin metinsel kimliği.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="c6ae9-107">'ndaki Kullanıcı tarafından belirtilen için `pwzAssemblyIdentity1`birleştirme belirten bir Boole bayrağı.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="c6ae9-108">'ndaki Karşılaştırmayla ikinci derlemenin metinsel kimliği.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="c6ae9-109">'ndaki Kullanıcı tarafından belirtilen için `pwzAssemblyIdentity2`birleştirme belirten bir Boole bayrağı.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="c6ae9-110">dışı İki derlemenin eşdeğer olup olmadığını belirten bir Boolean bayrak.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="c6ae9-111">dışı Karşılaştırma hakkında ayrıntılı bilgi içeren bir [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6ae9-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6ae9-112">Return Value</span></span>  
 <span data-ttu-id="c6ae9-113">`pfEquivalent`iki derlemenin eşdeğer olup olmadığını gösteren bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="c6ae9-114">`pResult`değeri için daha ayrıntılı `AssemblyComparisonResult` bir neden vermek üzere değerlerden birini döndürür. `pfEquivalent`</span><span class="sxs-lookup"><span data-stu-id="c6ae9-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6ae9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6ae9-115">Remarks</span></span>  
 <span data-ttu-id="c6ae9-116">`CompareAssemblyIdentity``pwzAssemblyIdentity1` ve`pwzAssemblyIdentity2` eşdeğer olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="c6ae9-117">`pfEquivalent`, aşağıdaki koşullardan `true` biri veya birkaçı altında olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="c6ae9-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="c6ae9-118">İki derleme kimliği eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="c6ae9-119">Kesin adlandırılmış derlemeler için, denkliği derleme adı, sürüm, ortak anahtar belirteci ve kültürün aynı olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="c6ae9-120">Yalnızca adlandırılmış derlemeler için, denkliği derleme adı ve kültür üzerinde bir eşleşme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="c6ae9-121">Her iki derleme kimliği de .NET Framework çalışan derlemelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="c6ae9-122">Bu koşul, `true` derleme sürüm numaraları eşleşmediğinden bile döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="c6ae9-123">İki derleme yönetilen derlemeler değildir, ancak `fUnified1` veya `fUnified2` olarak `true`ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="c6ae9-124">`fUnified` Bayrak, kesin adlandırılmış derlemenin sürüm numarasına kadar olan tüm sürüm sayılarının kesin adlandırılmış derleme ile eşdeğer kabul edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="c6ae9-125">Örneğin, değeri `pwzAssemblyIndentity1` "MyAssembly, Version = 3.0.0.0, Culture = neutral, PublicKeyToken =...." ve `fUnified1` değeri `true`ise, bu, tüm MyAssembly sürümünün 0.0.0.0 ve 3.0.0.0 olarak olduğunu gösterir. eşdeğer olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="c6ae9-126">Böyle bir durumda `pwzAssemblyIndentity2` , daha `pfEquivalent` düşük bir sürüm `true`numarasına sahip olması dışında `pwzAssemblyIndentity1`, ile aynı derlemeye başvuruyorsa, olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="c6ae9-127">`fUnified2` `pfEquivalent` `true` Daha yüksek bir sürüm numarasına `true`başvuruyorsa, yalnızca değeri ise olarak ayarlanır. `pwzAssemblyIdentity2`</span><span class="sxs-lookup"><span data-stu-id="c6ae9-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="c6ae9-128">`pResult` Parametresi, iki derlemenin neden eşdeğer olarak kabul edildiği veya eşdeğer olmadığı hakkında belirli bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="c6ae9-129">Daha fazla bilgi için bkz. [AssemblyComparisonResult numaralandırması](assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c6ae9-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ae9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6ae9-130">Requirements</span></span>  
 <span data-ttu-id="c6ae9-131">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ae9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ae9-132">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c6ae9-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c6ae9-133">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c6ae9-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6ae9-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ae9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ae9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6ae9-135">See also</span></span>

- [<span data-ttu-id="c6ae9-136">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c6ae9-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="c6ae9-137">AssemblyComparisonResult Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c6ae9-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
