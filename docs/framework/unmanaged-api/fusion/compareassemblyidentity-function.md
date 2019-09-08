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
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity İşlevi
, Eşdeğer olup olmadıklarını anlamak için iki derleme kimliğini karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="parameters"></a>Parametreler  
 `pwzAssemblyIdentity1`  
 'ndaki Karşılaştırmayla ilk derlemenin metinsel kimliği.  
  
 `fUnified1`  
 'ndaki Kullanıcı tarafından belirtilen için `pwzAssemblyIdentity1`birleştirme belirten bir Boole bayrağı.  
  
 `pwzAssemblyIdentity2`  
 'ndaki Karşılaştırmayla ikinci derlemenin metinsel kimliği.  
  
 `fUnified2`  
 'ndaki Kullanıcı tarafından belirtilen için `pwzAssemblyIdentity2`birleştirme belirten bir Boole bayrağı.  
  
 `pfEquivalent`  
 dışı İki derlemenin eşdeğer olup olmadığını belirten bir Boolean bayrak.  
  
 `pResult`  
 dışı Karşılaştırma hakkında ayrıntılı bilgi içeren bir [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `pfEquivalent`iki derlemenin eşdeğer olup olmadığını gösteren bir Boole değeri döndürür. `pResult`değeri için daha ayrıntılı `AssemblyComparisonResult` bir neden vermek üzere değerlerden birini döndürür. `pfEquivalent`  
  
## <a name="remarks"></a>Açıklamalar  
 `CompareAssemblyIdentity``pwzAssemblyIdentity1` ve`pwzAssemblyIdentity2` eşdeğer olup olmadığını denetler. `pfEquivalent`, aşağıdaki koşullardan `true` biri veya birkaçı altında olarak ayarlanır:  
  
- İki derleme kimliği eşdeğerdir. Kesin adlandırılmış derlemeler için, denkliği derleme adı, sürüm, ortak anahtar belirteci ve kültürün aynı olmasını gerektirir. Yalnızca adlandırılmış derlemeler için, denkliği derleme adı ve kültür üzerinde bir eşleşme gerektirir.  
  
- Her iki derleme kimliği de .NET Framework çalışan derlemelere başvurur. Bu koşul, `true` derleme sürüm numaraları eşleşmediğinden bile döndürür.  
  
- İki derleme yönetilen derlemeler değildir, ancak `fUnified1` veya `fUnified2` olarak `true`ayarlanmıştır.  
  
 `fUnified` Bayrak, kesin adlandırılmış derlemenin sürüm numarasına kadar olan tüm sürüm sayılarının kesin adlandırılmış derleme ile eşdeğer kabul edileceğini gösterir. Örneğin, değeri `pwzAssemblyIndentity1` "MyAssembly, Version = 3.0.0.0, Culture = neutral, PublicKeyToken =...." ve `fUnified1` değeri `true`ise, bu, tüm MyAssembly sürümünün 0.0.0.0 ve 3.0.0.0 olarak olduğunu gösterir. eşdeğer olarak kabul edilir. Böyle bir durumda `pwzAssemblyIndentity2` , daha `pfEquivalent` düşük bir sürüm `true`numarasına sahip olması dışında `pwzAssemblyIndentity1`, ile aynı derlemeye başvuruyorsa, olarak ayarlanır. `fUnified2` `pfEquivalent` `true` Daha yüksek bir sürüm numarasına `true`başvuruyorsa, yalnızca değeri ise olarak ayarlanır. `pwzAssemblyIdentity2`  
  
 `pResult` Parametresi, iki derlemenin neden eşdeğer olarak kabul edildiği veya eşdeğer olmadığı hakkında belirli bilgiler içerir. Daha fazla bilgi için bkz. [AssemblyComparisonResult numaralandırması](assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Fusion. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
- [AssemblyComparisonResult Sabit Listesi](assemblycomparisonresult-enumeration.md)
