---
title: IMetaDataDispenser::OpenScope Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007474"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope Yöntemi
Mevcut, disk üzerindeki bir dosyayı açar ve meta verilerini belleğe eşler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szScope`  
 'ndaki Açılacak dosyanın adı. Dosya, ortak dil çalışma zamanı (CLR) meta verilerini içermelidir.  
  
 `dwOpenFlags`  
 'ndaki Açma için modu (okuma, yazma, vb.) belirtmek için [CorOpenFlags](coropenflags-enumeration.md) numaralandırması değeri.  
  
 `riid`  
 'ndaki Döndürülecek istenen meta veri arabiriminin IID 'si; çağıran, meta verileri içeri aktarmak (okumak) veya yayma (yazmak) için arabirimini kullanır.  
  
 Değeri, `riid` "import" veya "yayma" arabirimlerinden birini belirtmelidir. Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.  
  
 `ppIUnk`  
 dışı Döndürülen arabirime yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta verilerin bellek içi kopyası, "içeri aktarma" arabirimlerinden birindeki yöntemler kullanılarak sorgulanabilir veya "yayma" arabirimlerinden birindeki yöntemleri kullanarak eklenebilir.  
  
 Hedef dosya CLR meta verileri içermiyorsa, `OpenScope` Yöntem başarısız olur.  
  
 .NET Framework sürüm 1,0 ve sürüm 1,1 ' de bir kapsam, `dwOpenFlags` ofRead olarak ayarlandıysa, paylaşım için uygundur. Diğer bir deyişle, `OpenScope` daha önce açılan bir dosyanın adında sonraki çağrılar varsa, mevcut kapsam yeniden kullanılır ve yeni bir veri yapıları kümesi oluşturulmaz. Ancak, bu paylaşım nedeniyle sorunlar ortaya çıkabilir.  
  
 .NET Framework sürüm 2,0 ' de, `dwOpenFlags` ofRead olarak ayarlanan ile açılan kapsamlar artık paylaşılmaz. Kapsamın paylaşılmasını sağlamak için ofReadOnly değerini kullanın. Bir kapsam paylaşıldığında, "okuma/yazma" meta veri arabirimlerini kullanan sorgular başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenser Yöntemi](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx Arabirimi](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
