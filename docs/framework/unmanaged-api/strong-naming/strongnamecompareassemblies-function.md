---
title: StrongNameCompareAssemblies İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: adde52dddb63b83dcd7ff10703a43928d9601c92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140624"
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies İşlevi
İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszAssembly1`  
 'ndaki İlk derlemenin yolu.  
  
 `wszAssembly2`  
 'ndaki İkinci derlemenin yolu.  
  
 `pdwResult`  
 dışı Aşağıdaki değerlerden biri:  
  
- `SN_CMP_DIFFERENT` (0)-derlemelerin farklı veriler içerdiğini belirtir.  
  
- `SN_CMP_IDENTICAL` (1)-derlemelerin imzaları ve sağlama toplamı dahil olmak üzere tam olarak aynı olduğunu belirtir.  
  
- `SN_CMP_SIGONLY` (2)-derlemelerin yalnızca imzaya ve sağlama toplamına göre farklı olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 başarılı tamamlamada `true`; Aksi takdirde, `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Açıklamalar  
 Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirtecinden oluşur.  
  
 `StrongNameCompareAssemblies` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameCompareAssemblies Yöntemi](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
