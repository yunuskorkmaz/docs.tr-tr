---
title: Windows Communication Foundation İşlemleri Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 63f3826215f24a4bab6d84709c2f9da6a9c8f4f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498562"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Windows Communication Foundation İşlemleri Genel Bakış
İşlemler eylemler veya tek bir bölünemez birime işlemleri yürütme kümesini gruplamak için bir yol sağlar. Bir işlem, aşağıdaki özelliklere sahip işlemleri koleksiyonudur:  
  
-   Atom oranı. Bu, belirli bir işlem altında tamamlandı güncelleştirmelerini kaydedilen ve dayanıklı hale ya da bunlar tüm durduruldu ve önceki durumlarına geri olduğunu sağlar.  
  
-   Tutarlılık. Bu, bir işlem altında yapılan değişiklikleri tutarlı bir durumdan diğerine dönüştürme temsil ettiğini garanti eder. Örneğin, para tasarrufu hesabına denetleme hesabından aktaran bir işlem genel banka hesabı para miktarını değiştirmez.  
  
-   Yalıtım. Bu, diğer eşzamanlı işlemler ait kaydedilmemiş değişiklikler Gözlemleme gelen bir işlem engeller. Bir işlem sağlarken eşzamanlılık bir soyutlamasını başka bir işlemin yürütülmesi beklenmeyen bir etkiye sahip olamaz, yalıtım da sağlar.  
  
-   Dayanıklılık. Bu tamamlandıktan sonra yönetilen kaynaklar (örneğin, bir veritabanı kaydını) güncelleştirmeleri hataları karşısında kalıcı olması anlamına gelir.  
  
 Windows Communication Foundation (WCF) zengin bir Web hizmeti uygulamanız dağıtılmış işlemler oluşturmanıza olanak sağlayan özellikler kümesi sağlar.  
  
 WCF akışı işlemleri, üçüncü taraf teknolojisi kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri gibi birlikte çalışabilen uygulamaları WCF uygulamaları etkinleştirir WS-AtomicTransaction (WS-AT) protokolü için destek uygular. WCF da burada işlem akışını etkinleştirmek için birlikte çalışma işlevselliği gerekmez senaryolarda kullanılabilir OLE hareketleri protokolü için destek uygular.  
  
 Uygulama yapılandırma dosyası etkinleştirmek ya da işlem akışını devre dışı bırakmak, aynı zamanda bir bağlama üzerinde istenen işlem protokolü ayarlamak için bağlamalar yapılandırmak için kullanabilirsiniz. Ayrıca, yapılandırma dosyası kullanarak hizmet düzeyinde işlem zaman aşımlarını ayarlayabilirsiniz. Daha fazla bilgi için bkz: [işlem akışını etkinleştirme](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 İşlem öznitelikleri <xref:System.ServiceModel> ad alanı, aşağıdakileri yapmak izin ver:  
  
-   İşlem zaman aşımlarını ve yalıtım düzeyi kullanılarak filtrelemeyi yapılandırmak <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği.  
  
-   İşlemler işlevselliğini etkinleştirmek ve işlem tamamlama davranışını kullanarak yapılandırma <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği.  
  
-   Kullanım <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> gerektirecek şekilde bir sözleşme yöntemi özniteliklerinde izin verin veya işlem akışını reddedin.  
  
 Daha fazla bilgi için bkz: [ServiceModel işlem öznitelikleri](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel İşlem Öznitelikleri](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [İşlem Akışını Etkinleştirme](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
