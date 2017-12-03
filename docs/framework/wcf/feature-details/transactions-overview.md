---
title: "Windows Communication Foundation İşlemleri Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 480c7ca971eeb7f232517057efe4033f177b26b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a>Windows Communication Foundation İşlemleri Genel Bakış
İşlemler eylemler veya tek bir bölünemez birime işlemleri yürütme kümesini gruplamak için bir yol sağlar. Bir işlem, aşağıdaki özelliklere sahip işlemleri koleksiyonudur:  
  
-   Atom oranı. Bu, belirli bir işlem altında tamamlandı güncelleştirmelerini kaydedilen ve dayanıklı hale ya da bunlar tüm durduruldu ve önceki durumlarına geri olduğunu sağlar.  
  
-   Tutarlılık. Bu, bir işlem altında yapılan değişiklikleri tutarlı bir durumdan diğerine dönüştürme temsil ettiğini garanti eder. Örneğin, para tasarrufu hesabına denetleme hesabından aktaran bir işlem genel banka hesabı para miktarını değiştirmez.  
  
-   Yalıtım. Bu, diğer eşzamanlı işlemler ait kaydedilmemiş değişiklikler Gözlemleme gelen bir işlem engeller. Bir işlem sağlarken eşzamanlılık bir soyutlamasını başka bir işlemin yürütülmesi beklenmeyen bir etkiye sahip olamaz, yalıtım da sağlar.  
  
-   Dayanıklılık. Bu tamamlandıktan sonra yönetilen kaynaklar (örneğin, bir veritabanı kaydını) güncelleştirmeleri hataları karşısında kalıcı olması anlamına gelir.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zengin bir Web hizmeti uygulamanız dağıtılmış işlemler oluşturmanıza olanak sağlayan özellikler kümesi sağlar.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]etkinleştirir WS-AtomicTransaction (WS-AT) protokolü için desteği uygulayan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar, üçüncü taraf teknolojisi kullanılarak oluşturulan birlikte çalışabilen Web Hizmetleri gibi birlikte çalışabilen uygulamaları akış işlemleri. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Ayrıca, burada işlem akışını etkinleştirmek için birlikte çalışma işlevselliği gerekmez senaryolarda kullanılabilir OLE hareketleri protokolü için desteği uygular.  
  
 Uygulama yapılandırma dosyası etkinleştirmek ya da işlem akışını devre dışı bırakmak, aynı zamanda bir bağlama üzerinde istenen işlem protokolü ayarlamak için bağlamalar yapılandırmak için kullanabilirsiniz. Ayrıca, yapılandırma dosyası kullanarak hizmet düzeyinde işlem zaman aşımlarını ayarlayabilirsiniz. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][İşlem akışını etkinleştirme](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 İşlem öznitelikleri <xref:System.ServiceModel> ad alanı, aşağıdakileri yapmak izin ver:  
  
-   İşlem zaman aşımlarını ve yalıtım düzeyi kullanılarak filtrelemeyi yapılandırmak <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği.  
  
-   İşlemler işlevselliğini etkinleştirmek ve işlem tamamlama davranışını kullanarak yapılandırma <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği.  
  
-   Kullanım <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> gerektirecek şekilde bir sözleşme yöntemi özniteliklerinde izin verin veya işlem akışını reddedin.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ServiceModel işlem öznitelikleri](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel işlem öznitelikleri](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [İşlem akışını etkinleştirme](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
