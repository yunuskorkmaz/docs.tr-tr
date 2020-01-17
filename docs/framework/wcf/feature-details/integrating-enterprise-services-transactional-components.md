---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 5914f76639adc3ff569a3bfb8d6eb1db14313e76
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211946"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme

Windows Communication Foundation (WCF), Enterprise Services ile tümleştirme için otomatik bir mekanizma sağlar (bkz. [com+ uygulamalarıyla tümleştirme](integrating-with-com-plus-applications.md)). Ancak, kurumsal hizmetlerde barındırılan işlemsel bileşenleri dahili olarak kullanan hizmetler geliştirme esnekliği de isteyebilirsiniz. WCF Işlemler özelliği <xref:System.Transactions> altyapısında oluşturulduğundan, Enterprise Services 'ı WCF ile tümleştirme işlemi, [Kurumsal Hizmetler ve com+ işlemleri Ile birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))bölümünde açıklandığı gibi, <xref:System.Transactions> ve Enterprise hizmetleri arasında birlikte çalışabilirlik belirtmeyle aynıdır.  
  
 Gelen akışlı işlem ve COM+ bağlam işlemi arasında istediğiniz birlikte çalışabilirlik düzeyini sağlamak için, hizmet uygulamasının bir <xref:System.Transactions.TransactionScope> örneği oluşturması ve <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırmasından uygun değeri kullanması gerekir.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Kurumsal Hizmetleri bir hizmet Işlemi ile tümleştirme  
 Aşağıdaki kod, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> seçeneğiyle bir <xref:System.Transactions.TransactionScope> oluşturan, Izin verilen işlem akışına sahip bir işlemi gösterir. Bu senaryoda aşağıdaki koşullar geçerlidir:  
  
- İstemci bir işlem akışa alıyorsa, Enterprise Services bileşenine yapılan çağrı dahil olmak üzere işlem bu işlemin kapsamı içinde yürütülür. <xref:System.Transactions.EnterpriseServicesInteropOption.Full> kullanmak, işlemin <xref:System.EnterpriseServices> bağlamla eşitlenmesini sağlar. Bu, <xref:System.Transactions> ve <xref:System.EnterpriseServices> ortam işleminin aynı olduğu anlamına gelir.  
  
- İstemci bir işlem akiçermiyorsa, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` ayarı, işlem için yeni bir işlem kapsamı oluşturur. Benzer şekilde, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> kullanmak işlemin işleminin, <xref:System.EnterpriseServices> bileşenin bağlamı içinde kullanılan işlemle aynı olmasını sağlar.  
  
 Aynı işlemin işleminin kapsamı içinde ek yöntem çağrıları da oluşur.  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services   
         // component   
  
         // Call UpdateOtherCustomerData method on an Enterprise   
         // Services component   
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 Bir işlemin geçerli işlemi ve işlemsel kurumsal hizmetler bileşenlerine çağrılar arasında eşitleme gerekmiyorsa, <xref:System.Transactions.TransactionScope> örneğini örneklemesinde <xref:System.Transactions.EnterpriseServicesInteropOption.None> seçeneğini kullanın.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Kurumsal Hizmetleri bir Istemciyle tümleştirme  
 Aşağıdaki kod, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarıyla bir <xref:System.Transactions.TransactionScope> örneği kullanarak istemci kodunu gösterir. Bu senaryoda, işlem akışını destekleyen hizmet işlemlerine yapılan çağrılar, Enterprise Services bileşenlerine yapılan çağrılarla aynı işlemin kapsamı içinde oluşur.  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services   
        // component   
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and   
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM+ Uygulamaları ile Tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [COM Uygulamaları ile Tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
