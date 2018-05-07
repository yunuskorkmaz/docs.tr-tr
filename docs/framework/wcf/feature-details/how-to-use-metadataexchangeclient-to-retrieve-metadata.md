---
title: 'Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: 1df4bc156485108dc0c11d597b268864c9656b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma
Kullanım <xref:System.ServiceModel.Description.MetadataExchangeClient> sınıfı WS-MetadataExchange (MEX) protokolünü kullanarak meta verileri indirir. Alınan meta veri dosyaları verilir bir <xref:System.ServiceModel.Description.MetadataSet> nesnesi. Döndürülen <xref:System.ServiceModel.Description.MetadataSet> nesnesini içeren koleksiyonu <xref:System.ServiceModel.Description.MetadataSection> nesneleri, her biri içeren belirli meta veriler dialect ve bir tanımlayıcı. Döndürülen meta veri dosyaları için yazabilir veya Web Hizmetleri Açıklama Dili (WSDL) belgeleri döndürülen meta veri içeriyorsa, meta verileri kullanarak içeri aktarabilirsiniz <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 <xref:System.ServiceModel.Description.MetadataExchangeClient> Bir adresi alın oluşturucular kullandığınıza bağlama <xref:System.ServiceModel.Description.MetadataExchangeBindings> adresinin Tekdüzen Kaynak Tanımlayıcısı (URI) şemasını eşleşen statik sınıf. Alternatif olarak kullanabileceğiniz <xref:System.ServiceModel.Description.MetadataExchangeClient> açıkça kullanılacak bağlama belirtmenize olanak tanır Oluşturucusu. Belirtilen bağlama tüm meta veri başvurularını çözmek için kullanılır.  
  
 Diğer Windows Communication Foundation (WCF) istemcisini,'olduğu gibi <xref:System.ServiceModel.Description.MetadataExchangeClient> türü, istemci uç noktası yapılandırmaları uç nokta Yapılandırması adı kullanarak yüklemek için bir oluşturucu sağlar. Belirtilen uç nokta yapılandırması belirtmelisiniz <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme. Aşağıdakilerden birini kullanmanız gerekir böylece uç nokta yapılandırması adresi, yüklü değil <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> bir adresi alın aşırı. Meta veri adresi kullanarak belirttiğinizde bir <xref:System.ServiceModel.EndpointAddress> örneği <xref:System.ServiceModel.Description.MetadataExchangeClient> adresi bir MEX uç noktaya işaret varsayar. Meta veri adresi bir URL olarak belirttiğiniz sonra da belirtmek gereken <xref:System.ServiceModel.Description.MetadataExchangeClientMode> kullanmak için MEX veya HTTP GET.  
  
> [!IMPORTANT]
>  Varsayılan olarak, <xref:System.ServiceModel.Description.MetadataExchangeClient> tüm başvuruları sizin için çözümler WSDL ve XML Şeması dahil olmak üzere içeri aktarır ve da içerir. Ayarlayarak bu işlev devre dışı bırakabilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğine `false`. Kullanarak çözümlemek için referans maksimum sayısını kontrol edebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> özelliği. Bu özellik ile birlikte kullanabileceğiniz `MaxReceivedMessageSize` ne kadar meta verileri alınır denetlemek için bağlama özelliği.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Meta veri elde etmek üzere MetadataExchangeClient kullanma  
  
1.  Yeni bir <xref:System.ServiceModel.Description.MetadataExchangeClient> belirterek açıkça bağlama, bir uç nokta yapılandırması adını veya adresini meta veri nesnesi.  
  
2.  Yapılandırma <xref:System.ServiceModel.Description.MetadataExchangeClient> gereksinimlerinize uygun olarak. Örneğin, meta veriler bulunurken kullanın, nasıl meta veri başvurularını çözümlendi, ayarlayın ve denetlemek için kimlik bilgileri belirtebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> ne kadar zaman aşımına uğramadan önce dönmek meta veri isteği olduğunu denetleme özelliği.  
  
3.  Elde <xref:System.ServiceModel.Description.MetadataSet> birini çağırarak alınan meta verileri içeren nesne <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> yöntemleri. Yalnızca kullanabilirsiniz Not <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> açıkça bir adresi oluşturulurken belirttiyseniz bağımsız değişken almayan aşırı <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.ServiceModel.Description.MetadataExchangeClient> karşıdan yüklenir ve meta veri dosyaları numaralandırma.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kod örneği derlemek için System.ServiceModel.dll derleme başvurusu ve alma <xref:System.ServiceModel.Description> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.MetadataResolver>  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>  
 <xref:System.ServiceModel.Description.WsdlImporter>
