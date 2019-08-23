---
title: 'Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: dce65c31134c211c134cbae2b9bd8296f74b1627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930721"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma
Bu konuda, bir hizmet uç noktası koleksiyonuna meta verilerin nasıl içeri aktarılacağı ve [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' de tanımlanan hizmetin nasıl kullanılacağı açıklanmaktadır. Bu konuda, hizmetten meta verileri içeri aktaran ve sonra hizmette `Add` yöntemi çağıran bir istemci uygulamasının nasıl oluşturulacağı gösterilmektedir.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Meta verileri hizmet uç noktalarına aktarmak için  
  
1. Bir <xref:System.ServiceModel.EndpointAddress> nesne bildirin ve hizmetin meta veri değişimi (MEX) adresi için Tekdüzen Kaynak tanımlayıcısı (URI) ile başlatın.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. Bir <xref:System.ServiceModel.Description.MetadataExchangeClient>oluşturun, MEX adresini geçirerek ve çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. Bu, hizmetten meta verileri alır.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. Daha önce <xref:System.ServiceModel.Description.WsdlImporter>alınan meta verileri geçirerek bir oluşturun ve çağırın. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> Bu bir <xref:System.ServiceModel.Description.ContractDescription> nesne koleksiyonu oluşturur. Gereksinimlerinize bağlı olarak, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> veya <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>öğesini de çağırabilirsiniz.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > Meta verileri içeri aktardıktan sonra, bir istemci kanalı oluşturamaz veya meta verileri dışarı aktarabilirsiniz. Bunun nedeni, bu noktada hiçbir tür bilgisinin mevcut olmaması değildir. Hizmet veya dışarı aktarma meta verileriyle etkileşim kurmak için tür bilgileri gereklidir. Tür bilgilerini oluşturmak için, 4 ve 5. adımlarda gösterilen kodu oluşturmanız gerekir. Alternatif olarak, <xref:System.ServiceModel.Description.MetadataResolver> yardımcı sınıfını kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Bağlama meta verilerini dinamik olarak](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)almak Için MetadataResolver kullanın.  
  
4. Her sözleşme için tür bilgisi oluşturun.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. Artık bu bilgileri kullanabilirsiniz. Aşağıdaki örnek kaynak kodu C# oluşturur.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)
