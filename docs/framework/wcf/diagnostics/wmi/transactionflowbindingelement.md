---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c65eb1689d1411cb9083967b9a29c946b7568b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 TransactionFlowBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 TransactionFlowBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="issuedtokens"></a>IssuedTokens  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Verilen güvenlik belirteçleri üstbilgisi (WS-Trust gelen IssuedTokens) gereksinimini belirtir.  
  
### <a name="transactionprotocol"></a>transactionProtocol  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Akış işlemleri için hizmet tarafından kullanılan işlemleri protokol.  
  
### <a name="transactions"></a>İşlemler  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Gelen işlemin desteklenip desteklenmediğini gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
