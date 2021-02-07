---
description: 'Daha fazla bilgi edinin: bir Iş akışı hizmetinde serileştirme yapılandırma'
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: e268f82fc3c1f65086e3c6b112e481ad8abed070
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743245"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma

Workflow Services Windows Communication Foundation (WCF) hizmetlerdir ve bu nedenle, <xref:System.Runtime.Serialization.DataContractSerializer> (varsayılan) veya ' i kullanma seçeneğine sahiptir <xref:System.Xml.Serialization.XmlSerializer> . İş akışı olmayan hizmetleri yazarken, hizmet veya işlem sözleşmesinde kullanılacak seri hale getirici türü belirtilir. WCF iş akışı hizmetleri oluşturulurken bu sözleşmeleri kodda belirtmezsiniz, ancak bunun yerine sözleşme çıkarımı tarafından çalışma zamanında oluşturulmazlar. Sözleşme çıkarımı hakkında daha fazla bilgi için bkz.  [Iş akışında sözleşmeleri kullanma](using-contracts-in-workflow.md).  Seri hale getirici, özelliği kullanılarak belirtilir <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> . Bu, aşağıdaki çizimde gösterildiği gibi tasarımcıda ayarlanabilir.  
  
 ![Özellikler penceresinde SerializerOption özelliği ayarlanıyor.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Seri hale getirici, aşağıdaki örnekte gösterildiği gibi kodda de ayarlanabilir.  
  
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
  
  Bilinen türler, Iş akışı hizmetlerinde de belirtilebilir. Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md). Bilinen türler tasarımcıda veya kodda belirtilebilir. Tasarımcıda bilinen türleri belirtmek için, aşağıdaki çizimde gösterildiği gibi bir etkinliğin **Özellikler penceresinde** KnownTypes özelliğinin yanındaki üç nokta düğmesine tıklayın <xref:System.ServiceModel.Activities.Receive> .
  
 ![KnownTypes özelliği iletişim kutusunun ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Bu, bilinen türleri aramanızı ve belirtmenizi sağlayan tür koleksiyonları düzenleyicisini görüntüler.  
  
 ![Tür koleksiyonları düzenleyicisinin ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Bilinen türler koleksiyonuna eklemek üzere bir tür seçmek veya aramak için **yeni tür Ekle** bağlantısına tıklayın ve açılan eklentiyi kullanın. Kodda bilinen türleri belirtmek için, <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> Aşağıdaki örnekte gösterildiği gibi özelliğini kullanın.  
  
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
