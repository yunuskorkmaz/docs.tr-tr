---
title: 'Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 9ae888f5a9569ef51be52b91ea019fea897597b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme
Genellikle, aynı kişi değildir tasarlayıp Hizmetleri. Birlikte çalışma uygulamaları önemli olduğu ortamlarda sözleşmeleri tasarlanmış ya da Web Hizmetleri Açıklama Dili (WSDL) açıklanan ve geliştirici sağlanan sözleşme ile uyumlu bir hizmet uygulamalıdır. Windows Communication Foundation (WCF) için bir hizmetiniz geçirmek ancak kablo biçimini korumak isteyebilirsiniz. Ayrıca, çift yönlü sözleşmeler da bir geri çağırma sözleşmesini uygulama arayanlar gerektirir.  
  
 Bu durumlarda, kullanmalısınız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (veya eşdeğer bir aracı) gereksinimlerini karşılamak için uygulayabileceğiniz yönetilen bir dilde hizmet sözleşme arabirimi oluşturmak için Sözleşme. Genellikle [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kanal fabrikası ya da bir WCF istemcisi türü ile yanı sıra yukarı doğru bağlama ayarlar istemci yapılandırma dosyası ile kullanılan bir hizmet sözleşmesini almak için kullanılır ve adres. Oluşturulan yapılandırma dosyası kullanmak için bir hizmet yapılandırma dosyasına değiştirmeniz gerekir. Hizmet sözleşmesi değiştirmeniz gerekebilir.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Veri almak ve uyumlu bir hizmet ekleme  
  
1.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veri dosyaları veya bir kod dosyası oluşturmak için bir meta veri uç noktası karşı.  
  
2.  İle işaretlenen içeren ilgi (var. durumda birden fazla tek) arabiriminin çıkış kodu dosyası bölümünü arayın <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> özniteliği. Aşağıdaki kod örneği tarafından oluşturulan iki arabirimler gösterilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). İlk (`ISampleService`) uyumlu bir hizmet oluşturmak için uygulaması hizmet sözleşmesi arabirimidir. İkinci (`ISampleServiceChannel`) her iki hizmet sözleşme arabirimi genişletir istemci kullanımı için yardımcı arabirimdir ve <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> ve bir istemci uygulamasındaki kullanım içindir.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  WSDL tüm işlemler için bir yanıt eylemi belirtmiyor, oluşturulan işlemi sözleşmeleri olabilir <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> özelliği için joker karakter (*) olarak ayarlanmış. Bu özellik ayarı kaldırın. Aksi takdirde, hizmet sözleşmesi meta verilerini uyguladığınızda, meta verileri bu işlemleri için verilemez.  
  
4.  Arabirim üzerinde bir sınıf uygulama ve hizmet ana bilgisayar. Bir örnek için bkz: [nasıl yapılır: bir hizmet sözleşmesini uygulama](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), veya bir basit uygulamasında Aşağıda örnek bölümüne bakın.  
  
5.  İstemci yapılandırmasında, dosya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturur, değiştirme [ \<istemci >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) yapılandırma bölümü bir [ \<Hizmetleri >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) yapılandırma bölümü. (Oluşturulan istemci uygulama yapılandırma dosyası örneği için aşağıdaki "Örnek" bölümüne bakın.)  
  
6.  İçinde [ \<Hizmetleri >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) yapılandırma bölümünde, oluşturmak bir `name` özniteliğini [ \<Hizmetleri >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) hizmetiniz için yapılandırma bölümü uygulaması.  
  
7.  Hizmet kümesi `name` , hizmet uygulamanız için yapılandırma adı özniteliği.  
  
8.  Hizmet yapılandırma bölümü uygulanan hizmet sözleşmesi kullanan uç nokta yapılandırma öğelerini ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde çalıştırarak oluşturulan bir kod dosyası çoğunluğu gösterir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veri dosyası.  
  
 Aşağıdaki kod gösterir:  
  
-   Hizmet sözleşmesi arabirim, uygulandığında sözleşme gereksinimleriyle uyumlu (`ISampleService`).  
  
-   Her iki hizmet sözleşme arabirimi genişletir istemci kullanımı için yardımcı arabirimi ve <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> ve bir istemci uygulaması için kullanılır (`ISampleServiceChannel`).  
  
-   Genişletir yardımcı sınıfı <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> ve bir istemci uygulaması için kullanılır (`SampleServiceClient`).  
  
-   Hizmetinden oluşturulan yapılandırma dosyası.  
  
-   Basit bir `ISampleService` hizmet uygulaması.  
  
-   Hizmet tarafı sürümüne dönüştürme istemci tarafı yapılandırma dosyası.  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]    
 [!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    
 [!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
