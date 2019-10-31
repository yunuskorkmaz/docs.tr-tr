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
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134323"
---
# <a name="iassemblyname-interface"></a>IAssemblyName Arabirimi
Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](iassemblyname-clone-method.md)|Bu `IAssemblyName` nesnesinin basit bir kopyasını oluşturur.|  
|[Finalize Yöntemi](iassemblyname-finalize-method.md)|Bu `IAssemblyName` nesnesinin, yıkıcısı çağrılmadan önce kaynakları serbest bırakmasıyla ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.|  
|[GetDisplayName Yöntemi](iassemblyname-getdisplayname-method.md)|Bu `IAssemblyName` nesnesi tarafından başvurulan derlemenin okunabilir adını alır.|  
|[GetName Yöntemi](iassemblyname-getname-method.md)|Bu `IAssemblyName` nesnesi tarafından başvurulan derlemenin basit, şifrelenmemiş adını alır.|  
|[GetProperty Yöntemi](iassemblyname-getproperty-method.md)|Belirtilen `PropertyId`başvurduğu özelliğe bir işaretçi alır.|  
|[GetVersion Yöntemi](iassemblyname-getversion-method.md)|Bu `IAssemblyName` nesnesi tarafından başvurulan derleme için sürüm bilgilerini alır.|  
|[IsEqual Yöntemi](iassemblyname-isequal-method.md)|Belirtilen bir `IAssemblyName` nesnesinin, belirtilen karşılaştırma bayraklarını temel alarak bu `IAssemblyName`eşit olup olmadığını belirler.|  
|[SetProperty Yöntemi](iassemblyname-setproperty-method.md)|Belirtilen `PropertyId`başvurduğu özelliğin değerini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IAssemblyEnum Arabirimi](iassemblyenum-interface.md)
