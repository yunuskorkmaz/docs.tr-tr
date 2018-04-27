---
title: Tutorial1 Başlarken
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c66e7d8f610126e2702a6c593a93ee496108ecf
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="getting-started-tutorial"></a>Başlangıç Öğreticisi
Bu bölümdeki konularda hızlı maruz sağlamak için tasarlanmıştır [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] programlama deneyimine. Bu konunun sonundaki listesi sırasına göre tamamlanması için tasarlanmıştır. Bu öğreticide, bir giriş anlayış oluşturmak için gerekli adımları verir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet ve istemci uygulamaları. Bir hizmet bir veya daha fazla uç noktalar, her biri bir veya daha fazla hizmet işlemini kullanıma sunar, kullanıma sunar. *Endpoint* Hizmetin nerede hizmet bulunabilir, bir adresi nasıl bir istemci hizmeti ve işlevselliği tanımlayan bir sözleşme ile iletişim kurması gereken açıklayan bilgileri içeren bir bağlama belirtir hizmet tarafından istemcilerine sağlanan.  
  
 Bu öğreticideki konu başlıklarını sırasıyla çalıştıktan sonra çalışan bir hizmetiniz ve hizmetin çağıran bir istemci sahip olacaktır. İlk üç konularda bir hizmet sözleşmesini tanımlama, hizmet sözleşmesini uygulama ve hizmet barındırmak nasıl açıklanmaktadır. Oluşturulan hizmet bir konsol uygulaması içinde kendiliğinden barındırılır. Hizmetler, aynı zamanda Internet Information Services (IIS) altında barındırılabilir. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Bunu yapmak için bkz: nasıl [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md). Kod içinde hizmet yapılandırılan; Ancak, hizmetleri yapılandırma dosyasının içinde yapılandırılabilir. [!INCLUDE[crabout](../../../includes/crabout-md.md)] bir yapılandırma dosyası kullanarak bkz [yapılandırma dosyalarını kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).  
  
 Sonraki üç konuları, istemci proxy oluşturma, istemci uygulaması yapılandırın ve hizmeti tarafından sunulan hizmet işlemini çağırmak için istemci proxy kullanma açıklanmaktadır. Hizmetleri hizmeti ile iletişim için bir istemci uygulaması gereken bilgileri tanımlayan meta veri yayımlama. [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Bu meta verilere erişme işlemini otomatikleştiren ve oluşturmak ve hizmeti için istemci uygulamasını yapılandırmak için kullanır. Kullanmıyorsanız, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], kullanabileceğiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak ve hizmeti için istemci uygulaması yapılandırın.  
  
 Tüm bu bölümdeki konular geliştirme ortamı olarak Visual Studio 2011 kullandığınız varsayılır. Başka bir geliştirme ortamını kullanıyorsanız, Visual Studio özel yönergeler yoksay.  
  
> [!NOTE]
>  Çalıştırıyorsanız, [!INCLUDE[wv](../../../includes/wv-md.md)] veya Windows işletim sisteminin sonraki sürümlerini, size başlamalı Visual Studio Başlat menüsüne giderek ve Visual Studio 2011 sağ tıklayarak ve seçme **yönetici olarak çalıştır**. Her zaman, bir kısayol oluşturun, kısa kesme sağ tıklayın, seçin özellikleri, bir yönetici olarak Visual Studio 2011 başlatmak için **Uyumluluk** sekmesini tıklatın ve denetleme **yöneticiolarakbuprogramıçalıştır** onay kutusu. Visual Studio 2011 bu kısayol ile başlattığınızda, her zaman yönetici olarak çalıştırılır.  
  
 Sabit diskinize indirilebilir ve çalıştırmak, konulara bakın örnek uygulamaları için [Windows Communication Foundation örnekleri](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91). Bu konu, bakın, özellikle için [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Hizmetler ve istemcileri oluşturma hakkında daha ayrıntılı bilgi için bkz: [temel WCF programlama](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 Nasıl oluşturulacağını açıklar bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kullanıcı tanımlı bir arabirimini kullanarak sözleşme. Sözleşme hizmeti tarafından kullanıma sunulan işlevsellikten tanımlar.  
  
 [Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 Bir hizmet sözleşmesini uygulama açıklar. Bir sözleşme tanımlama eklendiğinde, bir hizmet sınıfıyla uygulanmalıdır.  
  
 [Nasıl yapılır: Temel Bir Hizmet Barındırma ve Çalıştırma](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 Kod içinde hizmet için bir uç nokta yapılandırın ve hizmeti bir konsol uygulamasında barındırma açıklar. Etkin hale gelmesi bir hizmet yapılandırılmalı ve çalışma zamanı ortamı içinde barındırılan. Bu ortam hizmeti oluşturur ve yaşam süresi ve bağlam denetler.  
  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 Oluşturmak için kullanılan meta verilerini almak açıklar bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci proxy sunucudan bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet. Bu işlem, Visual Studio 2011 Hizmet Başvurusu Ekle işlevini kullanır.  
  
 [Nasıl yapılır: İstemci Yapılandırma](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 Bir WCF yapılandırmayı açıklar istemcisi istemci yapılandırma gerektirir İstemcinin hizmete erişmek için kullandığı uç noktası belirtme.  
  
 [Nasıl yapılır: İstemci Kullanma](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 Nasıl kullanılacağını açıklar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci proxy hizmet işlemlerini çağırma.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Communication Foundation Örnekleri](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [Temel Programlama Yaşam Döngüsü](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kavramsal Genel Bakış](../../../docs/framework/wcf/conceptual-overview.md)  
 [Belgeler için Kılavuz](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Windows Communication Foundation nedir?](../../../docs/framework/wcf/whats-wcf.md)  
 [WCF Özellik Ayrıntıları](../../../docs/framework/wcf/feature-details/index.md)
