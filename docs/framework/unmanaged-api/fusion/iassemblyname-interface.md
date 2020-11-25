---
title: IAssemblyName Arabirimi
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
ms.openlocfilehash: f6feed9f59715f9a2801cd3a2a99a087957d4377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715075"
---
# <a name="iassemblyname-interface"></a>IAssemblyName Arabirimi

Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](iassemblyname-clone-method.md)|Bu nesnenin basit bir kopyasını oluşturur `IAssemblyName` .|  
|[Finalize Metodu](iassemblyname-finalize-method.md)|Bu `IAssemblyName` nesnenin, yıkıcısı çağrılmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.|  
|[GetDisplayName Metodu](iassemblyname-getdisplayname-method.md)|Bu nesne tarafından başvurulan derlemenin okunabilir adını alır `IAssemblyName` .|  
|[GetName Yöntemi](iassemblyname-getname-method.md)|Bu nesnenin başvurduğu derlemenin basit, şifrelenmemiş adını alır `IAssemblyName` .|  
|[GetProperty yöntemi](iassemblyname-getproperty-method.md)|Belirtilen özelliğin başvurduğu özelliğe bir işaretçi alır `PropertyId` .|  
|[GetVersion Yöntemi](iassemblyname-getversion-method.md)|Bu nesne tarafından başvurulan derleme için sürüm bilgilerini alır `IAssemblyName` .|  
|[IsEqual Yöntemi](iassemblyname-isequal-method.md)|Belirtilen `IAssemblyName` `IAssemblyName` karşılaştırma bayraklarını temel alarak belirtilen bir nesnenin bu değere eşit olup olmadığını belirler.|  
|[SetProperty Yöntemi](iassemblyname-setproperty-method.md)|Belirtilen öğesinin başvurduğu özelliğin değerini ayarlar `PropertyId` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IAssemblyEnum Arabirimi](iassemblyenum-interface.md)
