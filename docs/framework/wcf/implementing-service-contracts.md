---
title: Hizmet Sözleşmelerini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: aefe146a8941d98d7d9138e4ece83c330c967034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183998"
---
# <a name="implementing-service-contracts"></a>Hizmet Sözleşmelerini Uygulama
Hizmet, istemcilerin bir veya daha fazla uç noktada kullanabileceği işlevselliği ortaya çıkaran bir sınıftır. Bir hizmet oluşturmak için, Windows Communication Foundation (WCF) sözleşmesini uygulayan bir sınıf yazın. Bunu iki yoldan birini kullanarak yapabilirsiniz. Sözleşmeyi ayrı ayrı arabirim olarak tanımlayabilir ve ardından bu arabirimi uygulayan bir sınıf oluşturabilirsiniz. Alternatif olarak, sınıfın kendisine özniteliği ve <xref:System.ServiceModel.ServiceContractAttribute> hizmet istemcileri için kullanılabilir <xref:System.ServiceModel.OperationContractAttribute> yöntemlere öznitelik yerleştirerek sınıf ve sözleşme doğrudan oluşturabilirsiniz.  
  
## <a name="creating-a-service-class"></a>Hizmet sınıfı oluşturma  
 Aşağıda, ayrı olarak tanımlanmış bir sözleşme `IMath` uygulayan bir hizmet örneği verilmiştir.  
  
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
  
 Alternatif olarak, bir hizmet doğrudan bir sözleşme ortaya çıkarabilir. Aşağıda, bir `MathService` sözleşmetanımlayan ve uygulayan bir hizmet sınıfı örneği verilmiştir.  
  
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
  
 Sözleşme adları farklı olduğundan, önceki hizmetlerin farklı sözleşmeler ortaya çıkardığını unutmayın. İlk durumda, açıkta kalan sözleşme`IMath`" " olarak adlandırılırken,`MathService`ikinci durumda sözleşme " " olarak adlandırılır.  
  
 Eşzamanlılık ve instancing gibi hizmet ve işlem uygulama düzeylerinde birkaç şey ayarlayabilirsiniz. Daha fazla bilgi için [bkz.](designing-and-implementing-services.md)  
  
 Bir hizmet sözleşmesi uyguladıktan sonra, hizmet için bir veya daha fazla uç nokta oluşturmanız gerekir. Daha fazla bilgi için Bkz. [Endpoint Oluşturma Genel Bakış.](endpoint-creation-overview.md) Bir hizmeti nasıl çalıştırabileceğiniz hakkında daha fazla bilgi için [Barındırma Hizmetleri'ne](hosting-services.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Tasarlama ve Uygulama](designing-and-implementing-services.md)
- [Nasıl yapılır: Anlaşma Sınıfı ile Hizmet Oluşturma](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Nasıl yapılır: Anlaşma Arabirimi ile Hizmet Oluşturma](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Hizmet Çalışma Zamanı Davranışını Belirtme](specifying-service-run-time-behavior.md)
