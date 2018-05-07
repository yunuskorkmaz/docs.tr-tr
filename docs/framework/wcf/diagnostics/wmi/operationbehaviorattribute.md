---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 4f731d146885265d9f956c182f1bebdba5db924b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 OperationBehaviorAttribute sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Parametreler için otomatik dispose özellik durumu.  
  
### <a name="impersonation"></a>Kimliğe bürünme  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İşlemin desteklediği arayan kimliğe bürünme düzeyini gösterir.  
  
### <a name="releaseinstancemode"></a>OperationBehaviorAttribute üstündeki ReleaseInstanceMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Nesne geri dönüştürmek için bir işlemi başlatılması sırasında gösterir.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 İşlenmeyen özel durumlar oluşursa geçerli işlem otomatik olarak gerçekleştirmeyi gösterir.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 İşlemi bir işlem gerekli olup olmadığını gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
