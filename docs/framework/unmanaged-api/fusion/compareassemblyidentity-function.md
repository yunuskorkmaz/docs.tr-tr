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
ms.openlocfilehash: 1b48adcb8e9de49a312af77c8a9b80a07455ebfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity İşlevi
Eşdeğer olup olmadıklarını belirlemek için iki derleme kimlikleri karşılaştırır.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `pwzAssemblyIdentity1`  
 [in] Karşılaştırma ilk derlemede metinsel kimliği.  
  
 `fUnified1`  
 [in] Kullanıcı tarafından belirtilen Birleştirici için gösteren bir Boole bayrağı `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [in] Karşılaştırma ikinci derlemede metinsel kimliği.  
  
 `fUnified2`  
 [in] Kullanıcı tarafından belirtilen Birleştirici için gösteren bir Boole bayrağı `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] İki derleme eşdeğer olup olmadığını gösteren bir Boole bayrak.  
  
 `pResult`  
 [out] Bir [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) karşılaştırması hakkında ayrıntılı bilgi içeren numaralandırması.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `pfEquivalent` İki derleme eşdeğer olup olmadığını gösteren bir Boole değeri döndürür. `pResult` aşağıdakilerden birini döndürür `AssemblyComparisonResult` değerine ilişkin daha ayrıntılı bir nedenle vermek için değerleri `pfEquivalent`.  
  
## <a name="remarks"></a>Açıklamalar  
 `CompareAssemblyIdentity` denetler olup olmadığını `pwzAssemblyIdentity1` ve `pwzAssemblyIdentity2` eşdeğerdir. `pfEquivalent` ayarlanmış `true` altında bir veya daha fazla aşağıdaki koşullardan biri:  
  
-   İki derleme kimlikleri eşdeğerdir. Türü kesin adlandırılmış derlemeler için derleme adı, sürüm, ortak anahtar belirteci ve aynı olacak şekilde kültür denkliği gerektirir. Yalnızca adlandırılmış derlemeler için derleme adı ve kültür bir eşleşme denkliği gerektirir.  
  
-   Hem derleme kimlikleri .NET Framework üzerine Çalıştır derlemeleri bakın. Bu durum döndürür `true` dahi derleme sürüm numaraları eşleşmiyor.  
  
-   İki derleme Yönetilen derlemeler değildir ancak `fUnified1` veya `fUnified2` ayarlandı `true`.  
  
 `fUnified` Bayrağı gösterir tüm sürüm numaralarını kesin adlandırılmış derleme sürüm sayısı kadar kesin adlandırılmış derlemeye eşdeğer olarak değerlendiriliyor. Örneğin, varsa değerini `pwzAssemblyIndentity1` olan "MyAssembly, sürüm 3.0.0.0, culture = neutral, publicKeyToken = =...", değerini `fUnified1` olan `true`, bu sürüm için 0.0.0.0 3.0.0.0 MyAssembly'nin tüm sürümleri olması gerektiğini gösterir eşdeğer olarak kabul edilir. Böyle bir durumda olmadığını `pwzAssemblyIndentity2` aynı bütünleştirilmiş başvurduğu `pwzAssemblyIndentity1`, daha düşük bir sürüm numarası olan dışında `pfEquivalent` ayarlanır `true`. Varsa `pwzAssemblyIdentity2` daha yüksek bir sürüm numarası, başvuruyor `pfEquivalent` ayarlanır `true` yalnızca değerini `fUnified2` olan `true`.  
  
 `pResult` Parametresi neden iki derleme eşdeğer veya eşdeğer değil olarak kabul edilir hakkında ayrıntılı bilgi içerir. Daha fazla bilgi için bkz: [AssemblyComparisonResult numaralandırması](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [AssemblyComparisonResult Sabit Listesi](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
