---
description: 'Hakkında daha fazla bilgi edinin: meta veriler alma'
title: Meta Verileri Alma
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: 35068c9ad532b3a48eabda03274b0d53fcc94694
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632821"
---
# <a name="retrieving-metadata"></a>Meta Verileri Alma

Meta veri alma, WS-MetadataExchange (MEX) meta veri uç noktası veya HTTP/GET meta veri uç noktası gibi meta veri uç noktasından meta veri isteme ve alma işlemidir.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Svcutil.exe kullanarak komut satırından meta verileri alma  

 WS-MetadataExchange veya HTTP/GET isteklerini kullanarak, [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanarak ve `/target:metadata` anahtarı ve bir adresi geçirerek hizmet meta verilerini alabilirsiniz. Svcutil.exe, belirtilen adresteki meta verileri indirir ve dosyayı diske kaydeder. Svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> , dahili olarak bir örneği kullanır ve adı, <xref:System.ServiceModel.Description.IMetadataExchange> giriş olarak Svcutil.exe geçirilen adresin düzeniyle eşleşen uç nokta yapılandırması yapılandırmadan yüklenir.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>MetadataExchangeClient kullanarak meta verileri program aracılığıyla alma  

 Windows Communication Foundation (WCF), WS-MetadataExchange ve HTTP/GET istekleri gibi standartlaştırılmış protokolleri kullanarak hizmet meta verilerini alabilir. Bu protokollerin her ikisi de tür tarafından desteklenir <xref:System.ServiceModel.Description.MetadataExchangeClient> . <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Meta veri uç noktası ve isteğe bağlı bir bağlama için bir adres sağlayarak türü kullanarak hizmet meta verilerini alırsınız. Bir örnek tarafından kullanılan bağlama <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> statik sınıftan varsayılan bağlamalardan biri <xref:System.ServiceModel.Description.MetadataExchangeBindings> , Kullanıcı tarafından sağlanan bir bağlama veya sözleşmenin bir uç nokta yapılandırmasından yüklenen bir bağlama olabilir `IMetadataExchange` . <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Ayrıca, türü kullanılarak meta VERILERE http url başvurularını da çözümleyebilir <xref:System.Net.HttpWebRequest> .  
  
 Varsayılan olarak, bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örnek tek bir <xref:System.ServiceModel.ChannelFactory> örneğe bağlanır. <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>Tarafından kullanılan örneği <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> sanal yöntemi geçersiz kılarak değiştirebilir veya değiştirebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> . Benzer şekilde, <xref:System.Net.HttpWebRequest> <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> sanal yöntemi GEÇERSIZ kılarak http/get istekleri yapmak için tarafından kullanılan örneği değiştirebilir veya değiştirebilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> .  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma](how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Meta veri belgelerini indirmek için Svcutil.exe nasıl kullanacağınızı gösterir.  
  
 [Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>Çalışma zamanında dinamik olarak bağlama meta verilerini elde etmek için ' nin nasıl kullanılacağını gösterir.  
  
 [Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma](how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Meta veri dosyalarını <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> dosyalara yazmak için veya diğer kullanımlar için nesneleri içeren bir nesneye indirmek için sınıfını nasıl kullanacağınızı gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataExchangeClient>
