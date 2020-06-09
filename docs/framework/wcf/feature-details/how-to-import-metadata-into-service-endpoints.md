---
title: 'Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 1de316b8e91739d5e3e24ff960e2cdfb33cc7fab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597065"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma
Bu konuda, bir hizmet uç noktası koleksiyonuna meta verilerin nasıl içeri aktarılacağı ve [Başlarken](../samples/getting-started-sample.md)' de tanımlanan hizmetin nasıl kullanılacağı açıklanmaktadır. Bu konuda, hizmetten meta verileri içeri aktaran ve sonra hizmette yöntemi çağıran bir istemci uygulamasının nasıl oluşturulacağı gösterilmektedir `Add` .  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Meta verileri hizmet uç noktalarına aktarmak için  
  
1. Bir <xref:System.ServiceModel.EndpointAddress> nesne bildirin ve hizmetin meta veri değişimi (MEX) adresi Için Tekdüzen Kaynak tanımlayıcısı (URI) ile başlatın.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. Bir oluşturun <xref:System.ServiceModel.Description.MetadataExchangeClient> , MEX adresini geçirerek ve çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> . Bu, hizmetten meta verileri alır.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <xref:System.ServiceModel.Description.WsdlImporter>Daha önce alınan meta verileri geçirerek bir oluşturun ve çağırın <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> . Bu bir nesne koleksiyonu oluşturur <xref:System.ServiceModel.Description.ContractDescription> . <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> Gereksinimlerinize bağlı olarak, veya öğesini de çağırabilirsiniz.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > Meta verileri içeri aktardıktan sonra, bir istemci kanalı oluşturamaz veya meta verileri dışarı aktarabilirsiniz. Bunun nedeni, bu noktada hiçbir tür bilgisinin mevcut olmaması değildir. Hizmet veya dışarı aktarma meta verileriyle etkileşim kurmak için tür bilgileri gereklidir. Tür bilgilerini oluşturmak için, 4 ve 5. adımlarda gösterilen kodu oluşturmanız gerekir. Alternatif olarak, <xref:System.ServiceModel.Description.MetadataResolver> yardımcı sınıfını kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: MetadataResolver kullanarak bağlama meta verilerini dinamik olarak elde](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)edin.  
  
4. Her sözleşme için tür bilgisi oluşturun.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. Artık bu bilgileri kullanabilirsiniz. Aşağıdaki örnek C# kaynak kodu oluşturur.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](metadata.md)
- [Başlarken](../samples/getting-started-sample.md)
