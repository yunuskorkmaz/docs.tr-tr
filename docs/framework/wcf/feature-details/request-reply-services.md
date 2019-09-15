---
title: İstek-Yanıt Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991137"
---
# <a name="request-reply-services"></a>İstek-Yanıt Hizmetleri
İstek-yanıt Hizmetleri, Windows Communication Foundation (WCF) ' de varsayılan işlem anlaşması türüdür. İstemciler hizmet işlemlerine çağrı yapar ve hizmetten bir yanıt bekler. İstemci, hizmetten veya çağrı sürelerinin bir yanıtını alana kadar engellediği veya zaman uyumsuz olarak, istemcinin hizmet işlemine bir çağrı yaptığı, çalışmaya devam ettiği ve bunu aldığı zaman uyumsuz olarak bir hizmet işlemine çağrı yapabilirsiniz. başka bir iş parçacığında hizmetten yanıt.  
  
 İstek-yanıt hizmet sözleşmesi oluşturmak için, hizmet sözleşmenizi tanımlayın ve aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.OperationContractAttribute> gibi her bir işleme sınıfı uygulayın.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Bu varsayılan davranış olduğundan, <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini olarak `false` ayarlamanız gerekmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tek Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [Çift Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)
