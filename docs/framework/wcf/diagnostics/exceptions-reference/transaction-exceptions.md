---
title: İşlem Özel Durumları
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-exceptions"></a>İşlem Özel Durumları
Bu konu, Windows Communication Foundation (WCF) işlem tarafından üretilen tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Meta verilerini içeri aktarılmakta olan ilke bilgilerini işlemleri arasında TransactionProtocol için farklı değerler belirtir. Yalnızca bir tek TransactionProtocol her uç noktası için desteklenir.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Hizmetin InstanceContextMode değeri PerSession olmadıkça TransactionAutoComplete yanlış olamaz. Bir hata belirtilen sözleşme ve işlem uyarlamasını bulundu.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete yalnızca TransactionAutoComplete false olarak ayarlanmış ve TransactionScopeRequired özelliği doğru olarak ayarlanmış bir işlemde çağrılabilir true. Bu geçersiz bir senaryodur ve geçerli işlem sonlandırıldı.|  
|TransactionFlowRequiredIssuedTokens|Bir işlem akışı için verilen belirteçler de desteklenmesi gerekir.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Yapılandırılan güven sürümü verilen belirteçleri desteklemez. WSTrustFeb2005 kullanın veya üstü.|
