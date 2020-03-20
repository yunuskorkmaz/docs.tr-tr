---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 292573f911459d8a8419e09d81fd1e54dbc6c70b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184745"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme

Windows Communication Foundation (WCF), Kurumsal Hizmetlerle tümleştirme için otomatik bir mekanizma sağlar (bkz. [COM+ Uygulamaları ile Tümleştirme).](integrating-with-com-plus-applications.md) Ancak, kurumsal hizmetler içinde barındırılan işlem bileşenlerini dahili olarak kullanan hizmetler geliştirme esnekliği isteyebilirsiniz. WCF İşlemleri özelliği <xref:System.Transactions> altyapı üzerine kurulduğundan, Kurumsal Hizmetler ile WCF'yi tümleştirme işlemi, Kurumsal <xref:System.Transactions> Hizmetler [ve COM+ İşlemleriyle Birlikte Çalışabilirlik'te](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))belirtildiği gibi, Kurumsal Hizmetler ve Kurumsal Hizmetler arasında birlikte çalışabilirlik belirtmek için de aynıdır.  
  
 Gelen akışlı işlem ile COM+ bağlam hareketi arasında istenilen birlikte çalışabilirlik düzeyini sağlamak <xref:System.Transactions.TransactionScope> için, hizmet uygulamasının <xref:System.Transactions.EnterpriseServicesInteropOption> bir örnek oluşturması ve numaralandırmadan uygun değeri kullanması gerekir.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Kurumsal Hizmetleri Bir Hizmet İşlemiyle Bütünleştirme  
 Aşağıdaki kod, İzin Verilen hareket <xref:System.Transactions.TransactionScope> akışıyla birlikte bir <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlem gösterir ve bu işlem seçeneğiyle birlikte bir işlem oluşturur. Bu senaryoda aşağıdaki koşullar geçerlidir:  
  
- İstemci bir hareket le hareket ederse, Kurumsal Hizmetler bileşenine yapılan çağrı da dahil olmak üzere işlem bu işlem kapsamında yürütülür. Kullanılması, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> hareketin <xref:System.EnterpriseServices> bağlamla eşitlemesini sağlar, bu da ortam hareketinin <xref:System.Transactions> aynı <xref:System.EnterpriseServices> olduğu anlamına gelir.  
  
- İstemci bir hareket akışı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> yoksa, ayar işlem için yeni bir işlem kapsamı `true` oluşturur. Benzer şekilde, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> kullanım, işlemin <xref:System.EnterpriseServices> bileşenin bağlamı içinde kullanılan hareketle aynı olmasını sağlar.  
  
 Ek yöntem çağrıları da aynı işlemin işlem kapsamında oluşur.  
  
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
  
 Bir işlemin geçerli hareketi ile işlemsel Kurumsal Hizmetler bileşenlerine yapılan aramalar arasında <xref:System.Transactions.EnterpriseServicesInteropOption.None> eşitleme gerekmiyorsa, <xref:System.Transactions.TransactionScope> örneği anında ayarlarken seçeneği kullanın.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Kurumsal Hizmetleri Bir İstemci ile Tümleştirme  
 Aşağıdaki kod, <xref:System.Transactions.TransactionScope> <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarı olan bir örneği kullanarak istemci kodunu gösterir. Bu senaryoda, hareket akışını destekleyen hizmet işlemleriçağrıları, Kurumsal Hizmetler bileşenlerine yapılan çağrılarla aynı işlem kapsamında gerçekleşir.  
  
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

- [COM+ Uygulamaları ile tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [COM Uygulamaları ile Tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
