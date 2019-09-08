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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796557"
---
# <a name="iassemblyname-interface"></a>IAssemblyName Arabirimi
Bir derlemenin benzersiz kimliğini tanımlamak ve bunlarla çalışmak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](iassemblyname-clone-method.md)|Bu `IAssemblyName` nesnenin basit bir kopyasını oluşturur.|  
|[Finalize Yöntemi](iassemblyname-finalize-method.md)|Bu `IAssemblyName` nesnenin, yıkıcısı çağrılmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.|  
|[GetDisplayName Yöntemi](iassemblyname-getdisplayname-method.md)|Bu `IAssemblyName` nesne tarafından başvurulan derlemenin okunabilir adını alır.|  
|[GetName Yöntemi](iassemblyname-getname-method.md)|Bu `IAssemblyName` nesnenin başvurduğu derlemenin basit, şifrelenmemiş adını alır.|  
|[GetProperty Yöntemi](iassemblyname-getproperty-method.md)|Belirtilen `PropertyId`özelliğin başvurduğu özelliğe bir işaretçi alır.|  
|[GetVersion Yöntemi](iassemblyname-getversion-method.md)|Bu `IAssemblyName` nesne tarafından başvurulan derleme için sürüm bilgilerini alır.|  
|[IsEqual Yöntemi](iassemblyname-isequal-method.md)|Belirtilen karşılaştırma bayraklarını temel `IAssemblyName` alarak belirtilen bir nesnenin bu `IAssemblyName`değere eşit olup olmadığını belirler.|  
|[SetProperty Yöntemi](iassemblyname-setproperty-method.md)|Belirtilen `PropertyId`öğesinin başvurduğu özelliğin değerini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IAssemblyEnum Arabirimi](iassemblyenum-interface.md)
