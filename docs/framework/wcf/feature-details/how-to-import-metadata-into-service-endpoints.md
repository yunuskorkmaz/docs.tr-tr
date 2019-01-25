---
title: 'Nasıl yapılır: Hizmet uç noktalarına meta verileri alma'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 5a6375f0a0b0f657401a1ac2254be942d4e618aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548683"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Nasıl yapılır: Hizmet uç noktalarına meta verileri alma
Bu konu başlığında, tanımlanan hizmet meta verileri, hizmet uç noktaları bir koleksiyona içe aktarma ve açıklanmaktadır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Bu konuda hizmet ve çağrıları meta veri aktaran bir istemci uygulamanın nasıl oluşturulacağını gösterir `Add` hizmette yöntemi.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Hizmet uç noktalarına meta verileri içeri aktarmak için  
  
1.  Bildirme bir <xref:System.ServiceModel.EndpointAddress> nesne ve ile Tekdüzen Kaynak Tanımlayıcısı (URI) hizmeti meta veri değişimi (MEX) adresi için başlatılamıyor.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  Oluşturma bir <xref:System.ServiceModel.Description.MetadataExchangeClient>, geçen MEX adresa ve çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. Bu hizmet meta verileri alır.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  Oluşturma bir <xref:System.ServiceModel.Description.WsdlImporter>, daha önce listelene meta verileri ve çağrı geçen <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. Bu işlem bir koleksiyonunu oluşturur. <xref:System.ServiceModel.Description.ContractDescription> nesneleri. Ayrıca çağırabilir <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> veya <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, ihtiyaçlarınıza bağlı.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  Meta verileri içeri aktardıktan sonra istemci bir kanal oluşturmak veya meta veri dışarı aktarmak mümkün olmayacaktır. Bu noktada kullanılabilir türü bilgi olmasıdır. Tür bilgilerini gerçekten hizmetiyle etkileşim kurmak veya meta veri dışarı aktarmak için gereklidir. Tür bilgisi üretmek için 4 ve 5. adımda gösterilen kodu oluşturmak gerekir. Alternatif olarak, kullanabileceğinizi <xref:System.ServiceModel.Description.MetadataResolver> yardımcı sınıfı. Daha fazla bilgi için [nasıl yapılır: Dinamik olarak meta verilerini almak için MetadataResolver kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4.  Her sözleşme için tür bilgisi oluşturur.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  Artık bu bilgileri kullanabilirsiniz. Aşağıdaki örnek oluşturur C# kaynak kodu.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)
