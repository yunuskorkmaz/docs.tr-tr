---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 2d1008a4308c9fda5d2291ce704d1f19205e996a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041261"
---
# <a name="transactionflow"></a>\<transactionFlow >
Özel bağlama için işlem akış desteğini belirtir.  
  
 \<system.serviceModel>  
\<bağlama >  
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
|transactionProtocol|Kullanılacak işlem protokolünü belirtir. Geçerli değerler şunlardır:<br /><br /> -OleTransactions<br />- WSAtomicTransactionOctober2004<br /><br /> Varsayılan değer OleTransactions 'dir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../misc/binding.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, bir uç noktanın bağlama ayarlarında gelen işlem akışını etkinleştirmenizi veya devre dışı bırakmanızı, ayrıca gelen işlemler için istenen protokol biçimini belirtmenizi sağlar. Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
> Uç noktadan uç `OleTransactions` noktaya işlem akışı yapmak için protokolü kullanırken, hedef uç noktası dışında `OleTransactions`herhangi bir protokolü kullanarak yeniden akışı denerse, işlem zaman aşımı kaybolabilir. Bu, OleTransactions atından sonra beklenden sonra zaman aşımına uğradıktan sonra tüm alt düzey düğümlerin oluşmasına neden olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [ServiceModel İşlem Yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [İşlem Akışını Etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
