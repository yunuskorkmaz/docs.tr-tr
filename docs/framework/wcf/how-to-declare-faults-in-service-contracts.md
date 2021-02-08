---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: hizmet sözleşmelerinde hata bildirme'
title: 'Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 1d83840386338747c983d8c4e9a788a452b9c4b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793265"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme

Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur. Ancak Windows Communication Foundation (WCF) uygulamalarında, hizmet sözleşmeleri, hizmet sözleşmesinde SOAP hataları bildirerek istemcilere hangi hata bilgilerinin döndürüleceğini belirtir. Özel durumlar ve hatalar arasındaki ilişkiye genel bakış için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>SOAP hatası belirten bir hizmet sözleşmesi oluşturma

1. En az bir işlem içeren bir hizmet sözleşmesi oluşturun. Bir örnek için bkz. [nasıl yapılır: hizmet sözleşmesi tanımlama](how-to-define-a-wcf-service-contract.md).

2. Hangi istemcilere bildirilmesi beklendiğini belirten bir hata koşulu içerebilen bir işlem seçin. İstemcilere SOAP hataları döndürmekte olan hata koşullarının belirlenmesi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).

3. <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>Seçili işleme uygulayın ve oluşturucuya seri hale getirilebilir bir hata türü geçirin. Serileştirilebilir türler oluşturma ve kullanma hakkında ayrıntılı bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](./feature-details/specifying-data-transfer-in-service-contracts.md). Aşağıdaki örnekte, `SampleMethod` işlemin bir ile sonuçlanabileceğini belirtme gösterilmektedir `GreetingFault` .

     [!code-csharp[FaultContractAttribute#4](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. Sözleşmede hata koşullarını ileten tüm işlemler için adım 2 ve 3 ' ü tekrarlayın.

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Belirtilen SOAP hatasını döndürmek için bir Işlem uygulama

 Bir işlem, bir hata koşulunu çağıran bir uygulamayla iletmek için belirli bir SOAP hatasının döndürülüp döndürülmeyeceğini (önceki yordamda olduğu gibi) belirledikten sonra, bir sonraki adım bu belirtimi uygulamaktır.

### <a name="throw-the-specified-soap-fault-in-the-operation"></a>İşlemde belirtilen SOAP hatasını oluştur

1. Bir <xref:System.ServiceModel.FaultContractAttribute> işlemde belirtilen bir hata koşulu oluştuğunda, <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> belirtilen SOAP hatasının tür parametresi olduğu yeni bir oluştur. Aşağıdaki örnek, bir `GreetingFault` `SampleMethod` önceki yordamda ve aşağıdaki kod bölümünde gösterildiği içindeki ' ın nasıl oluşturulacağını gösterir.

     [!code-csharp[FaultContractAttribute#5](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, işlem için bir öğesini belirten tek bir işlemin bir uygulamasını gösterir `GreetingFault` `SampleMethod` .

[!code-csharp[FaultContractAttribute#1](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
