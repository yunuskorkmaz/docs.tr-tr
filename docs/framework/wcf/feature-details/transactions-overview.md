---
title: Windows Communication Foundation İşlemleri Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: a8e3306612e016568ad7cfd5138ab538af771a17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585837"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Windows Communication Foundation İşlemleri Genel Bakış
İşlemler, bir dizi eylemin veya işlemin tek bir görünmeyen yürütme birimiyle gruplandırılmasına olanak sağlar. İşlem, aşağıdaki özelliklere sahip işlemler koleksiyonudur:  
  
- Kararlılık. Bu, belirli bir işlem altında tamamlanan tüm güncelleştirmelerin yapıldığından ve sürekli olarak yapıldığından ya da tümünün durdurulduğundan ve önceki durumlarına geri döndürüldüğünden emin olur.  
  
- Denetleme. Bu, bir işlem altında yapılan değişikliklerin, tutarlı bir durumdan diğerine dönüştürmeyi temsil eder. Örneğin, bir denetim hesabından tasarruf hesabına para aktaran bir işlem, genel banka hesabındaki para miktarını değiştirmez.  
  
- Yalıtım. Bu işlem, bir işlemin diğer eş zamanlı işlemlere ait kaydedilmemiş değişiklikleri gözlemmasını önler. Yalıtım bir eşzamanlılık soyutlaması sağlarken bir işlemin başka bir işlemin yürütülmesi üzerinde beklenmedik bir etkiye sahip olmamasını sağlar.  
  
- Lığının. Bu, bir kez kaydedildikten sonra yönetilen kaynaklardaki (veritabanı kaydı gibi) güncelleştirmelerin hatalara karşı kalıcı olacağı anlamına gelir.  
  
 Windows Communication Foundation (WCF), Web hizmeti uygulamanızda dağıtılmış işlemler oluşturmanızı sağlayan zengin bir özellik kümesi sağlar.  
  
 WCF, WCF uygulamalarının, üçüncü taraf teknoloji kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri gibi birlikte çalışabilme uygulamalarına işlem akışını sağlayan WS-AtomicTransaction (WS-AT) protokolü için destek uygular. WCF Ayrıca, işlem akışını etkinleştirmek için birlikte çalışma işlevselliğine gerek duymayan senaryolarda kullanılabilen OLE Transactions protokolü için destek uygular.  
  
 Bir uygulama yapılandırma dosyasını, işlem akışını etkinleştirmek veya devre dışı bırakmak için bağlamaları yapılandırmak ve bir bağlamada istenen işlem protokolünü ayarlamak için kullanabilirsiniz. Ayrıca, yapılandırma dosyasını kullanarak hizmet düzeyinde işlem zaman aşımlarını ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Işlem akışını etkinleştirme](enabling-transaction-flow.md).  
  
 Ad alanındaki işlem öznitelikleri <xref:System.ServiceModel> şunları yapmanıza izin verir:  
  
- Özniteliği kullanarak işlem zaman aşımları ve yalıtım düzeyinde filtreleme yapılandırın <xref:System.ServiceModel.ServiceBehaviorAttribute> .  
  
- İşlem işlevlerini etkinleştirin ve özniteliği kullanarak işlem tamamlama davranışını yapılandırın <xref:System.ServiceModel.OperationBehaviorAttribute> .  
  
- <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> İşlem akışına izin vermek veya reddetmek için bir sözleşme yönteminde ve özniteliklerini kullanın.  
  
 Daha fazla bilgi için bkz. [ServiceModel Işlem öznitelikleri](servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel İşlem Öznitelikleri](servicemodel-transaction-attributes.md)
- [İşlem Akışını Etkinleştirme](enabling-transaction-flow.md)
