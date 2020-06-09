---
title: 'Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593522"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler

Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur. Uç noktalar, istemcilere bir WCF hizmeti tarafından sunulan işlevlere erişim sağlar.

Her uç nokta dört özelliklerden oluşur:

- Uç noktanın nerede bulunamayacağını gösteren bir adres.

- Bir istemcinin bitiş noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama.

- Kullanılabilir işlemleri tanımlayan bir anlaşma.

- Uç noktanın yerel uygulama ayrıntılarını belirten davranışlar kümesi.

Bu konu, bu uç nokta yapısını tartışır ve WCF nesne modelinde nasıl temsil edileceğini açıklar.

## <a name="the-structure-of-an-endpoint"></a>Bir uç noktanın yapısı

Her uç nokta aşağıdakilerden oluşur:

- Adres: adres, uç noktayı benzersiz bir şekilde tanımlar ve hizmetin bulunduğu tüketicilere ait potansiyel tüketicilere bildirir. Sınıfı tarafından WCF nesne modelinde temsil edilir <xref:System.ServiceModel.EndpointAddress> . Bir <xref:System.ServiceModel.EndpointAddress> sınıf şunları içerir:

  - <xref:System.ServiceModel.EndpointAddress.Uri%2A>Hizmetin adresini temsil eden bir özellik.

  - <xref:System.ServiceModel.EndpointAddress.Identity%2A>Hizmetin güvenlik kimliğini ve isteğe bağlı ileti üstbilgileri koleksiyonunu temsil eden bir özellik. İsteğe bağlı ileti üstbilgileri, uç noktayı tanımlamak veya bunlarla etkileşime geçmek üzere ek ve daha ayrıntılı adresleme bilgileri sağlamak için kullanılır.

  Daha fazla bilgi için bkz. [uç nokta adresi belirtme](../specifying-an-endpoint-address.md).

- Bağlama: bağlama, bitiş noktasıyla nasıl iletişim kuracağını belirtir. Buna aşağıdakiler dahildir:

  - Kullanılacak Aktarım Protokolü (örneğin, TCP veya HTTP).

  - İletiler için kullanılacak kodlama (örneğin, metin veya ikili).

  - Gerekli güvenlik gereksinimleri (örneğin, SSL veya SOAP iletisi güvenliği).

  Daha fazla bilgi için bkz. [WCF bağlamalarına genel bakış](../bindings-overview.md). Bir bağlama, WCF nesne modelinde soyut temel sınıf tarafından temsil edilir <xref:System.ServiceModel.Channels.Binding> . Çoğu senaryoda, kullanıcılar sistem tarafından belirtilen bağlamalardan birini kullanabilir. Daha fazla bilgi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).

- Sözleşmeler: sözleşme, uç noktanın istemciye sunduğu işlevleri özetler. Bir sözleşme şunları belirtir:

  - İstemci tarafından hangi işlemleri çağrılabilecek.

  - İleti formu.

  - İşlemi çağırmak için gereken giriş parametrelerinin veya verilerin türü.

  - İstemcinin tahmin edebilecekleri işlem veya yanıt iletisi türü.

  Sözleşme tanımlama hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).

- Davranışlar: uç nokta davranışlarını, hizmet uç noktasının yerel davranışını özelleştirmek için kullanabilirsiniz. Endpoint davranışları, WCF çalışma zamanı oluşturma işlemine katılarak bunu elde etmenizi ister. Bir uç nokta davranışı örneği <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> , soap veya Web Hizmetleri Açıklama Dili (wsdl) adresinden farklı bir dinleme adresi belirtmenizi sağlayan özelliktir. Daha fazla bilgi için bkz. [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).

## <a name="defining-endpoints"></a>Uç noktaları tanımlama

Bir hizmet için uç noktayı kod kullanarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-configuration.md) ve [nasıl yapılır: kod Içinde hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-code.md).

## <a name="in-this-section"></a>Bu Bölümde

Bu bölümde bağlamalar, uç noktalar ve adreslerin amacı açıklanmaktadır; bir bağlamanın ve uç noktanın nasıl yapılandırılacağını gösterir; ve `ClientVia` davranışın ve özelliğinin nasıl kullanılacağını gösterir `ListenUri` .

[Gideren](endpoint-addresses.md)\
Uç noktaların WCF 'de nasıl giderildiği açıklanmaktadır.

[Lara](bindings.md)\
İstemcilerin ve hizmetlerin birbirleriyle iletişim kurması için gereken aktarım, kodlama ve protokol ayrıntılarını belirtmek için bağlamaların nasıl kullanıldığını açıklar.

[Sözleşmeleri](contracts.md)\
Sözleşmelerin bir hizmet yöntemlerini nasıl tanımlalarını açıklar.

[Nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-configuration.md)\
Yapılandırmada bir hizmet uç noktası oluşturmayı açıklar.

[Nasıl yapılır: kod içinde hizmet uç noktası oluşturma](how-to-create-a-service-endpoint-in-code.md)\
Kodda bir hizmet uç noktası oluşturmayı açıklar.

[Nasıl yapılır: derlenmiş hizmet kodunu doğrulamak için Svcutil. exe kullanma](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)\
Hizmet uygulamalarında ve yapılandırmalarda [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak hizmeti barındırmadan hataların nasıl algılanacağını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Yapılandırma](../configuring-services.md)
- [Bağlamaları Genişletme](../extending/extending-bindings.md)
