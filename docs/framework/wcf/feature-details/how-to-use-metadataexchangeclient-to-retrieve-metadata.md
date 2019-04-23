---
title: 'Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: 32acef65ee30d7b80b37c11bdd024e3c09a935ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977680"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma
Kullanım <xref:System.ServiceModel.Description.MetadataExchangeClient> sınıfı WS-MetadataExchange (MEX) protokolünü kullanarak meta verileri indirilemedi. Alınan meta veri dosyaları olarak döndürülen bir <xref:System.ServiceModel.Description.MetadataSet> nesne. Döndürülen <xref:System.ServiceModel.Description.MetadataSet> nesneyi içeren koleksiyonu <xref:System.ServiceModel.Description.MetadataSection> nesneleri, her birinin içerdiği belirli meta veriler diyalekti ve bir tanımlayıcı. Döndürülen meta verilere dosyalara yazmak veya döndürülen meta verilere Web Hizmetleri Açıklama Dili (WSDL) belgeleri içeriyorsa, meta verileri kullanarak içeri aktarabilirsiniz <xref:System.ServiceModel.Description.WsdlImporter>.  
  
 <xref:System.ServiceModel.Description.MetadataExchangeClient> Bir adresi alan oluşturucular üzerinde bağlama kullan <xref:System.ServiceModel.Description.MetadataExchangeBindings> adresinin Tekdüzen Kaynak Tanımlayıcısı (URI) şemasını eşleşen statik sınıf. Alternatif olarak kullanabileceğiniz <xref:System.ServiceModel.Description.MetadataExchangeClient> Oluşturucu açıkça kullanılacak bağlamanın belirtmenizi sağlar. Belirtilen bağlama, tüm meta veri başvurularını çözümlemek için kullanılır.  
  
 Tıpkı diğer Windows Communication Foundation (WCF) istemcisini, olduğu gibi <xref:System.ServiceModel.Description.MetadataExchangeClient> türü, istemci uç noktası yapılandırmaları uç nokta yapılandırma adlarını kullanarak yüklemek için bir oluşturucu sağlar. Belirtilen uç nokta yapılandırması belirtmelisiniz <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme. Birini kullanmak için uç nokta yapılandırması adres, yüklenmedi <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> bir adresi alan aşırı yüklemeler. Belirttiğinizde meta veri adresini kullanarak bir <xref:System.ServiceModel.EndpointAddress> örneği <xref:System.ServiceModel.Description.MetadataExchangeClient> adresi MEX uç noktasına işaret varsayar. Bir URL olarak meta veri adresi belirtin, ardından da belirtmek için ihtiyacınız varsa <xref:System.ServiceModel.Description.MetadataExchangeClientMode> kullanmak için MEX veya HTTP GET.  
  
> [!IMPORTANT]
>  Varsayılan olarak, <xref:System.ServiceModel.Description.MetadataExchangeClient> sizin için tüm başvuruları çözümler WSDL ve XML Şeması de dahil olmak üzere içeri aktarır ve da içerir. Ayarlayarak bu işlevi devre dışı bırakabilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini `false`. Kullanarak çözümlemek için başvuru sayısı denetleyebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> özelliği. Bu özellik ile birlikte kullanabileceğiniz `MaxReceivedMessageSize` bağlamanın ne kadar meta veri alındığını denetleme özelliği.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Meta verileri almak için MetadataExchangeClient kullanılacak  
  
1. Yeni bir <xref:System.ServiceModel.Description.MetadataExchangeClient> bağlama, bir uç nokta Yapılandırması adı veya meta veri adresini açıkça belirterek nesne.  
  
2. Yapılandırma <xref:System.ServiceModel.Description.MetadataExchangeClient> gereksinimlerinize uyacak şekilde. Örneğin, meta veriler bulunurken kullanmak, nasıl meta veri başvurularının çözümlenen ayarlayın ve denetlemek için kimlik bilgilerini belirtebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> ne kadar zaman aşımına uğramadan önce döndürmek meta veri isteği olduğunu denetleme özelliği.  
  
3. Elde <xref:System.ServiceModel.Description.MetadataSet> birini çağırma alınan meta veriler içeren nesne <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> yöntemleri. Yalnızca kullanabileceğinizi unutmayın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> açıkça bir adresi oluştururken belirttiyseniz bağımsız değişkeni alan aşırı yüklemesini <xref:System.ServiceModel.Description.MetadataExchangeClient>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.ServiceModel.Description.MetadataExchangeClient> indirip meta veri dosyaları numaralandırma.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kod örneği derlemek için System.ServiceModel.dll derlemeye başvuru ve içe <xref:System.ServiceModel.Description> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
