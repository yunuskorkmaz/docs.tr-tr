---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 334bab97a04ed464dce6944692b04a9ed1295296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613835"
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior
MustUnderstandBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 MustUnderstandBehavior sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 MustUnderstandBehavior sınıfı şu özelliğe sahip:  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Zaman `true`, tüm SOAP başlıkları `MustUnderstand` değil işlenir özniteliği bir özel durum davranışını neden.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
