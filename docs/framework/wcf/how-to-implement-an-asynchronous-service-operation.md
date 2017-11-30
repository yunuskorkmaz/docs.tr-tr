---
title: "Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 65cd45a2510aa43c3f0c58a7cbf78c13e47d821e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama
İçinde [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulamalar, bir hizmet işlemi uygulanabilir zaman uyumsuz veya zaman uyumlu olarak bunu nasıl istemciyi dikte olmadan. Örneğin, zaman uyumsuz hizmet işlemlerini zaman uyumlu çağırma ve zaman uyumlu hizmet işlemlerini zaman uyumsuz olarak çağrılabilir. Bir istemci uygulamasında zaman uyumsuz bir işlem çağırma gösteren örnek için bkz: [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]zaman uyumlu ve zaman uyumsuz işlemler bkz [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md) ve [zaman uyumlu ve zaman uyumsuz işlemleri](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). Bu konuda bir zaman uyumsuz hizmet işlemi temel yapısını tanımlar, kod tam değil. Hem hizmet hem de istemci tarafında tam bir örnek için bkz: [zaman uyumsuz](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Zaman uyumsuz olarak bir hizmet işlemi uygulama  
  
1.  Hizmet sözleşmesini .NET zaman uyumsuz tasarım yönergelerine göre bir zaman uyumsuz yöntem çiftinin bildirin. `Begin` Yöntemi bir parametre, bir geri çağırma nesnesi ve bir durum nesnesi alır ve döndüren bir <xref:System.IAsyncResult?displayProperty=nameWithType> ve eşleşen bir `End` alır yöntemi bir <xref:System.IAsyncResult?displayProperty=nameWithType> ve dönüş değerini döndürür. Zaman uyumsuz çağrılar hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama tasarım desenleri](http://go.microsoft.com/fwlink/?LinkId=248221).  
  
2.  İşareti `Begin` yöntemi ile zaman uyumsuz yöntem çiftinin <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> özniteliği ve ayarlayın <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> özelliğine `true`. Örneğin, aşağıdaki kodu, 1 ve 2. adımları gerçekleştirir.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  Uygulama `Begin/End` zaman uyumsuz tasarım yönergelerine göre hizmet sınıfınızda yöntemi çifti. Örneğin, aşağıdaki kod örneği, bir dize yazılır hem de konsol uygulaması gösterir `Begin` ve `End` zaman uyumsuz hizmet işlemi ve dönüş değerini bölümlerini `End` işlemi istemciye döndürülen. Tam kod örneği için örnek bölümüne bakın.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri göster:  
  
1.  Hizmet sözleşme arabirimi ile:  
  
    1.  Bir zaman uyumlu `SampleMethod` işlemi.  
  
    2.  Zaman uyumsuz bir `BeginSampleMethod` işlemi.  
  
    3.  Zaman uyumsuz bir `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` işlemi çifti.  
  
2.  Bir hizmet uygulamasını kullanarak bir <xref:System.IAsyncResult?displayProperty=nameWithType> nesnesi.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Zaman uyumlu ve zaman uyumsuz işlemler](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
