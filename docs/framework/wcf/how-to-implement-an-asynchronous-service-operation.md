---
title: 'Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: eeea3933446a401ad8f556dc546f54122a19a8b5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723892"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama
Windows Communication Foundation (WCF) uygulamalar, bir hizmet işlemi zaman uyumlu veya zaman uyumsuz olarak nasıl çağıran istemciye dikte olmadan uygulanabilir. Örneğin, zaman uyumsuz hizmet işlemlerini zaman uyumlu olarak arama ve zaman uyumlu hizmet işlemlerini zaman uyumsuz olarak çağrılabilir. İşlem bir istemci uygulamasında zaman uyumsuz olarak çağırma gösteren bir örnek için bkz [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md) ve [zaman uyumlu ve zaman uyumsuz işlemler](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). Bu konu zaman uyumsuz bir hizmet işlemi temel yapısını tanımlar, kod tam değil. Hem hizmet hem de istemci tarafında tam bir örnek için bkz. [zaman uyumsuz](https://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Zaman uyumsuz olarak bir hizmet işlemi uygulama  
  
1.  Hizmet sözleşmeniz .NET zaman uyumsuz tasarım yönergelerine göre bir zaman uyumsuz yöntem çifti bildirin. `Begin` Yöntemi, bir parametre, bir geri çağırma nesnesi ve durum nesnesi alır ve döndürür bir <xref:System.IAsyncResult?displayProperty=nameWithType> ile eşleşen bir `End` gereken yöntemini bir <xref:System.IAsyncResult?displayProperty=nameWithType> ve dönüş değeri döndürür. Zaman uyumsuz çağrılar hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama desenleri](https://go.microsoft.com/fwlink/?LinkId=248221).  
  
2.  İşareti `Begin` yöntemi ile zaman uyumsuz yöntem çiftinin <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> ayarlayın ve öznitelik <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> özelliğini `true`. Örneğin, aşağıdaki kod, 1 ve 2. adımları gerçekleştirir.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  Uygulama `Begin/End` hizmet sınıfınızda zaman uyumsuz tasarım yönergelerine göre yöntemi çifti. Örneğin, aşağıdaki kod örneği, bir dize yazılır hem de konsol uygulaması gösterir `Begin` ve `End` uyumsuz bir hizmet işlemi ve dönüş değeri bölümlerini `End` işlemdir istemciye döndürülen. İçin tam kod örneği, örnek bölümüne bakın.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri göster:  
  
1.  Hizmet sözleşme arabirimi ile:  
  
    1.  Eş zamanlı `SampleMethod` işlemi.  
  
    2.  Zaman uyumsuz `BeginSampleMethod` işlemi.  
  
    3.  Zaman uyumsuz `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` işlemi çifti.  
  
2.  Bir hizmet uygulamasını kullanarak bir <xref:System.IAsyncResult?displayProperty=nameWithType> nesne.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet Sözleşmeleri Tasarlama](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
