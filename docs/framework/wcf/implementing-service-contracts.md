---
title: Hizmet Sözleşmelerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928642"
---
# <a name="implementing-service-contracts"></a>Hizmet Sözleşmelerini Uygulama
Bir veya daha fazla uç noktası istemcilere kullanılabilir olan işlevsellik sunduğu bir sınıf bir hizmettir. Bir hizmet oluşturmak için bir Windows Communication Foundation (WCF) sözleşmesi uygulayan bir sınıf yazın. İki yoldan biriyle bunu yapabilirsiniz. Sözleşme ayrı ayrı arabirim olarak tanımlayabilir ve ardından bu arabirimi uygulayan bir sınıf oluşturun. Alternatif olarak, sınıf ve sözleşme doğrudan yerleştirerek oluşturabileceğiniz <xref:System.ServiceModel.ServiceContractAttribute> sınıfı özniteliği ve <xref:System.ServiceModel.OperationContractAttribute> hizmeti istemcilerine uygun olan yöntemler özniteliği.  
  
## <a name="creating-a-service-class"></a>Bir hizmet sınıfı oluşturma  
 Uygulayan bir hizmetin bir örneği verilmiştir bir `IMath` ayrı olarak tanımlanan sözleşme.  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Alternatif olarak, bir hizmet sözleşme doğrudan kullanıma sunabilirsiniz. Tanımlar ve uygulayan bir hizmet sınıfın bir örneği verilmiştir bir `MathService` sözleşme.  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Önceki hizmetlerin sözleşmesi adları farklı olduğundan farklı sözleşmeler kullanıma unutmayın. Bu durumda, kullanıma sunulan sözleşme adında "`IMath`"İkinci durumda sözleşme adlandırılırken"`MathService`".  
  
 Hizmet ve işlem eşzamanlılık ve örnek oluşturma gibi uygulama düzeyleri birkaç şey ayarlayabilirsiniz. Daha fazla bilgi için [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Bir hizmet sözleşmesini uyguladıktan sonra hizmeti için bir veya daha fazla uç noktası oluşturmanız gerekir. Daha fazla bilgi için [uç nokta oluşturmaya genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md). Bir hizmet çalıştırma hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Tasarlama ve Uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Nasıl yapılır: Bir sözleşme sınıfı ile hizmet oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Nasıl yapılır: Bir sözleşme arabirimi ile hizmet oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Hizmet Çalışma Zamanı Davranışını Belirtme](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
