---
title: 'Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 8a09c265c77edc584b591477e64314f1e76e332b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593444"
---
# <a name="how-to-create-a-request-reply-contract"></a>Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma
İstek-yanıt sözleşmesi, yanıt döndüren bir yöntemi belirtir. Yanıt gönderilmesi ve bu sözleşmenin koşullarına göre istekle bağıntılı olması gerekir. Yöntem yanıt vermez ( `void` C# veya `Sub` Visual Basic içinde), altyapı çağırana boş bir ileti oluşturur ve gönderir. Boş bir yanıt iletisi gönderilmesini engellemek için, işlem için tek yönlü bir sözleşme kullanın.  
  
### <a name="to-create-a-request-reply-contract"></a>İstek-yanıt sözleşmesi oluşturmak için  
  
1. Seçtiğiniz programlama dilinde bir arabirim oluşturun.  
  
2. <xref:System.ServiceModel.ServiceContractAttribute>Özniteliğini arabirimine uygulayın.  
  
3. Özniteliği, <xref:System.ServiceModel.OperationContractAttribute> istemcilerin çağırabileceği her metoda uygulayın.  
  
4. İsteğe bağlı. <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` Boş bir yanıt iletisi gönderilmesini engellemek için özelliğinin değerini olarak ayarlayın. Varsayılan olarak, tüm işlemler istek-yanıt sözleşmeleri ' dir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ve yöntemleri sağlayan bir Hesaplayıcı hizmeti için bir sözleşme tanımlar `Add` `Subtract` . `Multiply`Yöntem, sınıf tarafından işaretlenmediği <xref:System.ServiceModel.OperationContractAttribute> ve istemciler tarafından erişilemediği için sözleşmenin bir parçası değil.  
  
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
  
- İşlem sözleşmelerini belirtme hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.OperationContractAttribute> . sınıfı ve <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği.  
  
- <xref:System.ServiceModel.ServiceContractAttribute>Ve özniteliklerinin uygulanması, <xref:System.ServiceModel.OperationContractAttribute> hizmet dağıtıldıktan sonra bir Web Hizmetleri Açıklama DILI (wsdl) belgesinde hizmet sözleşmesi tanımlarının otomatik olarak oluşturulmasına neden olur. Belge, `?wsdl` HIZMETIN http temel adresine eklenerek indirilir. Örneğin, `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationContractAttribute>
- [Hizmet Sözleşmeleri Tasarlama](../designing-service-contracts.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma](how-to-create-a-duplex-contract.md)
