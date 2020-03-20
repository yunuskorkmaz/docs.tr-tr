---
title: 'Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 793f7214f8319e87c3e344990577841fc029bc55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185024"
---
# <a name="how-to-create-a-request-reply-contract"></a>Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma
İstek-yanıt sözleşmesi, yanıtı döndüren bir yöntem belirtir. Yanıt gönderilmelidir ve bu sözleşmenin şartları altında istekle ilişkilendirilmelidir. Yöntem yanıt vermese`void` bile (C#veya `Sub` Visual Basic'te), altyapı oluşturur ve arayana boş bir ileti gönderir. Boş bir yanıt iletisi gönderilmesini önlemek için işlem için tek yönlü bir sözleşme kullanın.  
  
### <a name="to-create-a-request-reply-contract"></a>İstek-yanıt sözleşmesi oluşturmak için  
  
1. Seçtiğiniz programlama dilinde bir arayüz oluşturun.  
  
2. <xref:System.ServiceModel.ServiceContractAttribute> Özniteliği arabirime uygulayın.  
  
3. İstemcilerin <xref:System.ServiceModel.OperationContractAttribute> çağırabileceği her yönteme öznitelik uygulayın.  
  
4. İsteğe bağlı. Boş bir yanıt <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> iletisi gönderilmesini önlemek için `true` özelliğin değerini ayarlayın. Varsayılan olarak, tüm işlemler istek yanıtlama sözleşmeleridir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sağlayan `Add` ve `Subtract` yöntemler sağlayan bir hesap makinesi hizmeti için bir sözleşme tanımlar. Yöntem, `Multiply` <xref:System.ServiceModel.OperationContractAttribute> sınıf tarafından işaretlenmediği ve bu nedenle istemciler tarafından erişilemediği için sözleşmenin bir parçası değildir.  
  
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
  
- Çalışma sözleşmelerinin nasıl belirtilen hakkında <xref:System.ServiceModel.OperationContractAttribute> daha <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> fazla bilgi için sınıfa ve özelliğine bakın.  
  
- Hizmet <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> dağıtıldıktan sonra web hizmetleri açıklama dili (WSDL) belgesinde otomatik hizmet sözleşmesi tanımlarının uygulanmasına neden olur. Belge, hizmetin HTTP `?wsdl` temel adresine eklenerek indirilir. Örneğin, `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationContractAttribute>
- [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
