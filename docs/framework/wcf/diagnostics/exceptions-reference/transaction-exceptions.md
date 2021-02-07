---
description: 'Daha fazla bilgi edinin: Işlem özel durumları'
title: İşlem Özel Durumları
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: edea932ca12fcd05994c979555e7eb9c0d00e969
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686069"
---
# <a name="transaction-exceptions"></a>İşlem Özel Durumları

Bu konu, Windows Communication Foundation (WCF) Işlemi tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|Sfxcannothavefarklıenttransactionprotocolsinonebinding|Meta verilerden içeri aktarılan ilke bilgileri, işlemler arasında TransactionProtocol için farklı değerler belirtir. Her uç nokta için yalnızca tek bir TransactionProtocol desteklenir.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Hizmetin InstanceContextMode değeri PerSession olmadığı için TransactionAutoComplete yanlış olamaz. Belirtilen sözleşme ve işlem uygulamasında bir hata bulundu.|  
|Sfxtransactionınvalidsettransactiontamamlanmıştır|OperationContext. Settransactiontamamlanmıştır, yalnızca TransactionAutoComplete değeri false olarak ayarlandığında ve TransactionScopeRequired true olarak ayarlandığında bir işlemde çağrılabilir. Bu geçersiz bir senaryodur ve geçerli işlem sonlandırıldı.|  
|TransactionFlowRequiredIssuedTokens|Bir işlemi Flow için, akan verilen belirteçlerin de desteklenmelidir.|  
|Trustdriverversionmedinotsupportısedtokens|Yapılandırılan güven sürümü, verilen belirteçleri desteklemiyor. WSTrustFeb2005 veya üstünü kullanın.|
