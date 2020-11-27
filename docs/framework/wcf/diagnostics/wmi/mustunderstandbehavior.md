---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 9cac7192d5c34de55fe0bd6a4921a41387e985f8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250443"
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior

MustUnderstandBehavior  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 MustUnderstandBehavior sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 MustUnderstandBehavior sınıfı aşağıdaki özelliğe sahiptir:  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Ne zaman `true` , işlenmemelidir özniteliği olan tüm soap üstbilgileri `MustUnderstand` davranışın özel durum oluşturmasına neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
