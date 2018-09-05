---
title: Tutorial1 Başlarken
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: e5a07e5264c715f568121403721a3c844b903d99
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553083"
---
# <a name="getting-started-tutorial"></a>Başlangıç Öğreticisi
Bu bölümdeki konular, hızlı Etkilenme programlama deneyimi Windows Communication Foundation (WCF) için size yöneliktir. Bu konu başlığının altındaki listenin sırasına göre tamamlanması için tasarlanmıştır. Bu öğreticide, WCF hizmeti ve istemci uygulamaları oluşturmak için gerekli adımlar tanıtıcı bir anlayış verir. Her biri bir veya daha fazla hizmet işlemlerini kullanıma sunan bir veya daha fazla uç noktaları, bir hizmet sunar. *Uç nokta* Hizmetin nerede hizmet bulunabilir, adres nasıl bir istemci hizmeti ve işlevselliği tanımlayan bir sözleşme ile iletişim kurması gereken açıklayan bilgileri içeren bir bağlama belirtir hizmet tarafından istemcilerine sağlanan.  
  
 Bu öğreticideki konu başlıklarını sırasıyla anlayıp uyguladıktan sonra çalışan bir hizmete ve hizmetini çağıran bir istemci sahip olacaktır. İlk üç konularda hizmeti barındırmak nasıl bir hizmet sözleşmesini tanımlama ve hizmet sözleşmesini uygulama konusunda açıklanmaktadır. Oluşturulan bir konsol uygulaması içinde şirket içinde barındırılan hizmetidir. Hizmetleri, Internet Information Services (IIS) altında da barındırılabilir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md). Hizmet kodu yapılandırılır; Ancak, hizmet yapılandırma dosyasının içinde yapılandırılabilir. Bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).  
  
 Sonraki üç konular istemci proxy oluşturmak, istemci uygulaması yapılandırma ve hizmet tarafından sunulan hizmet işlemi çağırmak için istemci proxy kullanmak nasıl açıklar. Hizmetleri, bir istemci uygulama hizmeti ile iletişim için gereken bilgileri tanımlayan meta verileri yayımlama. [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Bu meta verilere erişme işlemini otomatikleştirir ve oluşturmak ve hizmeti için istemci uygulamasını yapılandırmak için kullanır. Kullanmıyorsanız, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], kullanabileceğiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) yapılandırmak ve hizmeti için istemci uygulamasını yapılandırmak için.  
  
 Bu bölümdeki konular, tüm geliştirme ortamı olarak Visual Studio 2011 kullanmakta olduğunuz varsayılır. Başka bir geliştirme ortamı kullanıyorsanız, Visual Studio özel yönergeler yoksayın.  
  
> [!NOTE]
>  Çalıştırıyorsanız [!INCLUDE[wv](../../../includes/wv-md.md)] veya sonraki sürümlerinde Windows işletim sisteminin, başlamalıdır Visual Studio Başlat menüsüne giderek ve Visual Studio 2011 sağ tıklayarak ve seçerek **yönetici olarak çalıştır**. Her zaman Visual Studio 2011 sizin bir kısayol oluşturun, kısayol sağ tıklayın, özellikleri seçin, seçin yönetici olarak başlatmak için **Uyumluluk** sekmesini tıklatıp denetleyin **yöneticiolarakbuprogramıçalıştır** onay kutusu. Bu kısayol ile Visual Studio 2011 başlattığınızda, yönetici olarak her zaman çalışır.  
  
 Sabit diskinize indirilebilir ve çalıştırma, konularına bakın ve örnek uygulamalar için [Windows Communication Foundation örnekleri](https://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91). Bu konu bakın, özellikle de [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Hizmetler ve istemcileri oluşturma hakkında daha ayrıntılı bilgi için bkz: [temel WCF programlama](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 Bir kullanıcı tarafından tanımlanan arabirimi kullanarak bir WCF sözleşmesi oluşturmayı açıklar. Sözleşme hizmet tarafından sunulan işlevselliği tanımlar.  
  
 [Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 Bir hizmet sözleşmesini uygulama açıklar. Bir sözleşme tanımlayan eklendiğinde, bir hizmet sınıfı ile uygulanmalıdır.  
  
 [Nasıl yapılır: Temel Bir Hizmet Barındırma ve Çalıştırma](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 Kodda bir uç nokta hizmeti için yapılandırma ve hizmeti bir konsol uygulamasında nasıl açıklar. Etkin duruma gelmesi hizmet yapılandırılmalı ve çalışma zamanı ortamı içinde barındırılan. Bu ortam hizmeti oluşturur ve yaşam süresi ve bağlam denetler.  
  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 Bir WCF hizmetinden bir WCF istemci proxy oluşturmak için kullanılan meta verilerini almak nasıl açıklar. Bu işlem, Visual Studio 2011 Hizmet Başvurusu Ekle işlevini kullanır.  
  
 [Nasıl yapılır: İstemci Yapılandırma](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 Bir WCF yapılandırmayı açıklar istemci istemci yapılandırma gerektirir İstemcinin hizmete erişmek için kullandığı uç noktası belirtme.  
  
 [Nasıl yapılır: İstemci Kullanma](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 Hizmet işlemleri çağırmak için WCF istemci proxy kullanmayı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Communication Foundation Örnekleri](https://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [Temel Programlama Yaşam Döngüsü](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kavramsal Genel Bakış](../../../docs/framework/wcf/conceptual-overview.md)  
 [Belgeler için Kılavuz](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Windows Communication Foundation nedir?](../../../docs/framework/wcf/whats-wcf.md)  
 [WCF Özellik Ayrıntıları](../../../docs/framework/wcf/feature-details/index.md)
