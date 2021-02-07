---
description: 'Daha fazla bilgi edinin: CompareAssemblyIdentity Işlevi'
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
ms.openlocfilehash: aa55d1ea0b1968ec4e50106139e154e29e159ec7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761219"
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
 'ndaki Kullanıcı tarafından belirtilen için birleştirme belirten bir Boole bayrağı `pwzAssemblyIdentity1` .  
  
 `pwzAssemblyIdentity2`  
 'ndaki Karşılaştırmayla ikinci derlemenin metinsel kimliği.  
  
 `fUnified2`  
 'ndaki Kullanıcı tarafından belirtilen için birleştirme belirten bir Boole bayrağı `pwzAssemblyIdentity2` .  
  
 `pfEquivalent`  
 dışı İki derlemenin eşdeğer olup olmadığını belirten bir Boolean bayrak.  
  
 `pResult`  
 dışı Karşılaştırma hakkında ayrıntılı bilgi içeren bir [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `pfEquivalent` iki derlemenin eşdeğer olup olmadığını gösteren bir Boole değeri döndürür. `pResult``AssemblyComparisonResult`değeri için daha ayrıntılı bir neden vermek üzere değerlerden birini döndürür `pfEquivalent` .  
  
## <a name="remarks"></a>Açıklamalar  

 `CompareAssemblyIdentity` ve eşdeğer olup olmadığını denetler `pwzAssemblyIdentity1` `pwzAssemblyIdentity2` . `pfEquivalent` , `true` aşağıdaki koşullardan biri veya birkaçı altında olarak ayarlanır:  
  
- İki derleme kimliği eşdeğerdir. Kesin adlandırılmış derlemeler için, denkliği derleme adı, sürüm, ortak anahtar belirteci ve kültürün aynı olmasını gerektirir. Yalnızca adlandırılmış derlemeler için, denkliği derleme adı ve kültür üzerinde bir eşleşme gerektirir.  
  
- Her iki derleme kimliği de .NET Framework çalışan derlemelere başvurur. Bu koşul `true` , derleme sürüm numaraları eşleşmediğinden bile döndürür.  
  
- İki derleme yönetilen derlemeler değildir, ancak `fUnified1` veya `fUnified2` olarak ayarlanmıştır `true` .  
  
 `fUnified`Bayrak, kesin adlandırılmış derlemenin sürüm numarasına kadar olan tüm sürüm sayılarının kesin adlandırılmış derleme ile eşdeğer kabul edileceğini gösterir. Örneğin, değeri `pwzAssemblyIndentity1` "MyAssembly, Version = 3.0.0.0, Culture = neutral, PublicKeyToken =...." ve değeri `fUnified1` ise, bu, `true` Tüm MyAssembly sürümünün 0.0.0.0 ile 3.0.0.0 arasında kabul edilmesinin gerektiğini gösterir. Böyle bir durumda, `pwzAssemblyIndentity2` `pwzAssemblyIndentity1` daha düşük bir sürüm numarasına sahip olması dışında, ile aynı derlemeye başvuruyorsa, olarak `pfEquivalent` ayarlanır `true` . `pwzAssemblyIdentity2`Daha yüksek bir sürüm numarasına başvuruyorsa, `pfEquivalent` yalnızca değeri ise olarak ayarlanır `true` `fUnified2` `true` .  
  
 `pResult`Parametresi, iki derlemenin neden eşdeğer olarak kabul edildiği veya eşdeğer olmadığı hakkında belirli bilgiler içerir. Daha fazla bilgi için bkz. [AssemblyComparisonResult numaralandırması](assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
- [AssemblyComparisonResult Numaralandırması](assemblycomparisonresult-enumeration.md)
