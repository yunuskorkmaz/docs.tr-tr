---
title: 'Öğretici: Windows Communication Foundation uygulamaları ile başlayın'
description: Bu öğreticiler WCF uygulamaları oluşturmak için bir giriş sağlar.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184118"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Öğretici: Windows Communication Foundation uygulamaları ile başlayın
Aşağıdaki öğreticiler serisi sizi Windows Communication Foundation (WCF) programlama deneyimiyle tanıştırır. Bu öğreticiler aracılığıyla çalışmak, WCF uygulamaları oluşturmak için gereken adımları anlamanızı sağlayacaktır. Bitirdikten sonra, çalışan bir WCF hizmetiniz ve hizmeti çağıran bir WCF istemciniz olur.

Öğretici, Visual Studio'yu geliştirme ortamı olarak kullandığınızı varsayar. Başka bir geliştirme ortamı kullanıyorsanız, Visual Studio'ya özgü yönergeleri yoksayın.

İndirebileceğiniz ve çalıştırabileceğiniz örnek WCF uygulamaları için [Windows Communication Foundation örneklerine](samples/index.md)bakın. Örneklere giriş için [bkz.](samples/getting-started-sample.md)

Hizmet ve istemci oluşturma hakkında daha ayrıntılı bilgi için [Temel WCF programlamaya](basic-wcf-programming.md)bakın.

## <a name="wcf-tutorials"></a>WCF eğitimleri

İlk üç öğretici, bir WCF hizmet sözleşmesinin nasıl tanımlanacağını, nasıl uygulanacağını ve nasıl barındırılabildiğini açıklar. Oluşturduğunuz hizmet, konsol uygulamasında kendi kendine barındırılır. Ayrıca, Microsoft Internet Information Services (IIS) altında da hizmetleri barındırabilirsiniz. Daha fazla bilgi için [bkz: IIS'de bir WCF Hizmeti barındırın.](feature-details/how-to-host-a-wcf-service-in-iis.md) Öğreticideki hizmeti yapılandırmak için kod kullanmanıza rağmen, bir yapılandırma dosyasındaki hizmetleri de [yapılandırabilirsiniz.](configuring-services-using-configuration-files.md)

- [Öğretici: Hizmet sözleşmesi tanımlama](how-to-define-a-wcf-service-contract.md)

    Kullanıcı tanımlı arabirimiçeren bir WCF sözleşmesi oluşturursunuz. Bu sözleşme, hizmetin ortaya çıkardığı işlevselliği tanımlar.

- [Öğretici: Bir hizmet sözleşmesi uygulayın](how-to-implement-a-wcf-contract.md)

    Bir sözleşme tanımladıktan sonra, bir hizmet sınıfı ile uygulamanız gerekir.

- [Öğretici: Ana bilgisayar ve temel bir hizmet çalıştırın](how-to-host-and-run-a-basic-wcf-service.md)

    Hizmet için bir bitiş noktası yapılandırın ve hizmeti bir konsol uygulamasında barındırın. Bir hizmetin etkin olabilmesi için, bir hizmetin çalışma zamanı ortamında yapılandırması ve barındırması gerekir. Bu çalışma zamanı ortamı hizmeti oluşturur ve içeriğini ve kullanım ömrünü denetler.

Sonraki iki öğretici, hizmetin ortaya çıkardığı işlemleri çağırmak için bir istemci uygulamasını nasıl oluşturup, yapılandıracak ve kullanacağınızı açıklar. Hizmetler, istemci uygulamasının hizmetle iletişim kurmak için ihtiyaç duyduğu bilgileri tanımlayan meta veriler yayımlar. Visual Studio bu meta verilere erişim işlemini otomatikleştirir ve hizmet için istemci uygulamasını oluşturmak için kullanır. Visual Studio'yu kullanmamaya karar verirseniz, bunun yerine [ServiceModel Metadata Utility aracını *(Svcutil.exe)*](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanabilirsiniz.

- [Öğretici: İstemci oluşturma](how-to-create-a-wcf-client.md)

    Bir WCF hizmetinden WCF istemci proxy'si oluşturmak için meta verileri alın. Bir hizmet başvurusu eklemek için Visual Studio'yu kullanarak meta verileri alırsınız veya ServiceModel Metadata Utility aracını kullanabilirsiniz. İstemcinin hizmete erişmek için kullandığı bitiş noktasını belirtirsiniz.

- [Öğretici: İstemci kullanma](how-to-use-a-wcf-client.md)

    Hizmet işlemlerini aramak için WCF istemci proxy'sini kullanın.

## <a name="reference"></a>Başvuru

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Ayrıca bkz.

- [Kavramsal genel bakış](conceptual-overview.md)
- [Dokümantasyon kılavuzu](guide-to-the-documentation.md)
- [Windows Communication Foundation nedir](whats-wcf.md)
- [WCF özellik ayrıntıları](feature-details/index.md)
- [Temel programlama yaşam döngüsü](basic-programming-lifecycle.md)
- [Müşteri oluşturma](building-clients.md)
- [Temel WCF programlama](basic-wcf-programming.md)
- [Nasıl?](feature-details/how-to-create-a-duplex-contract.md)
- [Nasıl yapilir: Çift yönlü sözleşmeyle hizmetlere erişin](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel Metadata Yardımcı araç (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Nasıl kullanılır: Meta veri belgelerini indirmek için Svcutil.exe'yi kullanın](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Nasıl kullanılır: Yapılandırma dosyasını kullanarak bir hizmet için meta veri yayımlama](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](using-bindings-to-configure-services-and-clients.md)
- [Başlatma örneği](samples/getting-started-sample.md)
- [Windows Communication Foundation örnekleri](samples/index.md)
- [Kendini Barındırma](samples/self-host.md)
