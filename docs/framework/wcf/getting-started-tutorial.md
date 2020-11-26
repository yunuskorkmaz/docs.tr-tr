---
title: 'Öğretici: Windows Communication Foundation uygulamaları kullanmaya başlama'
description: Bu öğreticiler, WCF uygulamaları oluşturmaya yönelik bir giriş sağlar.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 620a83260f01e27a19b19227165695a621c88e5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238242"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Öğretici: Windows Communication Foundation uygulamaları kullanmaya başlama

Aşağıdaki öğretici dizisi sizi Windows Communication Foundation (WCF) programlama deneyimine tanıtmaktadır. Bu öğreticilerde sırayla çalışmak, WCF uygulamaları oluşturmak için gereken adımlara ilişkin açıklayıcı bir fikir verecektir. Bitirdiğinizde, çalışan bir WCF hizmeti ve hizmeti çağıran bir WCF istemcisi vardır.

Öğretici, Visual Studio 'Yu geliştirme ortamı olarak kullandığınızı varsayar. Başka bir geliştirme ortamı kullanıyorsanız, Visual Studio 'Ya özgü yönergeleri yoksayın.

İndirebileceğiniz ve çalıştırabileceğiniz örnek WCF uygulamaları için bkz. [Windows Communication Foundation Örnekleri](samples/index.md). Örneklere giriş için bkz. Başlarken [örneği](samples/getting-started-sample.md).

Hizmet ve istemci oluşturma hakkında daha ayrıntılı bilgi için bkz. [Temel WCF programlama](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>WCF öğreticileri

İlk üç öğretici, bir WCF hizmeti sözleşmesinin nasıl tanımlanacağını, nasıl uygulanacağını ve nasıl barındıralınacağını açıklamaktadır. Oluşturduğunuz hizmet, bir konsol uygulaması içinde kendiliğinden barındırılır. Ayrıca, Hizmetleri Microsoft Internet Information Services (IIS) altında de barındırabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de WCF hizmeti barındırma](feature-details/how-to-host-a-wcf-service-in-iis.md). Öğreticide hizmeti yapılandırmak için kod kullanıyor olsanız da, [bir yapılandırma dosyası içinde hizmetleri de yapılandırabilirsiniz](configuring-services-using-configuration-files.md).

- [Öğretici: hizmet sözleşmesi tanımlama](how-to-define-a-wcf-service-contract.md)

    Kullanıcı tanımlı arabirimle bir WCF sözleşmesi oluşturursunuz. Bu sözleşme, hizmetin sunduğu işlevselliği tanımlar.

- [Öğretici: hizmet sözleşmesini uygulama](how-to-implement-a-wcf-contract.md)

    Bir sözleşmeyi tanımladıktan sonra, bir hizmet sınıfıyla uygulamanız gerekir.

- [Öğretici: temel bir hizmet barındırma ve çalıştırma](how-to-host-and-run-a-basic-wcf-service.md)

    Hizmet için bir uç nokta yapılandırın ve hizmeti bir konsol uygulamasında barındırın. Bir hizmetin etkin hale gelmesi için, onu yapılandırmanız ve bir çalışma zamanı ortamında barındırmalısınız. Bu çalışma zamanı ortamı, hizmeti oluşturur ve bağlamını ve ömrünü denetler.

Sonraki iki öğreticinin, hizmetin sunduğu işlemleri çağırmak için bir istemci uygulaması oluşturma, yapılandırma ve kullanma açıklanır. Hizmetler, bir istemci uygulamasının hizmetle iletişim kurması için gereken bilgileri tanımlayan meta verileri yayımlar. Visual Studio, bu meta verilere erişme sürecini otomatikleştirir ve hizmet için istemci uygulaması oluşturmak üzere onu kullanır. Visual Studio 'Yu kullanmamaya karar verirseniz, bunun yerine [ServiceModel meta veri yardımcı programı aracını (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanabilirsiniz.

- [Öğretici: istemci oluşturma](how-to-create-a-wcf-client.md)

    WCF hizmetinden bir WCF istemci proxy 'si oluşturmak için meta verileri alın. Bir hizmet başvurusu eklemek için Visual Studio 'Yu kullanarak meta verileri alır veya ServiceModel meta veri yardımcı programı aracını kullanabilirsiniz. İstemcinin hizmete erişmek için kullandığı uç noktayı belirtirsiniz.

- [Öğretici: istemci kullanma](how-to-use-a-wcf-client.md)

    Hizmet işlemlerini çağırmak için WCF istemci proxy 'sini kullanın.

## <a name="reference"></a>Başvuru

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Ayrıca bkz.

- [Kavramsal genel bakış](conceptual-overview.md)
- [Belge Kılavuzu](guide-to-the-documentation.md)
- [Windows Communication Foundation nedir?](whats-wcf.md)
- [WCF özellik ayrıntıları](feature-details/index.md)
- [Temel programlama yaşam döngüsü](basic-programming-lifecycle.md)
- [İstemcileri derleme](building-clients.md)
- [Temel WCF programlama](basic-wcf-programming.md)
- [Nasıl yapılır: çift yönlü sözleşme oluşturma](feature-details/how-to-create-a-duplex-contract.md)
- [Nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Nasıl yapılır: meta veri belgelerini indirmek için Svcutil.exe kullanma](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](using-bindings-to-configure-services-and-clients.md)
- [Başlangıç örneği](samples/getting-started-sample.md)
- [Windows Communication Foundation Örnekleri](samples/index.md)
- [Kendini Barındırma](samples/self-host.md)
