---
title: İş Akışında Sözleşmeleri Kullanma
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dc2d631d8a9e588645dd60495c54799b2a2dd8a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637764"
---
# <a name="using-contracts-in-workflow"></a>İş Akışında Sözleşmeleri Kullanma
Bir hizmet uygularken, bir dizi hizmet ve veri gönderen ve alan açıklayan sözleşme tanımlayın. Verileri veri sözleşmeleri ve ileti sözleşmeleri temsil edilir; WCF hem iş akışı Hizmetleri, veri sözleşme ve ileti anlaşması tanımlarını hizmet açıklamaları bir parçası olarak kullanın. Hizmet, hizmet işlemleri tanımlamak için meta verileri (WSDL biçiminde) kullanıma sunar. WCF'de, hizmet sözleşmeleri ve işlem sözleşmeleri hizmeti ve desteklediği işlemleri tanımlayın. Ancak, bir iş akışı hizmetinde, bu sözleşme iş işleminin bir parçası olan; Bunlar, meta verilerde sözleşme çıkarımı olarak adlandırılan bir işlem tarafından sunulur.  
  
## <a name="contract-inference"></a>Sözleşme çıkarımı  
 Bir iş akışı hizmeti kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tanımı incelenir ve sözleşme Mesajlaşma etkinlikleriyle iş akışında bulunan kümesi temel alınarak oluşturulur. Özellikle aşağıdaki etkinlikleri ve özellikleri sözleşme oluşturmak için kullanılır:  
  
 <xref:System.ServiceModel.Activities.Receive> Etkinlik  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> Etkinlik  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik  
  
 Sözleşme çıkarımı nihai sonucu WCF hizmeti ve işlem sözleşmeleri aynı veri yapılarını kullanarak hizmeti açıklamasıdır. Bu bilgiler, sonra iş akışı hizmeti için WSDL göstermek için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Mesajlaşma Etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [Nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Nasıl yapılır: Mevcut bir hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
