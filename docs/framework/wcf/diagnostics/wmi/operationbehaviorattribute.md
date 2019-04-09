---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 79601308c66abe43dd5a7f72bd2a05b9d2346c2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115810"
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 OperationBehaviorAttribute sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Parametreler için dispose otomatik özellik durumu.  
  
### <a name="impersonation"></a>Kimliğe bürünme  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Destekleyen işlemi çağıranın kimliğe bürünme düzeyini gösterir.  
  
### <a name="releaseinstancemode"></a>OperationBehaviorAttribute üstündeki ReleaseInstanceMode  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Nesne geri dönüştürmek için bir işlemi başlatılması sırasında gösterir.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 İşlenmeyen özel durumlar oluşursa otomatik olarak geçerli hareketi tamamlamak görüntülenip görüntülenmeyeceğini gösterir.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 İşlemi bir işlem gerekli olup olmadığını gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationBehaviorAttribute>
