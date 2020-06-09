---
title: WS-AtomicTransaction Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 71090efbb096bc3b7b3d6bcf40ff496b78ac6252
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600691"
---
# <a name="using-ws-atomictransaction"></a>WS-AtomicTransaction Kullanma
WS-AtomicTransaction (WS-AT), birlikte çalışabilen bir işlem protokolüdür. Web hizmeti iletilerini kullanarak dağıtılmış işlemleri Flow ve heterojen işlem altyapıları arasında birlikte çalışabilen bir şekilde koordine etmenize olanak sağlar. WS-AT, dağıtılmış uygulamalar, işlem yöneticileri ve kaynak yöneticileri arasında atomik bir sonucu sağlamak için iki aşamalı tamamlama protokolünü kullanır.  
  
 WS-AT uygulama Windows Communication Foundation (WCF), Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlem yöneticisi 'nde yerleşik olarak bulunan bir protokol hizmeti içerir. WS-AT kullanıldığında, WCF uygulamaları, üçüncü taraf teknoloji kullanılarak oluşturulan birlikte çalışabilen Web hizmetleri de dahil olmak üzere işlemleri diğer uygulamalara akabilir.  
  
 İstemci uygulaması ve sunucu uygulaması arasında bir işlem akışı yaparken kullanılan işlem protokolü, sunucunun seçilen uç noktada belirlediği bağlama tarafından belirlenir. Bazı WCF sistem tarafından sunulan bağlamalar `OleTransactions` , varsayılan olarak, varsayılan olarak ws-at belirtmek üzere protokol belirtmek için varsayılan olarak Protokolü işlem yayma biçimi olarak belirtmektir. Ayrıca, belirli bir bağlama içinde işlem protokolü seçimini programlı bir şekilde değiştirebilirsiniz.  
  
 Protokol seçimi şunları etkiler:  
  
- İşlemin istemciden sunucuya akışını sağlamak için kullanılan ileti üstbilgilerinin biçimi.  
  
- İşlemin sonucunu çözümlemek için istemcinin işlem yöneticisi ve sunucunun işlemi arasında iki aşamalı tamamlama protokolünü çalıştırmak için kullanılan ağ protokolü.  
  
 Sunucu ve istemci WCF kullanılarak yazılmışsa, WS-AT kullanmanız gerekmez. Bunun yerine, varsayılan ayarlarını, `NetTcpBinding` `TransactionFlow` özelliğini kullanacak olan özniteliğiyle birlikte kullanabilirsiniz `OleTransactions` . Daha fazla bilgi için bkz. [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md). Aksi halde, üçüncü taraf teknolojiler üzerinde oluşturulmuş Web Hizmetleri için işlem yapıyorsanız, WS-AT kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS-Atomic İşlem Desteğini Yapılandırma](configuring-ws-atomic-transaction-support.md)
