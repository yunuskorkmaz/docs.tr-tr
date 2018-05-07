---
title: 'Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 142ad26702f0732bc5103e29d5a44bc57ab37625
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme
Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar. Windows Communication Foundation (WCF) uygulamalarında hangi hata bilgilerini hizmet sözleşmesi SOAP Hataları bildirerek istemcilere döndürülen Hizmet sözleşmeleri ancak belirtin. Özel durum ve hataları arasındaki ilişkiyi genel bakış için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Bir SOAP hatasını belirtir bir hizmet sözleşmesi oluşturma  
  
1.  En az bir işlem içeren bir hizmet sözleşmesini oluşturun. Bir örnek için bkz: [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Bir hata durumu hakkında bildirim almak istemcileri bekleyebilirsiniz belirtebilirsiniz bir işlem seçin. İstemcilere SOAP hataları döndürüyor, hata koşullarını justify karar vermek için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
3.  Geçerli bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> seçili işlemi ve Oluşturucusu geçişine seri hale getirilebilir bir arıza yazın. Oluşturma ve seri hale getirilebilir türler kullanma hakkında daha fazla bilgi için bkz [hizmet sözleşmelerinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Aşağıdaki örnek, belirten gösterilmektedir `SampleMethod` işlemi sonuçlanabilir bir `GreetingFault`.  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  Hata koşulları istemcilere iletişim kuran tüm işlemleri sözleşmesindeki için 2 ve 3. adımları yineleyin.  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Belirtilen bir SOAP hatası döndürmek için bir işlem uygulama  
 Bir işlem belirli bir SOAP hatası (yukarıdaki yordamı olduğu gibi) çağıran bir uygulama bir hata koşuluna iletişim kurmak için döndürülebilecek olduğunu belirttiğinde, sonraki adım, belirtimi uygulamaktır.  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Belirtilen bir SOAP hatası işlemde throw  
  
1.  Zaman bir <xref:System.ServiceModel.FaultContractAttribute>-yeni bir durum, bir işlem içinde belirtilen hata koşulu ortaya <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> burada belirtilen bir SOAP hatası, tür parametresi. Aşağıdaki örnek throw gösterilmektedir `GreetingFault` içinde `SampleMethod` önceki yordamda ve aşağıdaki kod bölümünde gösterilir.  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde belirten tek bir işlem uygulaması gösterir bir `GreetingFault` için `SampleMethod` işlemi.  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
