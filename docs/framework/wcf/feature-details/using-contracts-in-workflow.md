---
title: İş Akışında Sözleşmeleri Kullanma
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: def100f9483ea9ac8bf1aa3285d76edccffb030a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595017"
---
# <a name="using-contracts-in-workflow"></a>İş Akışında Sözleşmeleri Kullanma
Bir hizmet uygularken, hizmeti ve gönderdiği verileri tanımlayan bir dizi sözleşme tanımlarsınız. Veriler veri sözleşmeleri ve ileti sözleşmeleri olarak temsil edilir; WCF ve Workflow Hizmetleri, hizmet açıklamalarının parçası olarak veri sözleşmesi ve ileti sözleşmesi tanımlarını kullanır. Hizmet, hizmetin işlemlerini anlatmak için meta verileri (WSDL biçiminde) kullanıma sunar. WCF 'de hizmet sözleşmeleri ve işlem sözleşmeleri, hizmeti ve desteklediği işlemleri tanımlar. Ancak, bir iş akışı hizmetinde, bu sözleşmeler iş sürecinin bir parçasıdır; Bunlar, anlaşma çıkarımı adlı bir işlem tarafından meta verilerde kullanıma sunulur.  
  
## <a name="contract-inference"></a>Sözleşme çıkarımı  
 Bir iş akışı hizmeti kullanılarak barındırıldığı zaman, iş akışı <xref:System.ServiceModel.Activities.WorkflowServiceHost> tanımı incelenir ve iş akışında bulunan mesajlaşma etkinlikleri kümesine göre bir sözleşme oluşturulur. Aşağıdaki etkinlikler ve özellikler, sözleşmeyi oluşturmak için kullanılır:  
  
 <xref:System.ServiceModel.Activities.Receive>Etkinlik  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply>Etkinlik  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik  
  
 Sözleşme çıkarımı nihai sonucu, WCF hizmeti ve işlem sözleşmeleri ile aynı veri yapılarını kullanan hizmetin bir açıklamasıdır. Bu bilgiler daha sonra iş akışı hizmeti için WSDL 'yi göstermek üzere kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](workflow-services.md)
- [Mesajlaşma Etkinlikleri](messaging-activities.md)
- [Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma](how-to-create-a-workflow-service-with-messaging-activities.md)
- [Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
