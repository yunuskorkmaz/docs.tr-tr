---
title: '&lt;transactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: d8597a71a9b7afadba7565290085f491052e04d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622137"
---
# <a name="lttransactionflowgt"></a>&lt;transactionFlow&gt;
Özel bağlama için işlem akış desteğini belirler.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<transactionFlow >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|transactionProtocol|Kullanılacak işlem protokolünü belirler. Geçerli değerler şunlardır:<br /><br /> -OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> OleTransactions varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, etkinleştirme veya devre dışı gelen işlem akışı uç noktanın bağlama ayarları'nda, aynı zamanda gelen işlemler için istenen protokole biçimini belirtmek için sağlar. Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz. [ServiceModel işlem Yapılandırması](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
>  Kullanırken `OleTransactions` akış işlemleri için uç nokta endpoint protokol, hedef uç nokta yeniden dışında herhangi bir protokol kullanarak akış çalışırsa işlem zaman aşımı kaybolabilir `OleTransactions`. Bu, OleTransactions atlama sonra zaman aşımına beklenenden daha sonra tüm alt düzey düğümleri neden olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [ServiceModel İşlem Yapılandırması](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [İşlem Akışını Etkinleştirme](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
