---
title: 'Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 9954be556df13193c290a55616ad83ef07e0af7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141082"
---
# <a name="how-to-create-a-request-reply-contract"></a>Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma
İstek-yanıt anlaşması yanıt döndüren bir yöntem belirtir. Yanıtı gönderilir ve bu sözleşmenin koşullarına isteğine bağıntılı. Bile yöntem hiç yanıt döndürür (`void` C# veya `Sub` Visual Basic'te), altyapıyı oluşturur ve çağırana bir boş ileti gönderir. Bir boş bir yanıt iletisini göndermeyi önlemek için tek yönlü anlaşma işlemi için kullanın.  
  
### <a name="to-create-a-request-reply-contract"></a>İstek-yanıt anlaşması oluşturma  
  
1.  Bir arabirim, kendi seçtiğiniz programlama dilinde oluşturun.  
  
2.  Uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim.  
  
3.  Uygulama <xref:System.ServiceModel.OperationContractAttribute> istemcileri çağırabilirsiniz her yönteme öznitelik.  
  
4.  İsteğe bağlı. Değerini <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini `true` bir boş bir yanıt iletisini göndermeyi önlemek için. Varsayılan olarak, tüm işlemler istek-yanıt sözleşmeleriyle gerçekleştirilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sağlayan bir hesap makinesi hizmet sözleşme tanımlayan `Add` ve `Subtract` yöntemleri. `Multiply` Yöntemi değil sözleşmesinin bir parçası olarak işaretlenmediğinden <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve bu nedenle, istemciler için erişilebilir değil.  
  
```csharp
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
  
-   İşlem sözleşmeleri belirtme hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.OperationContractAttribute> sınıfı ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği.  
  
-   Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri hizmet dağıtıldıktan sonra bu hizmet sözleşmesi tanımları otomatik olarak oluşturulmasını Web Hizmetleri Açıklama Dili (WSDL) belgesinde sağlar. Belge ekleyerek indirdiğiniz `?wsdl` HTTP temel adresi hizmeti. Örneğin, `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationContractAttribute>
- [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
