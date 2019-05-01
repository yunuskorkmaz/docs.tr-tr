---
title: Windows Communication Foundation İşlemleri Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 42276a9b450b6f0664901747239195ab13f7c44d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933659"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Windows Communication Foundation İşlemleri Genel Bakış
İşlem, bir dizi eylem veya işlemi tek bir bölünemez biriminde yürütme gruplamak için bir yol sağlar. Bir işlem, aşağıdaki özelliklere sahip işlemleri koleksiyonudur:  
  
- Özellik sağlar. Bu da tüm güncelleştirmeleri belirli bir işlem altında tamamlandı taahhüt verdiniz ve dayanıklı hale veya bunlar tüm durduruldu ve önceki durumlarına geri sağlar.  
  
- Tutarlılık. Bu, bir işlem altında yapılan değişiklikleri tutarlı bir durumdan diğerine dönüştürme temsil garanti eder. Örneğin, para tasarrufu hesabına denetleme hesabından aktaran bir işlem genel banka hesabı miktarda değiştirmez.  
  
- Yalıtım. Bu, diğer eş zamanlı işlem ait kaydedilmemiş değişiklikler gözleme gelen bir işlem engeller. Bir işlem sağlarken eşzamanlılık bir soyutlamasıdır üzerinde başka bir işlemin yürütülmesi beklenmeyen bir etkiye sahip olamaz yalıtım sağlar.  
  
- Dayanıklılık. Bu tamamlandıktan sonra yönetilen kaynaklara (örneğin, bir veritabanı kaydı) güncelleştirmeleri sorunla karşılaşıldığında kalıcı anlamına gelir.  
  
 Windows Communication Foundation (WCF) zengin bir Web hizmeti uygulamanızda dağıtılmış işlemler oluşturmanıza olanak sağlayan özellikler sunar.  
  
 WCF üçüncü taraf teknolojisi kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri gibi birlikte çalışabilen uygulamalar için akış işlem WCF uygulamaları etkinleştiren WS-AtomicTransaction (WS-AT) protokolü için destek uygular. WCF burada işlem akışını etkinleştirmek için birlikte çalışma işlevselliği gerekmez senaryolarda kullanılabilir OLE işlemlerin protokolü için desteği de uygular.  
  
 Uygulama yapılandırma dosyası, etkinleştirmek veya devre dışı işlem akışı yanı sıra, istenen işlem protokolünü üzerindeki bir bağlamaya ayarlamak için bağlamalar yapılandırmak için kullanabilirsiniz. Ayrıca, işlem zaman aşımlarını yapılandırma dosyası kullanarak hizmet düzeyinde ayarlayabilirsiniz. Daha fazla bilgi için [işlem akışını etkinleştirme](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 İşlem öznitelikleri içinde <xref:System.ServiceModel> ad alanı, aşağıdakileri yapmak izin ver:  
  
- İşlem zaman aşımları ve yalıtım düzeyi kullanılarak filtreleme yapılandırma <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği.  
  
- İşlem işlevselliğini etkinleştirmek ve işlem tamamlama davranışını kullanarak yapılandırma <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği.  
  
- Kullanım <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> gerektirecek şekilde bir sözleşme yöntemi özniteliklerinde veya işlem akışı engellediği.  
  
 Daha fazla bilgi için [ServiceModel işlem öznitelikleri](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel İşlem Öznitelikleri](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)
- [İşlem Akışını Etkinleştirme](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
