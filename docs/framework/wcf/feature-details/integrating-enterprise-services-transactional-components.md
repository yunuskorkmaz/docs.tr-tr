---
title: Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 33e09eab1d7ad24dc234cfff21e352611e0b2ef9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202046"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
Windows Communication Foundation (WCF) Hizmetleri ile Kurumsal tümleştirme için otomatik bir mekanizma sağlar (bkz [COM + uygulamaları ile tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Ancak, dahili olarak Enterprise Hizmetleri içinde bulunan işlem bileşenleri kullanan hizmetleri geliştirmek için esneklik isteyebilirsiniz. WCF işlem özellik oluşturulduğundan <xref:System.Transactions> altyapı, Kurumsal Services'ı WCF ile tümleştirme sürecini arasında birlikte çalışabilirlik belirtmek için aynı <xref:System.Transactions> ve kurumsal açıklandığı gibi hizmetleri [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](https://go.microsoft.com/fwlink/?LinkId=94949).  
  
 İstenen akışlı gelen işlem ve COM + bağlamı işlem arasında birlikte çalışabilirlik düzeyini sağlamak için hizmet uygulaması oluşturmanız gerekir bir <xref:System.Transactions.TransactionScope> uygun değerini kullanın ve örnek <xref:System.Transactions.EnterpriseServicesInteropOption> sabit listesi.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Kurumsal Hizmetler bir hizmet işlemi ile tümleştirme  
 Aşağıdaki kod, oluşturan, izin verilen işlem akışı ile bir işlem gösterir bir <xref:System.Transactions.TransactionScope> ile <xref:System.Transactions.EnterpriseServicesInteropOption.Full> seçeneği. Bu senaryoda aşağıdaki koşullar geçerlidir:  
  
-   İstemci bir işlem olursa Enterprise hizmetleri bileşeni için arama da dahil olmak üzere bu işlemi bu işlemin kapsamı içinde yürütülür. Kullanarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlem ile eşitlendiğini sağlar <xref:System.EnterpriseServices> anlamına gelir için ortam işlem bağlamı <xref:System.Transactions> ve <xref:System.EnterpriseServices> aynıdır.  
  
-   İstemci bir işlem geçmeyen varsa, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> için `true` işlemi için yeni bir işlem kapsamı oluşturur. Benzer şekilde, kullanarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin işlem içinde kullanılan işlem ile aynı olmasını sağlar <xref:System.EnterpriseServices> bileşenin bağlamı.  
  
 Herhangi bir ek yöntem çağrılarını da aynı işlemin işlem kapsamında oluşur.  
  
```  
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
  
 Bir işlemin geçerli işlem ve Kurumsal Hizmetler işlemsel bileşenlerini çağrıları arasında eşitleme gereklidir, ardından kullanın <xref:System.Transactions.EnterpriseServicesInteropOption.None> seçeneği örneklerken <xref:System.Transactions.TransactionScope> örneği.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Kurumsal Hizmetler istemcisi ile tümleştirme  
 Aşağıdaki kod, istemci kodu kullanarak gösterir. bir <xref:System.Transactions.TransactionScope> ile örnek <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarı. Bu senaryoda, Enterprise Hizmetleri bileşenleri çağrılar aynı işlem kapsamında işlem akışı destekleyen hizmet işlemlerine çağrıları oluşur.  
  
```  
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

- [COM Uygulamaları ile Tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [COM Uygulamaları ile Tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
