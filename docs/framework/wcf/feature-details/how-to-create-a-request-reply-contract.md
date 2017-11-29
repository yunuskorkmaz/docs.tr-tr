---
title: "Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ad32807227844e379dd44e63c61b3ff15d2a2ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-request-reply-contract"></a>Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma
İstek-yanıt sözleşmesi yanıt döndüren bir yöntem belirtir. Yanıt gönderilir ve bu sözleşmenin koşulları altında isteğine bağıntılı. Yanıt yöntem olsa bile (`void` C# ' ta, veya bir `Sub` Visual Basic'te), altyapı oluşturur ve çağırana boş iletisi gönderir. Bir boş yanıt iletisini göndermeyi önlemek için işlem için tek yönlü sözleşme kullanın.  
  
### <a name="to-create-a-request-reply-contract"></a>İstek-yanıt sözleşmesi oluşturmak için  
  
1.  Arabirim tercih ettiğiniz programlama dilinde oluşturun.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim.  
  
3.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> özniteliği istemcileri çağırabileceği her yöntemi.  
  
4.  İsteğe bağlı. Değerini <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `true` bir boş yanıt iletisini göndermeyi önlemek için. Varsayılan olarak, tüm, istek-yanıt sözleşmeleriyle işlemleridir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sağlayan hesaplayıcı hizmet için bir sözleşmede tanımlar `Add` ve `Subtract` yöntemleri. `Multiply` Yöntemi değil sözleşmesinin bir parçası olarak işaretlenmediğinden <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve böylece bu istemciler için erişilebilir değil.  
  
```
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);
    
    [OperationContract]
    int Subtract(int a, int b);
    
    int Multiply(int a, int b)
}
```
  
-   [!INCLUDE[crabout](../../../../includes/crabout-md.md)]işlemi sözleşmeleri belirtin nasıl <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği.  
  
-   Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri neden olan hizmet sözleşmesi tanımları otomatik olarak oluşturulmasını Web Hizmetleri Açıklama Dili (WSDL) belgede hizmet dağıtıldıktan sonra. Belge ekleyerek karşıdan `?wsdl` HTTP temel adresi hizmeti. Örneğin, `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
