---
title: "İşlem Özel Durumları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be53af47aef4d42ddd2c77fbd29c8c9e9961c47b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-exceptions"></a>İşlem Özel Durumları
Bu konu tarafından oluşturulan tüm özel durumları listeler [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] işlem.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Meta verilerini içeri aktarılmakta olan ilke bilgilerini işlemleri arasında TransactionProtocol için farklı değerler belirtir. Yalnızca bir tek TransactionProtocol her uç noktası için desteklenir.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Hizmetin InstanceContextMode değeri PerSession olmadıkça TransactionAutoComplete yanlış olamaz. Bir hata belirtilen sözleşme ve işlem uyarlamasını bulundu.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete yalnızca TransactionAutoComplete false olarak ayarlanmış ve TransactionScopeRequired özelliği doğru olarak ayarlanmış bir işlemde çağrılabilir true. Bu geçersiz bir senaryodur ve geçerli işlem sonlandırıldı.|  
|TransactionFlowRequiredIssuedTokens|Bir işlem akışı için verilen belirteçler de desteklenmesi gerekir.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Yapılandırılan güven sürümü verilen belirteçleri desteklemez. WSTrustFeb2005 kullanın veya üstü.|
