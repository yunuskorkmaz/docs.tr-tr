---
title: Hizmet Sözleşmelerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: ac27329278edc2b9ca693aa15bcc5bb58edffe05
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320155"
---
# <a name="implementing-service-contracts"></a>Hizmet Sözleşmelerini Uygulama
Hizmet, bir veya daha fazla bitiş noktasında istemciler için kullanılabilir işlevselliği kullanıma sunan bir sınıftır. Bir hizmet oluşturmak için, bir Windows Communication Foundation (WCF) sözleşmesi uygulayan bir sınıf yazın. Bunu iki şekilde yapabilirsiniz. Sözleşmeyi ayrı bir arabirim olarak tanımlayabilir ve ardından bu arabirimi uygulayan bir sınıf oluşturabilirsiniz. Alternatif olarak, sınıfının başına <xref:System.ServiceModel.ServiceContractAttribute> özniteliğini ve hizmetin istemcilerine sunulan yöntemlere <xref:System.ServiceModel.OperationContractAttribute> özniteliğini yerleştirerek doğrudan sınıfı ve sözleşmeyi oluşturabilirsiniz.  
  
## <a name="creating-a-service-class"></a>Hizmet sınıfı oluşturma  
 Aşağıda ayrı olarak tanımlanmış `IMath` sözleşmesini uygulayan bir hizmetin örneği verilmiştir.  
  
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
  
 Alternatif olarak, bir hizmet bir sözleşmeyi doğrudan kullanıma sunabilir. Aşağıda `MathService` sözleşmesinin tanımlandığı ve uyguladığı bir hizmet sınıfına bir örnek verilmiştir.  
  
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
  
 Sözleşme adları farklı olduğu için yukarıdaki hizmetlerin farklı sözleşmeleri kullanıma sunacağını unutmayın. İlk durumda, sözleşmenin "`MathService`" olarak adlandırıldığından, ortaya çıkan sözleşme "`IMath`" olarak adlandırılır.  
  
 Hizmet ve işlem uygulama düzeylerinde, eşzamanlılık ve örnek oluşturma gibi birkaç şey belirleyebilirsiniz. Daha fazla bilgi için bkz. [Hizmetleri tasarlama ve uygulama](designing-and-implementing-services.md).  
  
 Bir hizmet sözleşmesini uyguladıktan sonra, hizmet için bir veya daha fazla uç nokta oluşturmanız gerekir. Daha fazla bilgi için bkz. [Endpoint oluşturmaya genel bakış](endpoint-creation-overview.md). Bir hizmetin nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Tasarlama ve Uygulama](designing-and-implementing-services.md)
- [Nasıl yapılır: Anlaşma Sınıfı ile Hizmet Oluşturma](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Nasıl yapılır: Anlaşma Arabirimi ile Hizmet Oluşturma](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Hizmet Çalışma Zamanı Davranışını Belirtme](specifying-service-run-time-behavior.md)
