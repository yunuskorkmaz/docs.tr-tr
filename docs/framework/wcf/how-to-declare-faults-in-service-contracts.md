---
title: 'Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 6f08ef6eb62b31b0969779d51d0a068145a23fc0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971962"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme

Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur. Ancak Windows Communication Foundation (WCF) uygulamalarında, hizmet sözleşmeleri, hizmet sözleşmesinde SOAP hataları bildirerek istemcilere hangi hata bilgilerinin döndürüleceğini belirtir. Özel durumlar ve hatalar arasındaki ilişkiye genel bakış için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>SOAP hatası belirten bir hizmet sözleşmesi oluşturma

1. En az bir işlem içeren bir hizmet sözleşmesi oluşturun. Bir örnek için bkz [. nasıl yapılır: Bir hizmet sözleşmesi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)tanımlayın.

2. Hangi istemcilere bildirilmesi beklendiğini belirten bir hata koşulu içerebilen bir işlem seçin. İstemcilere SOAP hataları döndürmekte olan hata koşullarının belirlenmesi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).

3. <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> Seçili işleme uygulayın ve oluşturucuya seri hale getirilebilir bir hata türü geçirin. Serileştirilebilir türler oluşturma ve kullanma hakkında ayrıntılı bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Aşağıdaki örnekte, `SampleMethod` işlemin bir `GreetingFault`ile sonuçlanabileceğini belirtme gösterilmektedir.

     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. Sözleşmede hata koşullarını ileten tüm işlemler için adım 2 ve 3 ' ü tekrarlayın.

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Belirtilen SOAP hatasını döndürmek için bir Işlem uygulama
 Bir işlem, bir hata koşulunu çağıran bir uygulamayla iletmek için belirli bir SOAP hatasının döndürülüp döndürülmeyeceğini (önceki yordamda olduğu gibi) belirledikten sonra, bir sonraki adım bu belirtimi uygulamaktır.

### <a name="throw-the-specified-soap-fault-in-the-operation"></a>İşlemde belirtilen SOAP hatasını oluştur

1. Bir işlemde <xref:System.ServiceModel.FaultContractAttribute>belirtilen bir hata koşulu oluştuğunda, belirtilen SOAP hatasının tür parametresi olduğu <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> yeni bir oluştur. Aşağıdaki örnek, bir önceki yordamda ve aşağıdaki `GreetingFault` kod bölümünde `SampleMethod` gösterildiği içindeki ' ın nasıl oluşturulacağını gösterir.

     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `GreetingFault` `SampleMethod` işlem için bir öğesini belirten tek bir işlemin bir uygulamasını gösterir.

[!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
