---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: c73be31bef67f1de818f7b04181a3540bbd7caa8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991544"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
Windows Communication Foundation (WCF), Enterprise Services ile tümleştirme için otomatik bir mekanizma sağlar (bkz. [com+ uygulamalarıyla tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Ancak, kurumsal hizmetlerde barındırılan işlemsel bileşenleri dahili olarak kullanan hizmetler geliştirme esnekliği de isteyebilirsiniz. WCF işlemler özelliği altyapıda <xref:System.Transactions> oluşturulduğu için, Enterprise Services 'ı WCF ile tümleştirme işlemi, ' de açıklandığı gibi, ve Enterprise Services arasında <xref:System.Transactions> birlikte çalışabilirlik belirtme ile aynıdır. [Kurumsal Hizmetler ve com+ işlemleri Ile birlikte çalışabilirlik](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Gelen akışlı işlem ve com+ bağlam işlemi arasında istediğiniz birlikte çalışabilirlik düzeyini sağlamak için, hizmet uygulamasının bir <xref:System.Transactions.TransactionScope> örnek oluşturması ve <xref:System.Transactions.EnterpriseServicesInteropOption> Numaralandırmadaki uygun değeri kullanması gerekir.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Kurumsal Hizmetleri bir hizmet Işlemi ile tümleştirme  
 Aşağıdaki kod, <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> seçeneğiyle bir olan bir işlemi, izin verilen işlem akışı ile gösterir. Bu senaryoda aşağıdaki koşullar geçerlidir:  
  
- İstemci bir işlem akışa alıyorsa, Enterprise Services bileşenine yapılan çağrı dahil olmak üzere işlem bu işlemin kapsamı içinde yürütülür. Kullanılarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin, ve için <xref:System.Transactions> ortamişleminin<xref:System.EnterpriseServices> aynı olduğuanlamınagelenbağlamlaeşitlenmesisağlanır.<xref:System.EnterpriseServices>  
  
- İstemci bir işlem akiçermiyorsa işlem için yeni bir işlem <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> kapsamı `true` oluşturur ayarı. Benzer şekilde, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> kullanmak işlemin işleminin <xref:System.EnterpriseServices> bileşenin bağlamı içinde kullanılan işlemle aynı olmasını sağlar.  
  
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
  
 Bir işlemin geçerli işlemi ile işlem Enterprise Services bileşenlerine yapılan çağrılar arasında eşitleme gerekmiyorsa, <xref:System.Transactions.EnterpriseServicesInteropOption.None> <xref:System.Transactions.TransactionScope> örneği örneklemesinde seçeneğini kullanın.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Kurumsal Hizmetleri bir Istemciyle tümleştirme  
 Aşağıdaki kod, <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarıyla bir örnek kullanan istemci kodunu gösterir. Bu senaryoda, işlem akışını destekleyen hizmet işlemlerine yapılan çağrılar, Enterprise Services bileşenlerine yapılan çağrılarla aynı işlemin kapsamı içinde oluşur.  
  
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
