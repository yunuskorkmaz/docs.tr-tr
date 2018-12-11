---
title: 'Nasıl Yapılır: Meta veri alma ve uyumlu bir hizmet ekleme'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: dc7f5d97a5201698e8dc99e4523e3ab2925f6883
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148932"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Nasıl Yapılır: Meta veri alma ve uyumlu bir hizmet ekleme
Genellikle, aynı kişi değildir tasarlayıp Hizmetleri. Birlikte çalışma uygulamaları önemli olduğu ortamlarda sözleşmelerine tasarlanan veya Web Hizmetleri Açıklama Dili (WSDL) açıklanan ve bir geliştirici, sağlanan Sözleşmesi ile uyumlu bir hizmet uygulaması gerekir. Windows Communication Foundation (WCF) için bir hizmetiniz geçirme ancak kablo biçimini korumak isteyebilirsiniz. Ayrıca, çift yönlü sözleşmeler de bir geri çağırma anlaşması uygulamak çağıranlar gerektirir.  
  
 Bu gibi durumlarda kullanmalısınız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (veya eşdeğer bir aracı) gereksinimlerini karşılamak için uygulayabileceğiniz yönetilen bir dilde hizmet sözleşme arabirimi oluşturmak için Sözleşme. Genellikle [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kanal fabrikası ya da bir WCF istemci türü ile yanı sıra yukarı doğru bağlama ayarlar bir istemci yapılandırma dosyası ile kullanılan bir hizmet sözleşmesini almak için kullanılır ve adresi. Oluşturulan yapılandırma dosyası kullanmak için bir hizmet yapılandırma dosyasına değiştirmeniz gerekir. Hizmet sözleşmesi değiştirmek gerekebilir.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Veri alma ve uyumlu bir hizmet ekleme  
  
1.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veri dosyaları veya bir kod dosyası oluşturmak için bir meta veri uç noktasına karşı.  
  
2.  İle işaretlenen arabirim ilgilendiğiniz (çalışması yok birden fazla tek) içeren çıkış dosyasının kod bölümü için arama <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> özniteliği. Aşağıdaki kod örneği tarafından oluşturulan iki arabirimler gösterilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). İlk (`ISampleService`) uyumlu bir hizmet oluşturmak için uygulama hizmet sözleşmesi arabirimidir. İkinci (`ISampleServiceChannel`) her iki hizmet sözleşme arabirimini genişletir istemci kullanımı Yardımcısı arabirimdir ve <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> ve bir istemci uygulamasında kullanılır.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  WSDL tüm işlemler için bir yanıt eylemi belirtmezse, oluşturulan işlem sözleşmeleri olabilir <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> özelliği için joker karakter (*). Bu özellik ayarı kaldırın. Aksi takdirde, hizmet sözleşmesi meta verileri uyguladığınızda, meta veriler bu işlemler için dışarı aktarılamaz.  
  
4.  Bir sınıf üzerinde arabirim uygular ve hizmet barındırın. Bir örnek için bkz [nasıl yapılır: Bir hizmet sözleşmesini uygulama](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), veya aşağıda basit bir uygulama örnek bölümünde bakın.  
  
5.  İstemci yapılandırmasında dosya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturur, değiştirme [ \<istemci >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) yapılandırma bölümü bir [ \<Hizmetleri >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) yapılandırma bölümü. (Oluşturulan istemci uygulama yapılandırma dosyası örneği için aşağıdaki "Örnek" bölümüne bakın.)  
  
6.  İçinde [ \<Hizmetleri >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) yapılandırma bölümünde, oluşturun bir `name` özniteliğini [ \<Hizmetleri >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) hizmetiniz için yapılandırma bölümü uygulama.  
  
7.  Hizmet kümesi `name` hizmet uygulamanız için yapılandırma adı özniteliği.  
  
8.  Hizmet yapılandırma bölümü için uygulanan hizmet sözleşmesi kullandığınız uç nokta yapılandırma öğeleri ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir kod dosyası çalıştırılarak oluşturulan çoğunu gösterir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veri dosyası.  
  
 Aşağıdaki kod gösterir:  
  
-   Hizmet sözleşmesi arabirim, uygulandığında, sözleşme gereksinimleriyle uyumlu (`ISampleService`).  
  
-   Her iki hizmet sözleşme arabirimini genişletir istemci kullanımı için yardımcı arabirimi ve <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> ve bir istemci uygulamasında kullanılır (`ISampleServiceChannel`).  
  
-   Genişleten helper sınıfı <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> ve bir istemci uygulamasında kullanılır (`SampleServiceClient`).  
  
-   Hizmetten oluşturulan yapılandırma dosyası.  
  
-   Basit bir `ISampleService` hizmet uygulaması.  
  
-   İstemci tarafı yapılandırma dosyasının dönüştürme için bir hizmet tarafı sürümü.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
