---
title: İstek-Yanıt Hizmetleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 8fe1343a4b3590622becf71f1167f4b19dbc67af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="request-reply-services"></a>İstek-Yanıt Hizmetleri
İstek-yanıt Hizmetleri işlemi sözleşme Windows Communication Foundation (WCF) varsayılan türüdür. İstemcileri hizmet işlemleri çağrı yapmak ve hizmetinden bir yanıt bekleyin. Bir hizmet işlemi çağrıları ya da zaman uyumlu olarak gerçekleştirebileceğiniz, kadar istemci engeller burada bu hizmetin veya çağrı süreleri bir yanıt alır veya zaman uyumsuz olarak, istemci hizmet işlemi için bir çağrı yapar burada çalışmaya devam eder ve alır başka bir iş parçacığında hizmetinden gelen yanıt.  
  
 İstek-yanıt hizmeti sözleşme oluşturmak için hizmet sözleşmesini tanımlama ve uygulama <xref:System.ServiceModel.OperationContractAttribute> aşağıdaki örnek kodda gösterildiği gibi her işlem için sınıf.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Ayarlama gerekmez <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `false` bu varsayılan davranış olduğu için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tek Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [Çift Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)
