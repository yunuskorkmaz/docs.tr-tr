---
title: "Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: afc08d08a8843460972daf259027475cbbc10b66
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma
Bu konu hizmet uç noktaları koleksiyona meta verileri alma ve içinde tanımlanan Hizmeti'yle açıklanmaktadır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Bu konu hizmet ve çağrıları sonra meta verileri içe aktaran bir istemci uygulaması oluşturmak nasıl Göster `Add` hizmette yöntemi.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Hizmet uç noktalarına meta verileri içe aktarmak için  
  
1.  Bildirme bir <xref:System.ServiceModel.EndpointAddress> nesne ve ile Tekdüzen Kaynak Tanımlayıcısı (URI) hizmeti meta veri değişimi (MEX) adresi için başlatılamıyor.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  Oluşturma bir <xref:System.ServiceModel.Description.MetadataExchangeClient>, MEX adresi ve çağrı geçen <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. Bu hizmeti meta verilerini alır.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  Oluşturma bir <xref:System.ServiceModel.Description.WsdlImporter>, daha önce listelene meta verileri ve çağrı geçen <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. Bu koleksiyonu oluşturur <xref:System.ServiceModel.Description.ContractDescription> nesneleri. Ayrıca çağırabilirsiniz <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> veya <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, gereksinimlerinize bağlı.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  Meta verileri içe aktardıktan sonra istemci kanal oluşturmak veya meta verilerini dışa aktarmak mümkün olmaz. Hiçbir tür bilgiler bu noktada kullanılamaz olmasıdır. Tür bilgileri gerçekte hizmetiyle etkileşim veya meta verilerini dışa aktarmak için gereklidir. Tür bilgileri oluşturmak için adım 4 ve 5 gösterilen kodu oluşturmak gerekir. Alternatif olarak, kullanabileceğinizi <xref:System.ServiceModel.Description.MetadataResolver> yardımcı sınıfı. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: bağlama meta verilerini dinamik olarak almak için MetadataResolver kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4.  Her sözleşme için tür bilgisi oluşturur.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  Artık bu bilgileri kullanabilirsiniz. Aşağıdaki örnek, C# kaynak kodu oluşturur.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veriler](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)
