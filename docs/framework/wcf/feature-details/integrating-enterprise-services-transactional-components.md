---
title: "Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6ce82d100341fec4415cf9fdb7159706b2accc4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a>Kurumsal Hizmetler İşlemsel Bileşenlerini Tümleştirme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Kurumsal Hizmetler ile tümleştirmek için otomatik bir mekanizma sağlar (bkz [COM + uygulamaları ile tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)). Ancak, dahili Kurumsal Hizmetler içinde barındırılan işlemsel bileşenlerini kullanan hizmetler geliştirmek için esneklik isteyebilirsiniz. Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işlemleri özelliği üzerinde oluşturulan <xref:System.Transactions> altyapısı, Kuruluş Hizmetleri ile tümleştirme için işlem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arasında birlikte çalışabilirlik belirtmek için aynı olan <xref:System.Transactions> ve Enterprise Kısmında özetlendiği gibi hizmetleri [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](http://go.microsoft.com/fwlink/?LinkId=94949).  
  
 Gelen akışlı işlem ve COM + bağlam işlemi arasında birlikte çalışabilirlik istenen düzeyini sağlamak için hizmet uygulaması oluşturmanız gerekir bir <xref:System.Transactions.TransactionScope> örneği ve uygun değerini kullanın <xref:System.Transactions.EnterpriseServicesInteropOption> numaralandırması.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Kurumsal Hizmetler bir hizmet işlemi ile tümleştirme  
 Aşağıdaki kod bir işlemle oluşturan izin verilen işlem akışını göstermektedir bir <xref:System.Transactions.TransactionScope> ile <xref:System.Transactions.EnterpriseServicesInteropOption.Full> seçeneği. Bu senaryoda aşağıdaki koşullar geçerlidir:  
  
-   İstemci bir işlem akışlar, Kurumsal hizmetleri bileşeni çağrısı dahil olmak üzere işlemi, bu işlem kapsamı içinde yürütülür. Kullanarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlem ile eşitlenir sağlar <xref:System.EnterpriseServices> için ortam işlem anlamına bağlam <xref:System.Transactions> ve <xref:System.EnterpriseServices> aynıdır.  
  
-   İstemci bir işlem akış değil, ayarı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> için `true` işlemi için yeni bir işlem kapsamı oluşturur. Benzer şekilde, kullanarak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> işlemin işlem içinde kullanılan işlem ile aynı olmasını sağlar <xref:System.EnterpriseServices> bileşenin bağlamı.  
  
 Hiçbir ek yöntem çağrıları de aynı işlem işlem kapsamı içinde gerçekleşmesi gerekir.  
  
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
  
 Bir işlemin geçerli işlem ve Kurumsal Hizmetler işlemsel bileşenlerini çağrıları arasında eşitleme işlemi gerekiyorsa, daha sonra kullanmak <xref:System.Transactions.EnterpriseServicesInteropOption.None> seçeneği başlatılırken <xref:System.Transactions.TransactionScope> örneği.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Kurumsal Hizmetler istemcisi ile tümleştirme  
 Aşağıdaki kod, istemci kodu kullanarak gösterir bir <xref:System.Transactions.TransactionScope> örneği <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ayarı. Bu senaryoda, işlem akışı destek hizmet işlemlerine çağrıları Kuruluş Hizmetleri bileşenleri çağrılar aynı işlem kapsamı içinde oluşur.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM+ Uygulamaları ile Tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [COM Uygulamaları ile Tümleştirme](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
