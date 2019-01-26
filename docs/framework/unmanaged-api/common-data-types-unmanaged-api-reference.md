---
title: Ortak Veri Türleri (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98b83abce36b6e8a66ec3580af109b66b7ae09d8
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065836"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Ortak Veri Türleri (Yönetilmeyen API Başvurusu)
Bu konu yönetilmeyen API'ları tarafından kullanılan .NET Framework için C/C++ tarafından tanımlanan basit veri türleri listeler `typedef` deyimleri. Bu veri türleri, genellikle C/C++ ilkel veri türleri diğer adlarıdır. Genellikle, bu veri türlerinin donuk değerlerdir; Böylece diğer işlevleri veya yöntemleri yapmadan geçirilebilir diğer bir deyişle, bunlar belirli bir işlevi veya yöntemi tarafından döndürülür.  
  
|Veri türü|Tanım|İçinde tanımlanan|Açıklama|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|Uygulama etki alanı tanımlayıcısı.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|Bir derlemenin tanımlayıcı.|  
|Sınıf kimliği|`typedef UINT_PTR ClassID;`|corprof.h|Yönetilen bir sınıf tanımlayıcısı.|  
|CLRDATA_ADDRESS|`typedef ULONG64 CLRDATA_ADDRESS;`|clrdata.h|Bir 64-bit bellek adresi.|
|CLRDATA_ENUM|`typedef ULONG64 CLRDATA_ADDRESS;`|Kullanılabilir değil|Bir 64-bit bellek adresi.|
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|Microsoft SQL Server örneğine bağlı bir iş parçacığı için bağlantı kimliği.|  
|Contextıd|`typedef UINT_PTR ContextID;`|corprof.h|Belirli bir yönetilen iş parçacığı ile ilişkili Bağlam tanıtıcısı.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Belirli bir yığın çerçevesini ilgili bilgileri temsil eder bir donuk tanıtıcısı.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Bir opak, işaret ettiği bir yığın çerçevesine işleyin. Başarılı geri sırasında geçerli değil.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Bir bellek adresi.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|Devamlılık durumu.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|Bir CPU kayıt değeri.|
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|Bir işlev veya yöntem tanımlayıcısı.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Bir çöp toplama işleci.|  
|mdMethodDef|`typedef mdToken mdMethodDef;`|cordebug.h|Bir yöntemin tanımı belirteci.|
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Meta veri belirteci (meta veri tablosunda bir satıra).|  
|Modül kimliği|`typedef UINT_PTR ModuleID;`|corprof.h|Bir derleme modülü tanımlayıcısı.|  
|Nesne Kimliği|`typedef UINT_PTR ObjectID;`|corprof.h|Bir nesne tanımlayıcısı.|  
|ProcessID|`typedef UINT_PTR ProcessID;`|corprof.h|Yönetilen bir işlem tanımlayıcısı.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Jıtted işlevi tanımlayıcısı.|  
|TASKID|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|Tanımlayıcısını bir [Iclrtask](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.|  
|ThreadID|`typedef UINT_PTR ThreadID;`|corprof.h|Yönetilen iş parçacığı tanıtıcısı.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen API Başvurusu](../../../docs/framework/unmanaged-api/index.md)
