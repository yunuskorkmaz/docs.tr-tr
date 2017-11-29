---
title: "CreateClassEnumWmi işlevi (yönetilmeyen API Başvurusu)"
description: "CreateClassEnumWmi işlevi belirtilen ölçütleri karşılayan tüm sınıflar için bir numaralandırıcı döndürür."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateClassEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateClassEnumWmi
helpviewer_keywords: CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bfbfee6f8e98d04a591c58560e6d50044e716a1f
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi işlevi
Belirtilen seçim ölçütü karşılayan tüm sınıflar için bir numaralandırıcı döndürür.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a>Parametreler

`strSuperclass`    
[in] Aksi takdirde `null` veya boş, bir üst sınıf; adını belirtir, bu sınıfın yalnızca alt sınıfların Numaralandırıcı döndürür. Eğer öyleyse `null` ya da boş ve `lFlags` WBEM_FLAG_SHALLOW ise, yalnızca üst düzey sınıflar (hiçbir üst sınıf sınıflarıyla) döndürür. Eğer öyleyse `null` ya da boş ve `lFlags` olan `WBEM_FLAG_DEEP`, ad alanındaki tüm sınıfları döndürür.

`lFlags`   
[in] Bu işlev davranışını etkileyen bayrak birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda: 

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri kümesi, işlevi alır <br/> Aksi durumda kümesi işlevi yalnızca hemen ad alanında depolanan niteleyicileri alır. |
| `WBEM_FLAG_DEEP` | 0 | Numaralandırma, hiyerarşi, ancak bu sınıfın tüm alt sınıflar içerir. |
| `WBEM_FLAG_SHALLOW` | 1. | Numaralandırma yalnızca saf bu sınıfın örnekleri içerir ve bu sınıfında bulunmayan özellikleri tedarik alt sınıfların tüm örneklerini dışlar. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumlu bir çağrı neden olur. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlevi yalnızca ileri bir numaralandırıcı döndürür. Genellikle, yalnızca ileri numaralandırıcılar daha hızlı ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrıları izin verme [kopya](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Serbest bırakılana kadar WMI enumration nesnelerine işaretçiler korur. | 

Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.

`pCtx`  
[in] Bu değer genellikle `null`. Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen sınıfları sağlayarak sağlayıcı tarafından kullanılan örnek. 

`ppEnum`  
[out] İşaretçi Numaralandırıcı alır.

`authLevel`  
[in] Kimlik doğrulama düzeyi.

`impLevel`[in] Kimliğe bürünme düzeyi.

`pCurrentNamespace`   
[in] Bir işaretçi bir [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) geçerli ad alanını temsil eden nesne.

`strUser`   
[in] Kullanıcı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.

`strPassword`   
[in] Parola. Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.

`strAuthority`   
[in] Kullanıcının etki alanı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirlenemeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass`mevcut değil. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durduruldu ve yeniden başlatma. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) yöntemi.

İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
