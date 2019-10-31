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
 'ndaki `pwzAssemblyIdentity1`için Kullanıcı tarafından belirtilen birleştirme belirten bir Boole bayrağı.  
  
 `pwzAssemblyIdentity2`  
 'ndaki Karşılaştırmayla ikinci derlemenin metinsel kimliği.  
  
 `fUnified2`  
 'ndaki `pwzAssemblyIdentity2`için Kullanıcı tarafından belirtilen birleştirme belirten bir Boole bayrağı.  
  
 `pfEquivalent`  
 dışı İki derlemenin eşdeğer olup olmadığını belirten bir Boolean bayrak.  
  
 `pResult`  
 dışı Karşılaştırma hakkında ayrıntılı bilgi içeren bir [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `pfEquivalent` iki derlemenin eşdeğer olup olmadığını gösteren bir Boole değeri döndürür. `pResult`, `pfEquivalent`değerinin daha ayrıntılı bir sebebini sağlamak için `AssemblyComparisonResult` değerlerinden birini döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 `CompareAssemblyIdentity`, `pwzAssemblyIdentity1` ve `pwzAssemblyIdentity2` eşdeğer olup olmadığını denetler. `pfEquivalent`, aşağıdaki koşullardan biri veya birkaçı altında `true` olarak ayarlanır:  
  
- İki derleme kimliği eşdeğerdir. Kesin adlandırılmış derlemeler için, denkliği derleme adı, sürüm, ortak anahtar belirteci ve kültürün aynı olmasını gerektirir. Yalnızca adlandırılmış derlemeler için, denkliği derleme adı ve kültür üzerinde bir eşleşme gerektirir.  
  
- Her iki derleme kimliği de .NET Framework çalışan derlemelere başvurur. Bu koşul, derleme sürüm numaraları eşleşmediğinden bile `true` döndürür.  
  
- İki derleme yönetilen derlemeler değildir, ancak `fUnified1` veya `fUnified2` `true`olarak ayarlanmıştır.  
  
 `fUnified` bayrağı, kesin adlandırılmış derlemenin sürüm numarasına kadar olan tüm sürüm sayılarının, kesin adlandırılmış derleme ile eşdeğer kabul edileceğini gösterir. Örneğin, `pwzAssemblyIndentity1` değeri "MyAssembly, Version = 3.0.0.0, Culture = neutral, publicKeyToken =...." ve `fUnified1` değeri `true`ise, bu, MyAssembly 'in 0.0.0.0 olan tüm sürümlerinin 3.0.0.0 olarak değerlendirildiğini gösterir. değerinin. Böyle bir durumda `pwzAssemblyIndentity2` `pwzAssemblyIndentity1`ile aynı derlemeye başvuruyorsa, daha düşük bir sürüm numarası olması dışında `pfEquivalent` `true`olarak ayarlanır. `pwzAssemblyIdentity2` daha yüksek bir sürüm numarasına başvuruyorsa, `pfEquivalent` yalnızca `fUnified2` değeri `true``true` olarak ayarlanır.  
  
 `pResult` parametresi, iki derlemenin neden eşdeğer olarak kabul edildiği veya eşdeğer olmadığı hakkında özel bilgiler içerir. Daha fazla bilgi için bkz. [AssemblyComparisonResult numaralandırması](assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
- [AssemblyComparisonResult Sabit Listesi](assemblycomparisonresult-enumeration.md)
