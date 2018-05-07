---
title: WS-AtomicTransaction Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 7880d46d4827b36c7806c61877edf79faa766371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-ws-atomictransaction"></a>WS-AtomicTransaction Kullanma
WS-AtomicTransaction (WS-AT) bir birlikte çalışabilen işlem protokolüdür. Web hizmeti iletileri kullanarak dağıtılmış işlemler akış ve heterojen işlem altyapıları arasında birlikte çalışabilir bir şekilde koordine sağlar. WS-AT dağıtılmış uygulamalar, işlem yöneticileri ve kaynak yöneticileri arasında bir atomik sonucu sürücü için iki aşamalı yürütme protokolü kullanır.  
  
 Windows Communication Foundation (WCF) sağlar WS-AT uygulanmasını Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlem Manager'a yerleşik bir protokolü hizmeti içerir. WS-AT kullanarak, üçüncü taraf teknolojisi kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri dahil olmak üzere diğer uygulamalara işlemleri WCF uygulamaları akabilir.  
  
 İşlem bir istemci uygulaması ve bir sunucu uygulaması arasında akan, kullanılan işlem protokolü sunucunun seçili istemci uç noktada sunan bağlama tarafından belirlenir. Belirtmek için bazı WCF sistem tarafından sağlanan bağlamalar varsayılan `OleTransactions` Protokolü başkalarının WS-AT belirtmek için varsayılan sırada işlem yayma biçimi olarak. Belirtilen bağlama içindeki işlem protokolü seçimi program aracılığıyla da değiştirebilirsiniz.  
  
 Protokol etkiler Seçimi:  
  
-   İstemciden sunucuya işlem akış için kullanılan ileti üstbilgilerini biçimi.  
  
-   İşlem sonucunu çözümlemek amacıyla sunucunun işlem istemcinin işlem yöneticisi arasında iki aşamalı yürütme Protokolü çalıştırmak için kullanılan ağ protokolü.  
  
 Sunucu ve istemci WCF kullanılarak yazılan, WS-AT kullanmak gerekmez. Bunun yerine, varsayılan ayarları kullanabilir `NetTcpBinding` ile `TransactionFlow` kullanacağı etkin öznitelik `OleTransactions` yerine protokol. Daha fazla bilgi için bkz: [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). Aksi takdirde, üçüncü taraf teknolojilerini yerleşik Web hizmetlerine işlemleri akan gerekiyorsa, WS-AT kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WS-Atomic İşlem Desteğini Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
