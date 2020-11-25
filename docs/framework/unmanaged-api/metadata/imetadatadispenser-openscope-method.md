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
ms.openlocfilehash: f2a85bafc3e2f25b2ed6116a46a9938d869dbaae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726086"
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
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenser Arabirimi](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx Arabirimi](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
