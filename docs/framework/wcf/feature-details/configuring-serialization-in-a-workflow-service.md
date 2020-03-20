---
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185340"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
İş akışı hizmetleri Windows Communication Foundation (WCF) hizmetleridir ve <xref:System.Runtime.Serialization.DataContractSerializer> bu nedenle (varsayılan) veya <xref:System.Xml.Serialization.XmlSerializer>. İş akışı olmayan hizmetler yazarken kullanılacak serileştirici türü hizmet veya işletme sözleşmesinde belirtilir. WCF iş akışı hizmetleri oluştururken bu sözleşmeleri kod olarak belirtmezsiniz, daha çok sözleşme çıkarımı yla çalışma zamanında oluşturulurlar. Sözleşme çıkarımı hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)  Serileştirici <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği kullanılarak belirtilir. Bu, aşağıdaki resimde gösterildiği gibi tasarımcıda ayarlanabilir.  
  
 ![Özellikler Penceresinde SerializerOption özelliğini ayarlama.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Serileştirici, aşağıdaki örnekte gösterildiği gibi kod olarak da ayarlanabilir,  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  Bilinen türler İş Akışı hizmetlerinde de belirtilebilir. Bilinen Türler hakkında daha fazla bilgi için [bkz.](data-contract-known-types.md) Bilinen türler tasarımcıda veya kodda belirtilebilir. Tasarımcıda bilinen türleri belirtmek için, aşağıdaki resimde gösterildiği gibi bir <xref:System.ServiceModel.Activities.Receive> etkinlik için Özellikler **Penceresinde** bilinen türleri özelliğinin yanındaki elips düğmesini tıklatın.
  
 ![KnownTypes özellik iletişim kutusunun ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Bu, bilinen türleri aramanızı ve belirtmenizi sağlayan Tür Koleksiyonları Düzenleyicisi'ni görüntüler.  
  
 ![Type Collections Düzenleyicisinin ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Yeni **tür ekle** bağlantısını tıklatın ve bilinen türler koleksiyonuna eklemek için bir tür seçmek veya aramak için açılır açılır'ı kullanın. Kodda bilinen türleri belirtmek <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> için aşağıdaki örnekte gösterildiği gibi özelliği kullanın.  
  
```csharp
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```
