---
title: 'Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 6bd67ec8dcc0e73d097796b44974dce00b9a4eb2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601224"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme
Genellikle, aynı kişi hizmetleri tasarlamaz ve uygulamaz. Birlikte çalışma uygulamalarının önemli olduğu ortamlarda, sözleşmeler Web Hizmetleri Açıklama Dili (WSDL) içinde tasarlanabilir veya açıklanabilir ve bir geliştirici, belirtilen sözleşmeye uygun bir hizmet uygulamalıdır. Ayrıca, var olan bir hizmeti Windows Communication Foundation (WCF) öğesine geçirmek, ancak tel biçimini korumak isteyebilirsiniz. Ek olarak, çift yönlü sözleşmeler de çağıranların geri çağırma anlaşması uygulamasını gerektirir.  
  
 Bu durumlarda, sözleşmenin gereksinimlerini karşılamak üzere uygulayabileceğiniz bir yönetilen dilde hizmet sözleşmesi arabirimi oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) (veya eşdeğer bir aracı) kullanmanız gerekir. Genellikle [ServiceModel meta veri yardımcı programı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , bir kanal FABRIKASı veya WCF istemci türü ile birlikte kullanılan bir hizmet sözleşmesini ve doğru bağlama ve adresi ayarlayan bir istemci yapılandırma dosyasını almak için kullanılır. Oluşturulan yapılandırma dosyasını kullanmak için, onu bir hizmet yapılandırma dosyası olarak değiştirmeniz gerekir. Ayrıca, hizmet sözleşmesini değiştirmeniz gerekebilir.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Verileri almak ve uyumlu bir hizmeti uygulamak için  
  
1. Bir kod dosyası oluşturmak için meta veri dosyalarına veya meta veri uç noktasına karşı [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
2. Öznitelik ile işaretlenmiş, ilgilendiğiniz arayüzü (birden fazla olması durumunda) içeren çıkış kodu dosyasının bölümünü arayın <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> . Aşağıdaki kod örneği, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan iki arabirimi gösterir. Birincisi ( `ISampleService` ), uyumlu bir hizmet oluşturmak için uyguladığınız hizmet sözleşmesi arabirimidir. İkincisi ( `ISampleServiceChannel` ), hem hizmet sözleşmesi arabirimini genişleten hem de <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> bir istemci uygulamasında kullanılmak üzere istemci kullanımı için bir yardımcı arabirimdir.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. WSDL tüm işlemler için bir yanıt eylemi belirtmezse, oluşturulan işlem sözleşmeleri <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> özelliği joker karakter (*) olarak ayarlanmış olabilir. Bu özellik ayarını kaldırın. Aksi takdirde, hizmet sözleşmesi meta verilerini uyguladığınızda bu işlemler için meta veriler verilemez.  
  
4. Arabirimini bir sınıfa uygulayın ve hizmeti barındırın. Örnek için bkz. [nasıl yapılır: bir hizmet sözleşmesini uygulama](../how-to-implement-a-wcf-contract.md)veya örnek bölümünde aşağıdaki basit bir uygulama görme.  
  
5. [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturduğu istemci yapılandırma dosyasında yapılandırma bölümünü [\<client>](../../configure-apps/file-schema/wcf/client.md) [\<services>](../../configure-apps/file-schema/wcf/services.md) yapılandırma bölümüne değiştirin. (Oluşturulan bir istemci uygulama yapılandırma dosyasına bir örnek için, aşağıdaki "örnek" bölümüne bakın.)  
  
6. [\<services>](../../configure-apps/file-schema/wcf/services.md)Yapılandırma bölümünde, `name` [\<services>](../../configure-apps/file-schema/wcf/services.md) hizmet uygulamanızın yapılandırma bölümünde bir öznitelik oluşturun.  
  
7. Hizmet `name` uygulamanızın yapılandırma adına hizmet özniteliğini ayarlayın.  
  
8. Uygulanan hizmet sözleşmesini kullanan uç nokta yapılandırma öğelerini hizmet yapılandırma bölümüne ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, meta veri dosyalarına karşı [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırılarak oluşturulan bir kod dosyasının çoğunluğunu gösterir.  
  
 Aşağıdaki kod şunu gösterir:  
  
- Uygulandığında, sözleşme gereksinimleriyle () uyumlu olan hizmet sözleşmesi arabirimi `ISampleService` .  
  
- Hem hizmet sözleşmesi arabirimini genişleten hem de <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> ve bir istemci uygulamasında () kullanmak için istemci kullanımı için yardımcı arabirim `ISampleServiceChannel` .  
  
- Ve ' i genişleten yardımcı sınıfı, <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> bir istemci uygulamasında () kullanımı içindir `SampleServiceClient` .  
  
- Hizmetten oluşturulan yapılandırma dosyası.  
  
- Basit bir `ISampleService` hizmet uygulamasıdır.  
  
- İstemci tarafı yapılandırma dosyasının bir hizmet tarafı sürümüne dönüştürülmesi.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
