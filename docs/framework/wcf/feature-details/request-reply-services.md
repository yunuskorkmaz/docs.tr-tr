---
title: İstek-Yanıt Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: a8d9ee30df5198335b15d2d7130d853f4dd73a18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516661"
---
# <a name="request-reply-services"></a>İstek-Yanıt Hizmetleri
İstek-yanıt Hizmetleri işlem anlaşması Windows Communication Foundation (WCF) varsayılan türüdür. İstemcilerin hizmet işlemlerine aramaları yapmak ve hizmetten bir yanıt bekler. Bir hizmet işlemi çağrısına ya da zaman uyumlu olarak gerçekleştirebileceğiniz, istemci kadar engeller, hizmet veya çağrısı süreleri bir yanıt alır veya zaman uyumsuz olarak, istemci bir hizmet işlemi çağrıda burada çalışmaya devam eder ve alır başka bir iş parçacığında hizmetinden gelen yanıt.  
  
 İstek-yanıt hizmeti sözleşme oluşturmak için hizmet sözleşmesini tanımlama ve uygulama <xref:System.ServiceModel.OperationContractAttribute> aşağıdaki örnek kodda gösterildiği gibi her işlem için sınıf.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Ayarlamak zorunda değilsiniz <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini `false` çünkü bu varsayılan davranışı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Tek Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [Çift Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)
