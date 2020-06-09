---
title: İstek-Yanıt Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: df42f3fa8f5a15572987b0d4859856c7f838e632
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586240"
---
# <a name="request-reply-services"></a>İstek-Yanıt Hizmetleri
İstek-yanıt Hizmetleri, Windows Communication Foundation (WCF) ' de varsayılan işlem anlaşması türüdür. İstemciler hizmet işlemlerine çağrı yapar ve hizmetten bir yanıt bekler. İstemci, hizmetten veya çağrı sürelerinin bir yanıtını alana kadar engellediği veya zaman uyumsuz olarak, istemcinin hizmet işlemine bir çağrı yaptığı, çalışmaya devam ettiği ve diğer bir iş parçacığında hizmetten gelen yanıtı aldığı zaman uyumsuz olarak bir hizmet işlemine çağrı gerçekleştirebilirsiniz.  
  
 İstek-yanıt hizmet sözleşmesi oluşturmak için, hizmet sözleşmenizi tanımlayın ve <xref:System.ServiceModel.OperationContractAttribute> Aşağıdaki örnek kodda gösterildiği gibi her bir işleme sınıfı uygulayın.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>Bu varsayılan davranış olduğundan, özelliğini olarak ayarlamanız gerekmez `false` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tek Yönlü Hizmetler](one-way-services.md)
- [Çift Yönlü Hizmetler](duplex-services.md)
