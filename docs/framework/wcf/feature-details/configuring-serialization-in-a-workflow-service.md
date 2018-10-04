---
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 67d8807e5ff45db2e8662586861d969e14ceaa8d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583716"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
İş akışı Hizmetleri, Windows Communication Foundation (WCF) Hizmetleri, bu nedenle, ya da kullanma seçeneği <xref:System.Runtime.Serialization.DataContractSerializer> (varsayılan) veya <xref:System.Xml.Serialization.XmlSerializer>. Kullanılacak serileştirici tür olmayan iş akışı yazma, hizmetleri, hizmet veya işlemi sözleşme belirtilir. WCF iş akışı hizmetleri oluştururken bu sözleşme kodu belirtmeyin, ancak bunlar sözleşme çıkarımı tarafından çalışma zamanında yerine oluşturulur. Sözleşme çıkarımı hakkında daha fazla bilgi için bkz: [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Seri hale getirici kullanarak belirtilen <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği. Bu tasarımcıda aşağıdaki çizimde gösterildiği gibi ayarlanabilir.  
  
 ![Seri hale getirici ayarlama](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 Seri hale getirici aşağıdaki örnekte gösterildiği gibi kodda de ayarlanabilir,  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 Bilinen türler, iş akışı hizmetlerinde de belirtilebilir. Bilinen türleri hakkında daha fazla bilgi için bkz. [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Bilinen türler Tasarımcısı'nda veya kod içinde belirtilebilir. Tasarımcıda bilinen türler belirtmek için Özellikler penceresinde KnownTypes özelliğin yanındaki üç nokta düğmesini tıklayın. bir <xref:System.ServiceModel.Activities.Receive> aşağıdaki çizimde gösterildiği gibi etkinlik.  
  
 ![KnownTypes özelliği](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 Bu, arayın ve bilinen türler belirtmek olanak tanıyacak türü koleksiyonları Düzenleyicisi'ni görüntüler.  
  
 ![Bilinen türleri ekleme](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 Tıklayın **yeni türü eklemek** bağlamak ve bilinen türlerin koleksiyonuna eklemek için açılan listeyi seçin veya bir tür için arama yapın. Kod kullanımda bilinen türler belirtmek için <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> aşağıdaki örnekte gösterildiği gibi özelliği.  
  
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
