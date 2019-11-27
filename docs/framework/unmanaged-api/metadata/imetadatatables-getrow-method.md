---
title: IMetaDataTables::GetRow Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 9973ef77a064dfe144d742d8cf12d8ae8dd2565f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447404"
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow Yöntemi
Belirtilen tablo dizinindeki tabloda belirtilen satır dizinindeki satırı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ixTbl`  
 'ndaki Satırın alınacağı tablonun dizini.  
  
 `rid`  
 'ndaki Alınacak satırın dizini.  
  
 `ppRow`  
 dışı Satır işaretçisinin işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz. GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği". Belgeler çevrimiçi olarak kullanılabilir; Ecma International web sitesinde, MSDN ve [standart ECMA-335-ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) üzerinde bulunan [ECMA C# ve ortak dil altyapısı standartlarına](https://go.microsoft.com/fwlink/?LinkID=99212) bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümler**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
