---
title: Hizmet Sözleşmelerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 4e6570291571815781ce543f5991ae40ed57d1e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-service-contracts"></a>Hizmet Sözleşmelerini Uygulama
Bir hizmet bir veya daha fazla uç noktaları istemcilerinde kullanımına işlevselliği kullanıma sunan bir sınıftır. Bir hizmet oluşturmak için bir Windows Communication Foundation (WCF) sözleşme uygulayan bir sınıf yazma. Bunu iki yoldan biriyle yapabilirsiniz. Sözleşme ayrı ayrı bir arabirim tanımlayın ve ardından arabirimi uygulayan bir sınıf oluşturun. Alternatif olarak, sınıf ve sözleşme doğrudan koyarak oluşturabileceğiniz <xref:System.ServiceModel.ServiceContractAttribute> sınıfı özniteliği ve <xref:System.ServiceModel.OperationContractAttribute> hizmetinin istemciler için kullanılabilen yöntemler özniteliği.  
  
## <a name="creating-a-service-class"></a>Hizmet sınıfı oluşturma  
 Aşağıdaki uygulayan bir hizmetin örneğidir bir `IMath` ayrı olarak tanımlanan sözleşme.  
  
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
  
 Alternatif olarak, bir hizmet, bir sözleşme doğrudan getirebilir. Aşağıdaki tanımlayan ve uygulayan bir hizmet sınıf örnektir bir `MathService` sözleşme.  
  
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
  
 Önceki hizmetleri sözleşmesi adları farklı olduğundan farklı sözleşmeleri kullanıma unutmayın. İlk durumda gösterilen sözleşme adında "`IMath`"İkinci durumda sözleşme adlı sırada"`MathService`".  
  
 Birkaç hizmet ve işlem eşzamanlılık ve örnek oluşturma gibi uygulama düzeyleri ayarlayabilirsiniz. Daha fazla bilgi için bkz: [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Bir hizmet sözleşmesini uyguladıktan sonra hizmet için bir veya daha fazla uç noktalar oluşturmanız gerekir. Daha fazla bilgi için bkz: [uç noktası oluşturma genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md). Bir hizmeti çalıştırma hakkında daha fazla bilgi için bkz: [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetleri Tasarlama ve Uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Nasıl yapılır: Anlaşma Sınıfı ile Hizmet Oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [Nasıl yapılır: Anlaşma Arabirimi ile Hizmet Oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [Hizmet Çalışma Zamanı Davranışını Belirtme](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
