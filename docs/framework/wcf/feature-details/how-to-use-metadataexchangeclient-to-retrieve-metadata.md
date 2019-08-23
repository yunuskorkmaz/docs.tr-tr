---
title: 'Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: c9558e1943c3886a61c3b19801e22d57732e459a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968760"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma
WS-MetadataExchange (MEX) protokolünü kullanarak meta verileri indirmek için sınıfınıkullanın.<xref:System.ServiceModel.Description.MetadataExchangeClient> Alınan meta veri dosyaları bir <xref:System.ServiceModel.Description.MetadataSet> nesne olarak döndürülür. Döndürülen <xref:System.ServiceModel.Description.MetadataSet> nesne, her biri belirli bir <xref:System.ServiceModel.Description.MetadataSection> meta veri diyalekti ve tanımlayıcı içeren bir nesne koleksiyonu içerir. Döndürülen meta verileri dosyalara yazabilir veya döndürülen meta veriler Web Hizmetleri Açıklama Dili (WSDL) belgeleri içeriyorsa, kullanarak <xref:System.ServiceModel.Description.WsdlImporter>meta verileri içeri aktarabilirsiniz.  
  
 Adresi alan <xref:System.ServiceModel.Description.MetadataExchangeBindings> oluşturucular, adresin Tekdüzen Kaynak tanımlayıcısı (URI) düzeniyle eşleşen statik sınıfta bağlamayı kullanır. <xref:System.ServiceModel.Description.MetadataExchangeClient> Alternatif olarak, kullanılacak bağlamayı <xref:System.ServiceModel.Description.MetadataExchangeClient> açıkça belirtmenizi sağlayan oluşturucuyu kullanabilirsiniz. Belirtilen bağlama tüm meta veri başvurularını çözümlemek için kullanılır.  
  
 Aynı diğer Windows Communication Foundation (WCF) istemci gibi, <xref:System.ServiceModel.Description.MetadataExchangeClient> türü, uç nokta yapılandırma adını kullanarak istemci uç noktası yapılandırmalarını yüklemek için bir oluşturucu sağlar. Belirtilen uç nokta yapılandırması <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmeyi belirtmelidir. Uç nokta yapılandırmasındaki adres yüklenmedi, bu nedenle bir adresi alan <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> aşırı yüklerden birini kullanmalısınız. Meta veri adresini bir <xref:System.ServiceModel.EndpointAddress> örnek <xref:System.ServiceModel.Description.MetadataExchangeClient> kullanarak belirttiğinizde, adresin bir MEX uç noktasına işaret ettiğini varsayar. Meta veri adresini bir URL olarak belirtirseniz, ne <xref:System.ServiceModel.Description.MetadataExchangeClientMode> kullanacağınızı, MEX veya http get ' i de belirtmeniz gerekir.  
  
> [!IMPORTANT]
> Varsayılan olarak, WSDL <xref:System.ServiceModel.Description.MetadataExchangeClient> ve XML şema içeri aktarmaları ve dahil olmak üzere tüm başvuruları çözümler. <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> Özelliğini olarak`false`ayarlayarak bu işlevselliği devre dışı bırakabilirsiniz. <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> Özelliğini kullanarak çözülecek en fazla başvuru sayısını kontrol edebilirsiniz. Bu özelliği, ne kadar meta veri alındığını denetlemek `MaxReceivedMessageSize` için bağlamadaki özelliğiyle birlikte kullanabilirsiniz.  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>Meta verileri almak için MetadataExchangeClient kullanma  
  
1. Açıkça bir bağlama <xref:System.ServiceModel.Description.MetadataExchangeClient> , uç nokta yapılandırma adı veya meta veri adresini belirterek yeni bir nesne oluşturun.  
  
2. ' İ gereksinimlerinize uyacak şekildeyapılandırın.<xref:System.ServiceModel.Description.MetadataExchangeClient> Örneğin, meta veri istenirken kullanılacak kimlik bilgilerini belirtebilir, meta veri başvurularının nasıl çözümlendiğini denetleyebilir ve meta veri isteğinin zaman aşımına <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> uğramadan önce ne kadar süre geri dönmesi gerektiğini denetlemek için özelliğini ayarlayabilirsiniz.  
  
3. Yöntemlerin birini çağırarak alınan meta verileri içeren nesneyiedinin.<xref:System.ServiceModel.Description.MetadataSet> <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ' İ oluştururken açıkça bir adres belirttiyseniz <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , <xref:System.ServiceModel.Description.MetadataExchangeClient>yalnızca bağımsız değişken alan aşırı yüklemeyi kullanabileceğinizi unutmayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, meta veri dosyalarını indirmek <xref:System.ServiceModel.Description.MetadataExchangeClient> ve listelemek için nasıl kullanılacağını gösterir.  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kod örneğini derlemek için, System. ServiceModel. dll derlemesine başvurmanız ve <xref:System.ServiceModel.Description> ad alanını içeri aktarmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
