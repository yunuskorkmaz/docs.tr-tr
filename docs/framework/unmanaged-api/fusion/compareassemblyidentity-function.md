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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914530"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity İşlevi
Eşdeğer olup olmadığını belirlemek için iki derleme kimlikleri karşılaştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="parameters"></a>Parametreler  
 `pwzAssemblyIdentity1`  
 [in] Metinsel karşılaştırma ilk derlemesinde kimliği.  
  
 `fUnified1`  
 [in] Kullanıcı tanımlı Birleştirici için gösteren bir Boole bayrağı `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [in] Metinsel karşılaştırma ikinci derlemesinde kimliği.  
  
 `fUnified2`  
 [in] Kullanıcı tanımlı Birleştirici için gösteren bir Boole bayrağı `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] İki derlemeyi eşdeğer olup olmadığını belirten bir Boole bayrağı.  
  
 `pResult`  
 [out] Bir [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) karşılaştırma hakkında ayrıntılı bilgi içeren bir sabit listesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `pfEquivalent` iki derlemeyi eşdeğer olup olmadığını gösteren bir Boole değeri döndürür. `pResult` döndürür `AssemblyComparisonResult` değerine ilişkin daha ayrıntılı bir neden vermek için değerleri `pfEquivalent`.  
  
## <a name="remarks"></a>Açıklamalar  
 `CompareAssemblyIdentity` denetler olmadığını `pwzAssemblyIdentity1` ve `pwzAssemblyIdentity2` eşdeğerdir. `pfEquivalent` ayarlanır `true` altında bir veya daha fazla aşağıdaki koşullardan biri:  
  
- İki derleme kimlikleri büyük/küçük harf eşdeğerdir. Kesin adlandırılmış derlemelerin için denkliği derleme adı, sürüm, ortak anahtar belirteci ve kültür aynı olmasını gerektirir. Yalnızca adlandırılmış derlemeler için derleme adı ve kültür bir eşleşme denkliği gerektirir.  
  
- Derleme kimlikleri'hem de .NET Framework derlemelerini bakın. Bu durum döndürür `true` bile derleme sürüm numaraları eşleşmiyor.  
  
- İki derlemenin Yönetilen derlemeler değildir ancak `fUnified1` veya `fUnified2` ayarlandı `true`.  
  
 `fUnified` Bayrağı belirten kesin adlandırılmış bütünleştirilmiş kod sürümü sayısı kadar tüm sürüm numaraları için kesin adlandırılmış derlemeyi eşdeğer olarak değerlendirilir. Örneğin, varsa değerini `pwzAssemblyIndentity1` olan "MyAssembly, sürüm 3.0.0.0, culture = neutral, publicKeyToken = =..." ve değerini `fUnified1` olduğu `true`, bu sürüm için 0.0.0.0 3.0.0.0 MyAssembly tüm sürümlerini gerektiğini gösterir eşdeğer olarak kabul edilir. Böyle bir durumda ise `pwzAssemblyIndentity2` aynı derlemenin başvurduğu `pwzAssemblyIndentity1`, onu daha düşük bir sürüm numarası olan `pfEquivalent` ayarlanır `true`. Varsa `pwzAssemblyIdentity2` daha yüksek bir sürüm numarası, başvuran `pfEquivalent` ayarlanır `true` yalnızca değerini `fUnified2` olduğu `true`.  
  
 `pResult` Parametresi neden iki derlemeyi eşdeğer veya eşdeğer değil olarak kabul edilir hakkında ayrıntılı bilgi içerir. Daha fazla bilgi için [AssemblyComparisonResult numaralandırması](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [AssemblyComparisonResult Sabit Listesi](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
