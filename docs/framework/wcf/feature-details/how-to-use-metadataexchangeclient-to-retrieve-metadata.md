---
description: 'Daha fazla bilgi edinin: nasıl yapılır: meta verileri almak için MetadataExchangeClient kullanma'
title: 'Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: 17206bbba2ccde5961326a431b019fb7718f6cd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734340"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma

<xref:System.ServiceModel.Description.MetadataExchangeClient>WS-MetadataExchange (MEX) protokolünü kullanarak meta verileri indirmek için sınıfını kullanın. Alınan meta veri dosyaları bir nesne olarak döndürülür <xref:System.ServiceModel.Description.MetadataSet> . Döndürülen <xref:System.ServiceModel.Description.MetadataSet> nesne <xref:System.ServiceModel.Description.MetadataSection> , her biri belirli bir meta veri diyalekti ve tanımlayıcı içeren bir nesne koleksiyonu içerir. Döndürülen meta verileri dosyalara yazabilir veya döndürülen meta veriler Web Hizmetleri Açıklama Dili (WSDL) belgeleri içeriyorsa, kullanarak meta verileri içeri aktarabilirsiniz <xref:System.ServiceModel.Description.WsdlImporter> .  
  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>Adresi alan oluşturucular, <xref:System.ServiceModel.Description.MetadataExchangeBindings> adresin Tekdüzen Kaynak tanımlayıcısı (URI) düzeniyle eşleşen statik sınıfta bağlamayı kullanır. Alternatif olarak, <xref:System.ServiceModel.Description.MetadataExchangeClient> kullanılacak bağlamayı açıkça belirtmenizi sağlayan oluşturucuyu kullanabilirsiniz. Belirtilen bağlama tüm meta veri başvurularını çözümlemek için kullanılır.  
  
 Aynı diğer Windows Communication Foundation (WCF) istemci gibi, türü, <xref:System.ServiceModel.Description.MetadataExchangeClient> uç nokta yapılandırma adını kullanarak istemci uç noktası yapılandırmalarını yüklemek için bir oluşturucu sağlar. Belirtilen uç nokta yapılandırması <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmeyi belirtmelidir. Uç nokta yapılandırmasındaki adres yüklenmedi, <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> Bu nedenle bir adresi alan aşırı yüklerden birini kullanmalısınız. Meta veri adresini bir örnek kullanarak belirttiğinizde, <xref:System.ServiceModel.EndpointAddress> <xref:System.ServiceModel.Description.MetadataExchangeClient> ADRESIN bir MEX uç noktasına işaret ettiğini varsayar. Meta veri adresini bir URL olarak belirtirseniz, ne <xref:System.ServiceModel.Description.MetadataExchangeClientMode> kullanacağınızı, MEX veya http get ' i de belirtmeniz gerekir.  
  
> [!IMPORTANT]
> Varsayılan olarak, <xref:System.ServiceModel.Description.MetadataExchangeClient> WSDL ve XML şema içeri aktarmaları ve dahil olmak üzere tüm başvuruları çözümler. Özelliğini olarak ayarlayarak bu işlevselliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> `false` . Özelliğini kullanarak çözülecek en fazla başvuru sayısını kontrol edebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> . Bu özelliği, `MaxReceivedMessageSize` ne kadar meta veri alındığını denetlemek için bağlamadaki özelliğiyle birlikte kullanabilirsiniz.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Meta verileri almak için MetadataExchangeClient kullanma  
  
1. <xref:System.ServiceModel.Description.MetadataExchangeClient>Açıkça bir bağlama, uç nokta yapılandırma adı veya meta veri adresini belirterek yeni bir nesne oluşturun.  
  
2. ' İ <xref:System.ServiceModel.Description.MetadataExchangeClient> gereksinimlerinize uyacak şekilde yapılandırın. Örneğin, meta veri istenirken kullanılacak kimlik bilgilerini belirtebilir, meta veri başvurularının nasıl çözümlendiğini denetleyebilir ve <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> meta veri isteğinin zaman aşımına uğramadan önce ne kadar süre geri dönmesi gerektiğini denetlemek için özelliğini ayarlayabilirsiniz.  
  
3. <xref:System.ServiceModel.Description.MetadataSet>Yöntemlerin birini çağırarak alınan meta verileri içeren nesneyi edinin <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> . ' İ <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> oluştururken açıkça bir adres belirttiyseniz, yalnızca bağımsız değişken alan aşırı yüklemeyi kullanabileceğinizi unutmayın <xref:System.ServiceModel.Description.MetadataExchangeClient> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, <xref:System.ServiceModel.Description.MetadataExchangeClient> meta veri dosyalarını indirmek ve listelemek için nasıl kullanılacağını gösterir.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu kod örneğini derlemek için System.ServiceModel.dll derlemesine başvurmanız ve ad alanını içeri aktarmanız gerekir <xref:System.ServiceModel.Description> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
