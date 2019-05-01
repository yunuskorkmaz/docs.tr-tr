---
title: İşlem Özel Durumları
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936987"
---
# <a name="transaction-exceptions"></a>İşlem Özel Durumları
Bu konu, Windows Communication Foundation (WCF) işlem tarafından üretilen tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Meta verileri içeri aktarılan ilke bilgilerini, işlemler arasında TransactionProtocol için farklı değerler belirtir. Yalnızca bir tek TransactionProtocol her uç nokta için desteklenir.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Hizmetin InstanceContextMode değeri PerSession olmadığı sürece TransactionAutoComplete yanlış olamaz. Belirtilen sözleşme ve işlem uygulaması üzerinde bir hata bulundu.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete sadece TransactionAutoComplete false olarak ayarlanmış ve TransactionScopeRequired ayarlanmış bir işlemde çağrılabilir true. Bu geçersiz bir senaryodur ve geçerli işlem sonlandırıldı.|  
|TransactionFlowRequiredIssuedTokens|Bir işlem akmasına izin verilen belirteçler de desteklenmelidir.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Yapılandırılan Trust sürümü, verilen belirteçleri desteklemez. WSTrustFeb2005 kullanın veya üzeri.|
