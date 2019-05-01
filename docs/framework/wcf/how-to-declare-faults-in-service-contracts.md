---
title: 'Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 0e173f71201d5f98a04d2ad922469e4ff6666681
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929291"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme
Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar. Windows Communication Foundation (WCF) uygulamalar, ancak hangi hata bilgilerini hizmet sözleşmesi, SOAP Hataları bildirerek istemcilere döndürülen hizmet sözleşmelerini belirtin. Özel durumlar ve hatalar arasındaki ilişkiyi genel bakış için bkz. [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Bir SOAP hatasını belirten bir hizmet sözleşmesi oluşturma  
  
1. En az bir işlem içeren bir hizmet sözleşmesi oluşturun. Bir örnek için bkz [nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. Bir hata durumu hakkında bildirim almak istemcileri bekleyebileceğiniz belirtebileceğiniz bir işlem seçin. Hangi hata koşulları istemcilere SOAP hataları döndürüyor Yasla karar vermek için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
3. Geçerli bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> seçili işlemi ve oluşturucuya seri hale getirilebilir bir hata türü geçişi. Oluşturma ve serializable türler kullanma hakkında daha fazla ayrıntı için bkz. [hizmet sözleşmelerinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Aşağıdaki örnek olduğunu belirtmek gösterilmektedir `SampleMethod` işlemi sonuçlanabilir bir `GreetingFault`.  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4. Sözleşme istemcilere hata koşulları iletişim kuran tüm işlemler için 2 ve 3. adımları tekrarlayın.  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Belirtilen SOAP hatası döndürmek için bir işlem uygulama  
 Bir işlemi belirli bir SOAP hatası (yukarıdaki yordamı gibi) bir hata koşulu çağıran bir uygulama için iletişim kurmak için döndürülebilir olduğunu belirttiğinde, sonraki adımda bu belirtimini uygulamaktır.  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Belirtilen bir SOAP hatası işlem içinde özel durum  
  
1. Olduğunda bir <xref:System.ServiceModel.FaultContractAttribute>-yeni bir durum, bir işlem belirtilen hata koşulu ortaya <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> tür parametresi olduğu belirtilen bir SOAP hatası. Aşağıdaki örnekte throw gösterilmektedir `GreetingFault` içinde `SampleMethod` önceki yordamdaki ve aşağıdaki kod bölümünde gösterilir.  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği belirten tek bir işlem uygulaması gösterir bir `GreetingFault` için `SampleMethod` işlemi.  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
