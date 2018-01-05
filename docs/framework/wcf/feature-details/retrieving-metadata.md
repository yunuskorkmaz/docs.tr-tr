---
title: Meta Verileri Alma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc96c585ba55fbf63283d7cb23fae5b364b0465
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-metadata"></a>Meta Verileri Alma
Meta veri alma isteme ve WS-MetadataExchange (MEX) meta veri uç noktasına veya bir HTTP/GET meta veri uç noktası gibi bir meta veri uç noktasından meta verilerini alma işlemidir.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Svcutil.exe kullanarak komut satırından meta verilerini alma  
 WS-MetadataExchange veya HTTP/GET isteklerini kullanarak hizmeti meta verileri alabilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı ve geçirme `/target:metadata` anahtarı ve bir adres. Svcutil.exe belirtilen adresteki meta verileri indirir ve dosyayı diske kaydeder. Svcutil.exe kullanan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> dahili örneği ve yükler yapılandırmasından <xref:System.ServiceModel.Description.IMetadataExchange> Svcutil.exe giriş olarak geçirilen adı ile eşleşen adres düzeni uç nokta yapılandırması.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Program aracılığıyla MetadataExchangeClient kullanma meta verilerini alma  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]WS-MetadataExchange ve HTTP/GET istekleri gibi standart protokoller kullanılarak hizmeti meta verileri alabilir. Bu protokollerin her ikisi de tarafından desteklenen <xref:System.ServiceModel.Description.MetadataExchangeClient> türü. Hizmet meta verileri kullanarak almak <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> meta veri uç noktası ve isteğe bağlı bir bağlama için bir adres sağlayarak türü. Bağlama tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örnek varsayılan bağlantılardan biri olabilir <xref:System.ServiceModel.Description.MetadataExchangeBindings> statik sınıf, bir kullanıcı tarafından sağlanan bağlama veya bir bağlama yüklenen bir uç nokta yapılandırması için gelen `IMetadataExchange` sözleşme. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Meta verileri kullanarak HTTP URL'si başvurular de çözebilirsiniz <xref:System.Net.HttpWebRequest> türü.  
  
 Varsayılan olarak, bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> örneğinin tek bir bağlı <xref:System.ServiceModel.ChannelFactory> örneği. Değiştirin veya Değiştir <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> örneği tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> kılarak <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> sanal yöntemi. Benzer şekilde, değiştirin ya da değiştirebileceğiniz <xref:System.Net.HttpWebRequest> örneği tarafından kullanılan bir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> HTTP/GET istekleri geçersiz kılarak yapmak için <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> sanal yöntemi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Meta veri belgelerini indirmek için svcutil.exe kullanma gösterilmektedir.  
  
 [Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Nasıl kullanılacağı ortaya <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> çalışma zamanında dinamik olarak bağlama meta verilerini almak için.  
  
 [Nasıl yapılır: Meta Verileri Almak için MetadataExchangeClient Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Nasıl kullanılacağını göstermektedir <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> meta veri dosyalarıyla indirmek için sınıf bir <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> içeren nesne <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> dosyalara veya diğer kullanımlar için yazılacak nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>
