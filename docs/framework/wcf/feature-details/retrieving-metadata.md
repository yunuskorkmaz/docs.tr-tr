---
title: Meta Verileri Alma
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: bb415d88c2bae75cb16aa137bdf867eb463afa63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748310"
---
# <a name="retrieving-metadata"></a>Meta Verileri Alma
Meta veri alımı isteme ve WS-MetadataExchange (MEX) meta veri uç noktası veya bir HTTP/GET meta veri uç noktası gibi bir meta veri uç noktasından meta verilerini alma işlemidir.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Komut satırından Svcutil.exe kullanarak meta verileri alma  
 WS-MetadataExchange veya HTTP/GET isteklerini kullanarak hizmet meta verileri alabilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı ve geçirme `/target:metadata` anahtarı ve bir adres. Svcutil.exe belirtilen adreste meta verileri indirir ve dosyayı diske kaydeder. Svcutil.exe kullanan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> dahili olarak örneği ve yapılandırmasından yükler <xref:System.ServiceModel.Description.IMetadataExchange> Svcutil.exe giriş olarak geçirilen uç nokta Yapılandırması adı ile eşleşen adresi düzeni.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>MetadataExchangeClient kullanarak program aracılığıyla meta verilerini alma  
 Windows Communication Foundation (WCF), WS-MetadataExchange ve HTTP/GET istekleri gibi standart protokoller kullanarak hizmet meta verileri alabilir. Bu protokollerin her ikisi de tarafından desteklenen <xref:System.ServiceModel.Description.MetadataExchangeClient> türü. Hizmet meta verileri kullanarak almak <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> meta veri uç noktası ve isteğe bağlı bir bağlama için bir adres sağlayarak türü. Bağlama tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örneği varsayılan bağlantılardan biri olabilir <xref:System.ServiceModel.Description.MetadataExchangeBindings> statik sınıf, bir kullanıcı tarafından sağlanan bağlama veya bir bağlama yüklenen bir uç nokta yapılandırması için gelen `IMetadataExchange` sözleşme. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Meta verileri kullanarak HTTP URL'si başvurular da çözebilirsiniz <xref:System.Net.HttpWebRequest> türü.  
  
 Varsayılan olarak, bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örneği için tek bir bağlı <xref:System.ServiceModel.ChannelFactory> örneği. Değiştirin veya değiştirebileceğiniz <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> örneği tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> kılarak <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> sanal yöntem. Benzer şekilde, değiştirin veya değiştirebileceğiniz <xref:System.Net.HttpWebRequest> örneği tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> geçersiz kılarak HTTP/GET isteğinde bulunmak için <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> sanal yöntem.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Meta veri belgelerini indirmek için svcutil.exe kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Meta veri belgelerini indirmek için svcutil.exe kullanma işlemi gösterilmektedir.  
  
 [Nasıl yapılır: Dinamik olarak meta verilerini almak için MetadataResolver kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Nasıl kullanılacağını gösteren <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> zamanında dinamik olarak bağlama meta verilerini edinmek için.  
  
 [Nasıl yapılır: Meta verileri almak için MetadataExchangeClient kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Nasıl kullanılacağını gösteren <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> sınıfı içine meta veri dosyaları indirmek için bir <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> içeren nesne <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> dosyaları veya diğer kullanımlar için yazılacak nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataExchangeClient>
