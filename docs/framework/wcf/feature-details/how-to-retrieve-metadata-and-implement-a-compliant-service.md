---
title: 'Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 0a13d504b1c7c38ec13fee58c36913a75119271b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184856"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme
Genellikle, aynı kişi tasarım ve hizmetleri uygulamak değildir. Ara uygulamaların önemli olduğu ortamlarda, sözleşmeler Web Hizmetleri Açıklama Dili'nde (WSDL) tasarlanabilir veya açıklanabilir ve geliştiricinin sağlanan sözleşmeye uygun bir hizmet uygulaması gerekir. Ayrıca, varolan bir hizmeti Windows Communication Foundation'a (WCF) geçirmek, ancak tel biçimini korumak isteyebilirsiniz. Buna ek olarak, çift yönlü sözleşmeler arayanların da bir geri arama sözleşmesi uygulamasını gerektirir.  
  
 Bu gibi durumlarda, sözleşmenin gereksinimlerini karşılamak için uygulayabileceğiniz yönetilen bir dilde bir hizmet sözleşmesi arabirimi oluşturmak için [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (veya eşdeğer bir araç) kullanmanız gerekir. Genellikle [ServiceModel Metadata Utility Tool (Svcutil.exe),](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bir kanal fabrikası veya WCF istemci türüyle ve doğru bağlama yı ve adresi ayarlayan bir istemci yapılandırma dosyasıyla kullanılan bir hizmet sözleşmesi elde etmek için kullanılır. Oluşturulan yapılandırma dosyasını kullanmak için, bunu bir hizmet yapılandırma dosyasına dönüştürmeniz gerekir. Hizmet sözleşmesini değiştirmeniz de gerekebilir.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Veri almak ve uyumlu bir hizmet uygulamak için  
  
1. Bir kod dosyası oluşturmak için meta veri dosyalarına veya meta veri bitiş noktasına karşı [ServiceModel Metadata Utility Aracını (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
2. Çıkış kodu dosyasının ilgi arabirimini içeren bölümünü (birden fazla olması durumunda) öznitelikle <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> işaretlenmiş bölümü arayın. Aşağıdaki kod örneği [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan iki arabirimi gösterir. Birincisi ,`ISampleService`uyumlu bir hizmet oluşturmak için uyguladığınız hizmet sözleşmesi arabirimidir. İkinci (`ISampleServiceChannel`) istemci kullanımı için hem hizmet sözleşmesi arabirimini <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> genişleten hem de istemci uygulamasında kullanılmak üzere yardımcı bir arabirimdir.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. WSDL tüm işlemler için bir yanıt eylemi belirtmezse, oluşturulan işlem <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> sözleşmeleri özelliği joker karaktere ayarlanmış olabilir (*). Bu özellik ayarını kaldırın. Aksi takdirde, hizmet sözleşmesi meta verilerini uyguladığınız zaman, meta veriler bu işlemler için dışa aktarılamaz.  
  
4. Arabirimi bir sınıfa uygulayın ve hizmeti barındırın. Örneğin, [bkz.](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
  
5. [ServiceModel Metadata Utility Tool'un (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturduğu istemci yapılandırma dosyasında, [ \<istemci>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) yapılandırma bölümünü [ \<bir hizmet>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) yapılandırma bölümüne değiştirin. (Oluşturulan istemci uygulama yapılandırma dosyası örneği için aşağıdaki "Örnek" bölümüne bakın.)  
  
6. Hizmetler>yapılandırma bölümünde, `name` [ \<hizmet](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) uygulamanız için hizmetler>yapılandırma bölümünde bir öznitelik oluşturun. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
7. Hizmet uygulamanız için yapılandırma adına hizmet `name` özniteliğini ayarlayın.  
  
8. Hizmet yapılandırma bölümüne uygulanan hizmet sözleşmesini kullanan bitiş noktası yapılandırma öğelerini ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, [ServiceModel Metadata Utility Tool 'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veri dosyalarına karşı çalıştırarak oluşturulan bir kod dosyasının çoğunluğunu gösterir.  
  
 Aşağıdaki kod gösterir:  
  
- Uygulandığında sözleşme gerekliliklerine uygun hizmet sözleşmesi arabirimi`ISampleService`( ).  
  
- Hem hizmet sözleşmesi arabirimini genişleten hem <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> de istemci uygulamasında kullanılmak üzere`ISampleServiceChannel`istemci kullanımı için yardımcı arabirim ( ).  
  
- Genişletir <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> ve bir istemci uygulamasında kullanım için yardımcı`SampleServiceClient`sınıf ( ).  
  
- Hizmetten oluşturulan yapılandırma dosyası.  
  
- Basit `ISampleService` bir hizmet uygulaması.  
  
- İstemci tarafı yapılandırma dosyasının hizmet tarafındaki sürüme dönüştürülmesi.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
