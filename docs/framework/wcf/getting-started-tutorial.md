---
title: 'Öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama'
description: Bu öğreticiler WCF uygulamaları oluşturmaya yönelik bir giriş sağlar.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: d4613edefeb8db2c0d1e11e925f8ac41329efb0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929551"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama
Şu öğretici serisinde, Windows Communication Foundation (programlama deneyimi WCF için) sunar. Bu öğreticileri sırasıyla üzerinden geçmeden WCF uygulamaları oluşturmak için gerekli adımları tanıtıcı bir anlayış verir. İşlemi tamamladığınızda, çalışan bir WCF hizmeti ve hizmetini çağıran bir WCF istemcisi sahip olacaksınız. 

Bu öğretici, geliştirme ortamı olarak Visual Studio kullanıyorsanız varsayar. Başka bir geliştirme ortamı kullanıyorsanız, Visual Studio özgü yönergeleri yoksayın. 

İndirip çalıştırabileceğiniz örnek WCF uygulamalar için bkz: [Windows Communication Foundation örnekleri](samples/index.md). Örnekleri bir giriş için bkz [Başlarken örnek](samples/getting-started-sample.md).

Hizmetler ve istemcileri oluşturma hakkında daha ayrıntılı bilgi için bkz: [temel WCF programlama](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>WCF öğreticiler

İlk üç öğretici, bir WCF hizmet sözleşmesini tanımlama, nasıl ve sitemi barındırmak nasıl açıklanmaktadır. Oluşturduğunuz bir konsol uygulaması içinde şirket içinde barındırılan hizmetidir. Ayrıca Microsoft Internet Information Services (IIS) altında Hizmetleri barındırabilir. Daha fazla bilgi için [nasıl yapılır: IIS'de WCF Hizmeti barındırma](feature-details/how-to-host-a-wcf-service-in-iis.md). Öğreticide hizmeti yapılandırmak için kod kullansa da, ayrıca [hizmetlerini yapılandırma dosyasındaki yapılandırma](configuring-services-using-configuration-files.md). 

- [Öğretici: Bir hizmet sözleşmesini tanımlama](how-to-define-a-wcf-service-contract.md)

    Kullanıcı tanımlı bir arabirimle'de bir WCF sözleşmesi oluşturun. Bu sözleşme hizmet sunan işlevleri tanımlar.

- [Öğretici: Bir hizmet sözleşmesini uygulama](how-to-implement-a-wcf-contract.md)

    Bir sözleşme tanımladıktan sonra bir hizmet sınıfı ile uygulamanız gerekir.

- [Öğretici: Temel hizmet barındırma ve çalıştırma](how-to-host-and-run-a-basic-wcf-service.md)

    Hizmet için bir uç noktasını yapılandırın ve hizmeti bir konsol uygulamasında barındırın. Bir hizmeti etkin duruma gelmesi bir çalışma zamanı ortamında ana ve yapılandırmanız gerekir. Bu çalışma zamanı ortamının hizmeti oluşturur ve yaşam süresi ve bağlam denetler.

Sonraki iki öğreticiler açıklayan oluşturma, yapılandırma ve kullanım hizmeti işlemleri çağırmak için bir istemci uygulaması kullanıma sunar. Hizmetleri, bir istemci uygulama hizmeti ile iletişim için gereken bilgileri tanımlayan meta verileri yayımlama. Visual Studio bu meta verilere erişme işlemini otomatikleştiren ve hizmeti için istemci uygulaması oluşturmak için kullanır. Visual Studio kullanmamaya karar verirseniz, kullanabileceğiniz [ServiceModel meta veri yardımcı programracı (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) yerine.

- [Öğretici: Bir istemci oluşturma](how-to-create-a-wcf-client.md)

    Bir WCF hizmetinden WCF istemci proxy oluşturma için meta verileri alır. Bir hizmet başvurusu eklemek için Visual Studio kullanarak meta verilerini almak veya ServiceModel meta veri yardımcı programracı kullanabilirsiniz. İstemcinin hizmete erişmek için kullandığı uç noktası belirtin.

- [Öğretici: Bir istemci kullanın](how-to-use-a-wcf-client.md)

    WCF istemci proxy hizmet işlemlerini aramak üzere kullanın.

## <a name="reference"></a>Başvuru

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Ayrıca bkz.

- [Kavramsal genel bakış](conceptual-overview.md)
- [Belgeler için kılavuz](guide-to-the-documentation.md)
- [Windows Communication Foundation nedir](whats-wcf.md)
- [WCF özellik ayrıntıları](feature-details/index.md)
- [Temel programlama yaşam döngüsü](basic-programming-lifecycle.md)
- [İstemci derleme](building-clients.md)
- [Temel WCF programlama](basic-wcf-programming.md)
- [Nasıl yapılır: Çift yönlü sözleşme oluşturma](feature-details/how-to-create-a-duplex-contract.md)
- [Nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişim](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel meta veri yardımcı programracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Nasıl yapılır: Meta veri belgelerini indirmek için svcutil.exe kullanma](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma](using-bindings-to-configure-services-and-clients.md)
- [Başlarken örneği](samples/getting-started-sample.md)
- [Windows Communication Foundation örnekleri](samples/index.md)
- [Kendini Barındırma](samples/self-host.md)
