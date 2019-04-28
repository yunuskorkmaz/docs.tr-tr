---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641690"
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 TransactionFlowBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="issuedtokens"></a>IssuedTokens  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Verilen güvenlik belirteçleri başlığı (WS-Trust gelen IssuedTokens) için gereksinim belirtir.  
  
### <a name="transactionprotocol"></a>transactionProtocol  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İşlem akış işlem hizmeti tarafından kullanılan protokol.  
  
### <a name="transactions"></a>İşlemler  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Gelen işlem desteklenip desteklenmediğini gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
