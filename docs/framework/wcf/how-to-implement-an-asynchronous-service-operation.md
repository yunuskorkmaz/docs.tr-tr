---
title: 'Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: b706ec49db123f33b3fc1ab0f420ed9a47e32f67
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320949"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama
Windows Communication Foundation (WCF) uygulamalarında, bir hizmet işlemi, istemciye dikte etmeden zaman uyumsuz veya eşzamanlı olarak uygulanabilir. Örneğin, zaman uyumsuz hizmet işlemleri zaman uyumlu olarak çağrılabilir ve zaman uyumlu hizmet işlemleri zaman uyumsuz olarak çağrılabilir. İstemci uygulamasında bir işlemin zaman uyumsuz olarak nasıl çağrılacağını gösteren bir örnek için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](./feature-details/how-to-call-wcf-service-operations-asynchronously.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](designing-service-contracts.md) ve zaman [uyumlu ve zaman uyumsuz işlemler](synchronous-and-asynchronous-operations.md) Bu konu, zaman uyumsuz bir hizmet işleminin temel yapısını açıklar, kod tamamlanmaz. Hem hizmet hem de istemci taraflarından oluşan tüm bir örnek için bkz. [zaman uyumsuz](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Zaman uyumsuz olarak bir hizmet işlemi uygulama  
  
1. Hizmet sözleşmeniz sırasında, .NET zaman uyumsuz tasarım yönergelerine göre zaman uyumsuz bir yöntem çifti bildirin. @No__t-0 yöntemi bir parametre, geri çağırma nesnesi ve bir durum nesnesi alır ve bir <xref:System.IAsyncResult?displayProperty=nameWithType> ve eşleşen `End` yöntemi döndürür ve <xref:System.IAsyncResult?displayProperty=nameWithType> alır ve döndürülen değeri döndürür. Zaman uyumsuz çağrılar hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama tasarım desenleri](https://go.microsoft.com/fwlink/?LinkId=248221).  
  
2. Zaman uyumsuz yöntem çiftinin `Begin` yöntemini <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> özniteliğiyle işaretleyin ve <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> özelliğini `true` olarak ayarlayın. Örneğin, aşağıdaki kod 1 ve 2. adımları gerçekleştirir.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. Zaman uyumsuz tasarım yönergelerine göre hizmet sınıfınızda `Begin/End` Yöntem çiftini uygulayın. Örneğin, aşağıdaki kod örneğinde bir dizenin, zaman uyumsuz hizmet işleminin hem `Begin` hem de `End` bölümlerinde konsola yazıldığı bir uygulama gösterilmektedir ve `End` işleminin dönüş değeri istemciye döndürülür. Tüm kod örneği için örnek bölümüne bakın.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri şunu gösterir:  
  
1. İle bir hizmet sözleşmesi arabirimi:  
  
    1. Zaman uyumlu `SampleMethod` işlemi.  
  
    2. Zaman uyumsuz bir `BeginSampleMethod` işlemi.  
  
    3. Zaman uyumsuz bir `BeginServiceAsyncMethod` @ no__t-1 @ no__t-2 işlem çifti.  
  
2. @No__t-0 nesnesi kullanan bir hizmet uygulamasıdır.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Sözleşmeleri Tasarlama](designing-service-contracts.md)
- [Zaman Uyumlu ve Zaman Uyumsuz İşlemler](synchronous-and-asynchronous-operations.md)
