---
title: Ortak Veri Türleri (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
ms.openlocfilehash: 5c00ff6d0947b5d847a9622dce02bd310491818c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673988"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Ortak Veri Türleri (Yönetilmeyen API Başvurusu)

Bu konu, C/C++ deyimleri tarafından tanımlanan .NET Framework için yönetilmeyen API 'Ler tarafından kullanılan basit veri türlerini listeler `typedef` . Bu veri türleri genellikle C/C++ temel veri türleri için diğer adlardır. Genellikle, bu veri türlerinin değerleri opaktır; diğer bir deyişle, bunlar belirli bir işlev veya yöntem tarafından, değişiklik yapılmadan diğer işlevlere veya yöntemlere geçirilebilmeleri için döndürülür.  
  
|Veri türü|Tanım|Tanımlı|Açıklama|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|CorProf. h|Bir uygulama etki alanının tanımlayıcısı.|  
|AssemblyId|`typedef UINT_PTR AssemblyID;`|CorProf. h|Bir derlemenin tanımlayıcısı.|  
|ClassID|`typedef UINT_PTR ClassID;`|CorProf. h|Yönetilen bir sınıfın tanımlayıcısı.|  
|CLRDATA_ADDRESS|`typedef ULONG64 CLRDATA_ADDRESS;`|ClrData. h|64 bitlik bir bellek adresi.|
|CLRDATA_ENUM|`typedef ULONG64 CLRDATA_ADDRESS;`|Kullanılamaz|64 bitlik bir bellek adresi.|
|CONNıD|`typedef DWORD CONNID;`|CorDebug. h, mscoree. h|Bir Microsoft SQL Server örneğine bağlı bir iş parçacığının bağlantı tanımlayıcısı.|  
|ContextId|`typedef UINT_PTR ContextID;`|CorProf. h|Belirli bir yönetilen iş parçacığıyla ilişkili bağlamın tanımlayıcısı.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|CorProf. h|Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|CorProf. h|Yığın çerçevesini işaret eden donuk bir tanıtıcı. Yalnızca geçirildiği geri arama sırasında geçerlidir.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|CorDebug. h|Bellekteki bir adres.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|CorDebug. h|Devamlılık durumu.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|CorDebug. h|Bir CPU kayıt değeri.|
|FunctionID|`typedef UINT_PTR FunctionID;`|CorProf. h|Bir işlevin veya metodun tanımlayıcısı.|  
|Gchandlet kimliği|`typedef UINT_PTR GCHandleID;`|CorProf. h|Çöp toplama tutamacı.|  
|mdMethodDef|`typedef mdToken mdMethodDef;`|CorDebug. h|Yöntem tanımı belirteci.|
|mdToken|`typedef UINT32 mdToken;`|CorProf. h|Meta veri belirteci (meta veri tablosundaki bir satır).|  
|Modül kimliği|`typedef UINT_PTR ModuleID;`|CorProf. h|Bütünleştirilmiş kod modülünün tanımlayıcısı.|  
|ObjectID|`typedef UINT_PTR ObjectID;`|CorProf. h|Bir nesnenin tanımlayıcısı.|  
|PCCOR_SIGNATURE|`typedef SIZE_T PCCOR_SIGNATURE;`|CorDebug. h|Üye veya meta veri imzası işaretçisi.|
|ProcessID|`typedef UINT_PTR ProcessID;`|CorProf. h|Yönetilen bir işlemin tanımlayıcısı.|  
|ReJitId|`typedef UINT_PTR ReJITID;`|CorProf. h|Bir jderlenen işlevinin tanımlayıcısı.|  
|SIZE_T|`typedef ULONG_PTR SIZE_T;`|CorSym. h|64 bitlik bir bellek adresine yönelik bir işaretçi.|
|TASKıD|`typedef UINT64 TASKID;`|CorDebug. h, mscoree. h|[ICLRTask](./hosting/iclrtask-interface.md) örneğinin tanımlayıcısı.|  
|ThreadID|`typedef UINT_PTR ThreadID;`|CorProf. h|Yönetilen bir iş parçacığının tanımlayıcısı.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen API başvurusu](index.md)
