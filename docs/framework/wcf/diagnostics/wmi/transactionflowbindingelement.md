---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 577502d1cd3d81784cb9b1eb3b249376b8ffa6b8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234901"
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement

TransactionFlowBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 TransactionFlowBindingElement sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="issuedtokens"></a>IssuedTokens  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Verilen bir güvenlik belirteçleri üst bilgisi için gereksinimi belirtir (WS-Trust ' den IssuedTokens).  
  
### <a name="transactionprotocol"></a>TransactionProtocol  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İşlemleri Flow için hizmet tarafından kullanılan işlemler protokolü.  
  
### <a name="transactions"></a>İşlemler  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Gelen işlemin desteklenip desteklenmediğini gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
