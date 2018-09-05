---
title: CreateClassEnumWmi işlevi (yönetilmeyen API Başvurusu)
description: CreateClassEnumWmi işlevi, belirtilen ölçütleri karşılayan tüm sınıflar için bir numaralandırıcı döndürür.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b38e4753105932d2464bf78797a6979aeb0a0aee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527845"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi işlevi
Belirtilen seçim kriterleri karşılayan tüm sınıflar için bir numaralandırıcı döndürür.  

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
[in] Aksi takdirde `null` veya boş, bir üst sınıf; adını belirtir. yalnızca alt sınıfları bu sınıftan bir numaralandırıcı döndürür. Eğer öyleyse `null` veya boş ve `lFlags` WBEM_FLAG_SHALLOW ise, yalnızca üst düzey sınıflar (hiçbir üst sınıf ile sınıflar) döndürür. Eğer öyleyse `null` veya boş ve `lFlags` olduğu `WBEM_FLAG_DEEP`, ad alanındaki tüm sınıfları döndürür.

`lFlags`   
[in] Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda: 

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri işlev kümesini alır <br/> Aksi durumda, küme yalnızca anında ad alanında depolanan niteleyicileri işlevi alır. |
| `WBEM_FLAG_DEEP` | 0 | Numaralandırma, hiyerarşi, ancak bu sınıfın tüm alt sınıflar içerir. |
| `WBEM_FLAG_SHALLOW` | 1. | Bu sınıfın yalnızca saf örneklerini içerir ve bu sınıfında bulunmayan özellikleri tedarik alt sınıfların tüm örneklerini dahil değildir. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumsuz bir çağrı neden olur. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlev yalnızca iletme bir numaralandırıcı döndürür. Genellikle, yalnızca iletme numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrısına izin verme [kopya](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Serbest bırakılana kadar WMI enumration nesnelerine işaretçiler korur. | 

Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.

`pCtx`  
[in] Genellikle, bu değer, `null`. Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen sınıfları sağlayan sağlayıcı tarafından kullanılan bir örnek. 

`ppEnum`  
[out] İşaretçi numaralandırıcıyı alır.

`authLevel`  
[in] Yetkilendirme düzeyi.

`impLevel` [in] Kimliğe bürünme düzeyi.

`pCurrentNamespace`   
[in] Bir işaretçi bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) geçerli ad alanını temsil eden nesne.

`strUser`   
[in] Kullanıcı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

`strPassword`   
[in] Parola. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

`strAuthority`   
[in] Kullanıcı etki alanı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` mevcut değil. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durdu ve yeniden başlatılıyor. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) yöntemi.

İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
