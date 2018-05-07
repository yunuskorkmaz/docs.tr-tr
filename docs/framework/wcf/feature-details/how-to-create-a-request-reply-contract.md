---
title: 'Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 76a3bbb9415a34218896bc561066c7ac4a30e6b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
  
-   İşlemi sözleşmeleri belirtme hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği.  
  
-   Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri neden olan hizmet sözleşmesi tanımları otomatik olarak oluşturulmasını Web Hizmetleri Açıklama Dili (WSDL) belgede hizmet dağıtıldıktan sonra. Belge ekleyerek karşıdan `?wsdl` HTTP temel adresi hizmeti. Örneğin, `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Nasıl yapılır: Çift Yönlü Anlaşma Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
