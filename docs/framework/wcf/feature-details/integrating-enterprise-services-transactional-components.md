---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 1c4fabfadb113c79b216fa10ff80b551ba0f9716
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596857"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme

Windows Communication Foundation (WCF), Enterprise Services ile tümleştirme için otomatik bir mekanizma sağlar (bkz. [com+ uygulamalarıyla tümleştirme](integrating-with-com-plus-applications.md)). Ancak, kurumsal hizmetlerde barındırılan işlemsel bileşenleri dahili olarak kullanan hizmetler geliştirme esnekliği de isteyebilirsiniz. WCF Işlemler özelliği altyapıda oluşturulduğu için, Enterprise Services 'ı <xref:System.Transactions> WCF ile tümleştirme işlemi, Kurumsal Hizmetler <xref:System.Transactions> [ve com+ Işlemleri ile birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))bölümünde açıklandığı gibi, ve Enterprise Services arasında birlikte çalışabilirlik belirtme ile aynıdır.  
  
 Gelen akışlı işlem ve COM+ bağlam işlemi arasında istediğiniz birlikte çalışabilirlik düzeyini sağlamak için, hizmet uygulamasının bir <xref:System.Transactions.TransactionScope> örnek oluşturması ve Numaralandırmadaki uygun değeri kullanması gerekir <xref:System.Transactions.EnterpriseServicesInteropOption> .  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Kurumsal Hizmetleri bir hizmet Işlemi ile tümleştirme  
 Aşağıdaki kod, seçeneğiyle bir olan bir işlemi, Izin verilen işlem akışı ile gösterir <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> . Bu senaryoda aşağıdaki koşullar geçerlidir:  
  
- İstemci bir işlem akışa alıyorsa, Enterprise Services bileşenine yapılan çağrı dahil olmak üzere işlem bu işlemin kapsamı içinde yürütülür. Kullanılarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin, <xref:System.EnterpriseServices> ve için ortam işleminin <xref:System.Transactions> aynı olduğu anlamına gelen bağlamla eşitlenmesi sağlanır <xref:System.EnterpriseServices> .  
  
- İstemci bir işlem akiçermiyorsa <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` işlem için yeni bir işlem kapsamı oluşturur ayarı. Benzer şekilde, kullanmak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin işleminin bileşenin bağlamı içinde kullanılan işlemle aynı olmasını sağlar <xref:System.EnterpriseServices> .  
  
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
  
 Bir işlemin geçerli işlemi ile işlem Enterprise Services bileşenlerine yapılan çağrılar arasında eşitleme gerekmiyorsa, <xref:System.Transactions.EnterpriseServicesInteropOption.None> örneği örneklemesinde seçeneğini kullanın <xref:System.Transactions.TransactionScope> .  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Kurumsal Hizmetleri bir Istemciyle tümleştirme  
 Aşağıdaki kod, ayarıyla bir örnek kullanan istemci kodunu gösterir <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> . Bu senaryoda, işlem akışını destekleyen hizmet işlemlerine yapılan çağrılar, Enterprise Services bileşenlerine yapılan çağrılarla aynı işlemin kapsamı içinde oluşur.  
  
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

- [COM+ uygulamalarıyla tümleştirme](integrating-with-com-plus-applications.md)
- [COM Uygulamaları ile Tümleştirme](integrating-with-com-applications.md)
