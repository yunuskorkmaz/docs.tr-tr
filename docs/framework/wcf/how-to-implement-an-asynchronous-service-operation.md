---
title: 'Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama'
description: WFC 'de zaman uyumsuz bir hizmet işleminin yapısı hakkında bilgi edinin. Bir hizmet işlemi, zaman uyumsuz veya zaman uyumlu olarak uygulanabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 5f890bd5124e2353cecee37d163b7f2c65b87fde
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244637"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama
Windows Communication Foundation (WCF) uygulamalarında, bir hizmet işlemi, istemciye dikte etmeden zaman uyumsuz veya eşzamanlı olarak uygulanabilir. Örneğin, zaman uyumsuz hizmet işlemleri zaman uyumlu olarak çağrılabilir ve zaman uyumlu hizmet işlemleri zaman uyumsuz olarak çağrılabilir. İstemci uygulamasında bir işlemin zaman uyumsuz olarak nasıl çağrılacağını gösteren bir örnek için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](./feature-details/how-to-call-wcf-service-operations-asynchronously.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](designing-service-contracts.md) ve zaman [uyumlu ve zaman uyumsuz işlemler](synchronous-and-asynchronous-operations.md) Bu konu, zaman uyumsuz bir hizmet işleminin temel yapısını açıklar, kod tamamlanmaz. Hem hizmet hem de istemci taraflarından oluşan tüm bir örnek için bkz. [zaman uyumsuz](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Zaman uyumsuz olarak bir hizmet işlemi uygulama  
  
1. Hizmet sözleşmeniz sırasında, .NET zaman uyumsuz tasarım yönergelerine göre zaman uyumsuz bir yöntem çifti bildirin. `Begin`Yöntemi bir parametre, geri çağırma nesnesi ve bir durum nesnesi alır ve bir ve döndürür ve <xref:System.IAsyncResult?displayProperty=nameWithType> `End` dönüş değerini döndüren eşleşen bir yöntemi döndürür <xref:System.IAsyncResult?displayProperty=nameWithType> . Zaman uyumsuz çağrılar hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama tasarım desenleri](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
2. `Begin`Zaman uyumsuz yöntem çiftinin yöntemini <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> özniteliğiyle işaretleyin ve <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` . Örneğin, aşağıdaki kod 1 ve 2. adımları gerçekleştirir.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. `Begin/End`Zaman uyumsuz tasarım yönergelerine göre hizmet sınıfınızda Yöntem çiftini uygulayın. Örneğin, aşağıdaki kod örneği, bir dizenin hem zaman uyumsuz hizmet işleminin hem de her bölümünde konsola yazıldığı bir uygulamayı gösterir `Begin` `End` ve işlemin dönüş değeri `End` istemciye döndürülür. Tüm kod örneği için örnek bölümüne bakın.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri şunu gösterir:  
  
1. İle bir hizmet sözleşmesi arabirimi:  
  
    1. Zaman uyumlu bir `SampleMethod` işlem.  
  
    2. Zaman uyumsuz bir `BeginSampleMethod` işlem.  
  
    3. Zaman uyumsuz bir `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` işlem çifti.  
  
2. Bir nesne kullanan hizmet uygulamasıdır <xref:System.IAsyncResult?displayProperty=nameWithType> .  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Sözleşmeleri Tasarlama](designing-service-contracts.md)
- [Zaman Uyumlu ve Zaman Uyumsuz İşlemler](synchronous-and-asynchronous-operations.md)
