---
title: WS-AtomicTransaction Kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 124c5dc0f6db94ae459fe140bd7a4290aa56e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-ws-atomictransaction"></a>WS-AtomicTransaction Kullanma
WS-AtomicTransaction (WS-AT) bir birlikte çalışabilen işlem protokolüdür. Web hizmeti iletileri kullanarak dağıtılmış işlemler akış ve heterojen işlem altyapıları arasında birlikte çalışabilir bir şekilde koordine sağlar. WS-AT dağıtılmış uygulamalar, işlem yöneticileri ve kaynak yöneticileri arasında bir atomik sonucu sürücü için iki aşamalı yürütme protokolü kullanır.  
  
 WS-AT uygulama [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sağlayan Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlem Manager'a yerleşik bir protokolü hizmeti içerir. WS-AT kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları işlemleri üçüncü taraf teknolojisi kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri dahil olmak üzere diğer uygulamalar için akış.  
  
 İşlem bir istemci uygulaması ve bir sunucu uygulaması arasında akan, kullanılan işlem protokolü sunucunun seçili istemci uç noktada sunan bağlama tarafından belirlenir. Bazı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] belirtmek için sistem tarafından sağlanan bağlamalar varsayılan `OleTransactions` Protokolü başkalarının WS-AT belirtmek için varsayılan sırada işlem yayma biçimi olarak. Belirtilen bağlama içindeki işlem protokolü seçimi program aracılığıyla da değiştirebilirsiniz.  
  
 Protokol etkiler Seçimi:  
  
-   İstemciden sunucuya işlem akış için kullanılan ileti üstbilgilerini biçimi.  
  
-   İşlem sonucunu çözümlemek amacıyla sunucunun işlem istemcinin işlem yöneticisi arasında iki aşamalı yürütme Protokolü çalıştırmak için kullanılan ağ protokolü.  
  
 Sunucu ve istemci kullanılarak yazılan, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], WS-AT kullanmanız gerekmez. Bunun yerine, varsayılan ayarları kullanabilir `NetTcpBinding` ile `TransactionFlow` kullanacağı etkin öznitelik `OleTransactions` yerine protokol. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). Aksi takdirde, üçüncü taraf teknolojilerini yerleşik Web hizmetlerine işlemleri akan gerekiyorsa, WS-AT kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WS-Atomic İşlem Desteğini Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
