---
title: "Ortak Veri Türleri (Yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03350825b3de4515a0d30e8644f34df71efa25db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="common-data-types-unmanaged-api-reference"></a>Ortak Veri Türleri (Yönetilmeyen API Başvurusu)
Bu konu C/C++ tarafından tanımlanan tarafından yönetilmeyen API'ler .NET Framework kullanılan basit veri türleri listeler `typedef` deyimleri. Bu veri türleri genellikle C/C++ temel veri türleri için diğer adlardır. Genellikle, bu veri türlerinin donuk değerlerdir; Böylece diğer işlevleri veya değişiklik yapmadan yöntemleri geçirilebilir diğer bir deyişle, bunlar belirli işlev veya yöntem tarafından döndürülür.  
  
|Veri türü|Tanım|Tanımlanan|Açıklama|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|Uygulama etki alanı tanımlayıcısı.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|Bir derleme tanımlayıcı.|  
|ClassId|`typedef UINT_PTR ClassID;`|corprof.h|Yönetilen sınıf tanımlayıcısı.|  
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|Microsoft SQL Server örneğine bağlı bir iş parçacığı için bağlantı kimliği.|  
|İçeriği No|`typedef UINT_PTR ContextID;`|corprof.h|Belirli bir yönetilen iş parçacığı ile ilişkili Bağlam tanıtıcısı.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Belirli Yığın çerçevesi ilgili bilgileri temsil eder donuk işleci.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Bir opak işaret yığın çerçevesi için işler. Geçirilen yalnızca geri çağırma sırasında geçerli değil.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Bellekteki bir adresi.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|Devamlılık durumu.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|Bir CPU kayıt değeri.|  
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|Bir işlev veya yöntem tanımlayıcısı.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Çöp Toplama işleci.|  
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Meta veri simgesi (meta veri tablosunda bir satırı).|  
|Modül kimliği|`typedef UINT_PTR ModuleID;`|corprof.h|Bir derleme modülü tanımlayıcısı.|  
|ObjectID|`typedef UINT_PTR ObjectID;`|corprof.h|Bir nesne tanımlayıcısı.|  
|İşlem kimliği|`typedef UINT_PTR ProcessID;`|corprof.h|Yönetilen bir işlem tanıtıcısı.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Jitted işlevi tanımlayıcısı.|  
|TASKID|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|Tanıtıcısı bir [Iclrtask](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.|  
|ThreadID|`typedef UINT_PTR ThreadID;`|corprof.h|Yönetilen iş parçacığı tanımlayıcısı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen API Başvurusu](../../../docs/framework/unmanaged-api/index.md)
