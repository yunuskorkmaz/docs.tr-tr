---
title: "Hizmet Sözleşmelerini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b40b93b33e57bf15b7ab614405ccffa44abb8df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-service-contracts"></a>Hizmet Sözleşmelerini Uygulama
Bir hizmet bir veya daha fazla uç noktaları istemcilerinde kullanımına işlevselliği kullanıma sunan bir sınıftır. Bir hizmet oluşturmak için uygulayan bir sınıf yazma bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] sözleşme. Bunu iki yoldan biriyle yapabilirsiniz. Sözleşme ayrı ayrı bir arabirim tanımlayın ve ardından arabirimi uygulayan bir sınıf oluşturun. Alternatif olarak, sınıf ve sözleşme doğrudan koyarak oluşturabileceğiniz <xref:System.ServiceModel.ServiceContractAttribute> sınıfı özniteliği ve <xref:System.ServiceModel.OperationContractAttribute> hizmetinin istemciler için kullanılabilen yöntemler özniteliği.  
  
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
  
 Birkaç hizmet ve işlem eşzamanlılık ve örnek oluşturma gibi uygulama düzeyleri ayarlayabilirsiniz. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Bir hizmet sözleşmesini uyguladıktan sonra hizmet için bir veya daha fazla uç noktalar oluşturmanız gerekir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Uç noktası oluşturma genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]bir hizmet farklı çalıştır nasıl [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Nasıl yapılır: Sözleşme sınıfı ile hizmet oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [Nasıl yapılır: sözleşme arabirimi ile bir hizmet oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [Hizmet çalışma zamanı davranışını belirtme](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
