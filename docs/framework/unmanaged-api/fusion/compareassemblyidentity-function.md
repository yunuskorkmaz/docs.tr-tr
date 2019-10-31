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
ms.openlocfilehash: f6711902fb9d5c5c16084057b731746843cf0230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108916"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="7a6a0-102">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="7a6a0-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="7a6a0-103">, Eşdeğer olup olmadıklarını anlamak için iki derleme kimliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a6a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a6a0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7a6a0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a6a0-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="7a6a0-106">'ndaki Karşılaştırmayla ilk derlemenin metinsel kimliği.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="7a6a0-107">'ndaki `pwzAssemblyIdentity1`için Kullanıcı tarafından belirtilen birleştirme belirten bir Boole bayrağı.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="7a6a0-108">'ndaki Karşılaştırmayla ikinci derlemenin metinsel kimliği.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="7a6a0-109">'ndaki `pwzAssemblyIdentity2`için Kullanıcı tarafından belirtilen birleştirme belirten bir Boole bayrağı.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="7a6a0-110">dışı İki derlemenin eşdeğer olup olmadığını belirten bir Boolean bayrak.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="7a6a0-111">dışı Karşılaştırma hakkında ayrıntılı bilgi içeren bir [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a6a0-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a6a0-112">Return Value</span></span>  
 <span data-ttu-id="7a6a0-113">`pfEquivalent` iki derlemenin eşdeğer olup olmadığını gösteren bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="7a6a0-114">`pResult`, `pfEquivalent`değerinin daha ayrıntılı bir sebebini sağlamak için `AssemblyComparisonResult` değerlerinden birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a6a0-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a6a0-115">Remarks</span></span>  
 <span data-ttu-id="7a6a0-116">`CompareAssemblyIdentity`, `pwzAssemblyIdentity1` ve `pwzAssemblyIdentity2` eşdeğer olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="7a6a0-117">`pfEquivalent`, aşağıdaki koşullardan biri veya birkaçı altında `true` olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="7a6a0-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="7a6a0-118">İki derleme kimliği eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="7a6a0-119">Kesin adlandırılmış derlemeler için, denkliği derleme adı, sürüm, ortak anahtar belirteci ve kültürün aynı olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="7a6a0-120">Yalnızca adlandırılmış derlemeler için, denkliği derleme adı ve kültür üzerinde bir eşleşme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="7a6a0-121">Her iki derleme kimliği de .NET Framework çalışan derlemelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="7a6a0-122">Bu koşul, derleme sürüm numaraları eşleşmediğinden bile `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="7a6a0-123">İki derleme yönetilen derlemeler değildir, ancak `fUnified1` veya `fUnified2` `true`olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="7a6a0-124">`fUnified` bayrağı, kesin adlandırılmış derlemenin sürüm numarasına kadar olan tüm sürüm sayılarının, kesin adlandırılmış derleme ile eşdeğer kabul edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="7a6a0-125">Örneğin, `pwzAssemblyIndentity1` değeri "MyAssembly, Version = 3.0.0.0, Culture = neutral, publicKeyToken =...." ve `fUnified1` değeri `true`ise, bu, MyAssembly 'in 0.0.0.0 olan tüm sürümlerinin 3.0.0.0 olarak değerlendirildiğini gösterir. değerinin.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="7a6a0-126">Böyle bir durumda `pwzAssemblyIndentity2` `pwzAssemblyIndentity1`ile aynı derlemeye başvuruyorsa, daha düşük bir sürüm numarası olması dışında `pfEquivalent` `true`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="7a6a0-127">`pwzAssemblyIdentity2` daha yüksek bir sürüm numarasına başvuruyorsa, `pfEquivalent` yalnızca `fUnified2` değeri `true``true` olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="7a6a0-128">`pResult` parametresi, iki derlemenin neden eşdeğer olarak kabul edildiği veya eşdeğer olmadığı hakkında özel bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="7a6a0-129">Daha fazla bilgi için bkz. [AssemblyComparisonResult numaralandırması](assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7a6a0-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a6a0-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a6a0-130">Requirements</span></span>  
 <span data-ttu-id="7a6a0-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a6a0-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a6a0-132">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7a6a0-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7a6a0-133">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7a6a0-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a6a0-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a6a0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6a0-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a6a0-135">See also</span></span>

- [<span data-ttu-id="7a6a0-136">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7a6a0-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="7a6a0-137">AssemblyComparisonResult Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7a6a0-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
