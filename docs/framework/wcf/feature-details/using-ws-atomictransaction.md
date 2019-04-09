---
title: WS-AtomicTransaction Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 8a8265873e4287e1455659aa4d9fae7e1d570a00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165508"
---
# <a name="using-ws-atomictransaction"></a>WS-AtomicTransaction Kullanma
WS-AtomicTransaction (WS-AT) bir birlikte çalışabilen işlem protokolüdür. Web hizmeti iletileri kullanarak dağıtılmış işlemler akış ve birlikte çalışabilen bir biçimde heterojen işlem altyapılar arasında koordine olanak tanır. WS-AT arasında dağıtılmış uygulamalar, işlem yöneticileri ve kaynak yöneticileri sonucu atomik sürücü için iki aşamalı tamamlama protokolü kullanır.  
  
 Windows Communication Foundation (WCF) sağlar WS-AT uygulanmasını Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) hareket yöneticisi ile oluşturulmuş bir protokolü hizmeti içerir. WCF uygulamaları WS-AT kullanarak, üçüncü taraf teknolojisi kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri gibi diğer uygulamaları hareketleri akabilir.  
  
 Bir istemci uygulaması ve bir sunucu uygulaması arasında bir işlem zaman, kullanılan işlem protokolü sunucu seçilen istemci uç noktada sunan bağlama tarafından belirlenir. Belirleme için bazı WCF sistem tarafından sağlanan bağlamalar varsayılan `OleTransactions` protokolü olarak ederken diğerleri WS-AT belirtmeye varsayılan işlem yayma biçimi. Verilen bağlama içindeki işlem protokolü, tercih ettiğiniz programlama yoluyla da değiştirebilirsiniz.  
  
 Protokol etkiler Seçimi:  
  
-   İstemciden sunucuya işlem akışı için kullanılan ileti üstbilgilerini biçimi.  
  
-   Hareketin sonucu çözmek için iki aşamalı tamamlama protokolü işlem yöneticisi istemcinin ve sunucunun işlem arasında çalıştırmak için kullanılan ağ protokolüdür.  
  
 WCF kullanarak sunucu ve istemci yazılır, WS-AT kullanmanız gerekmez. Bunun yerine, varsayılan ayarları kullanabilirsiniz `NetTcpBinding` ile `TransactionFlow` kullanacağı etkin, öznitelik `OleTransactions` yerine protokol. Daha fazla bilgi için [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). Aksi takdirde, Web Hizmetleri, üçüncü taraf teknolojileri üzerine kurulmuş hareketleri akışa alındığından, WS-AT kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS-Atomic İşlem Desteğini Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
