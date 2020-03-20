---
title: İş Akışında Sözleşmeleri Kullanma
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 9f967d75a8e9d24fcfac8b7376a3d4840fba52f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184268"
---
# <a name="using-contracts-in-workflow"></a>İş Akışında Sözleşmeleri Kullanma
Bir hizmeti uygularken, hizmeti ve gönderdiği ve aldığı verileri açıklayan bir dizi sözleşme tanımlarsınız. Veriler veri sözleşmeleri ve ileti sözleşmeleri olarak temsil edilir; hem WCF hem de iş akışı hizmetleri, hizmet açıklamalarının bir parçası olarak veri sözleşmesi ve ileti sözleşmesi tanımlarını kullanır. Hizmetin kendisi, hizmetin işlemlerini açıklamak için meta verileri (WSDL biçiminde) ortaya çıkarır. WCF'de hizmet sözleşmeleri ve işletme sözleşmeleri hizmeti ve desteklediği işlemleri tanımlar. Ancak, bir iş akışı hizmetinde, bu sözleşmeler iş sürecinin bir parçasıdır; sözleşme çıkarımı adı verilen bir işlemle meta verilerde ortaya çıkarlar.  
  
## <a name="contract-inference"></a>Sözleşme Çıkarımı  
 İş akışı hizmeti kullanılarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırıldığında, iş akışı tanımı incelenir ve iş akışında bulunan ileti etkinlikleri kümesine göre bir sözleşme oluşturulur. Özellikle aşağıdaki faaliyetler ve özellikler sözleşme oluşturmak için kullanılır:  
  
 <xref:System.ServiceModel.Activities.Receive>Etkinlik  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply>Etkinlik  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik  
  
 Sözleşme çıkarımının sonucu, WCF hizmeti ve işlem sözleşmeleri ile aynı veri yapılarını kullanan hizmetin açıklamasıdır. Bu bilgiler daha sonra iş akışı hizmeti için WSDL'yi ortaya çıkarmak için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Mesajlaşma Etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
