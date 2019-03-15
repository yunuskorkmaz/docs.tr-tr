---
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 0e0f03a30aa8e8679cf849aa75948e0bc2314fe5
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843944"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
İş akışı Hizmetleri, Windows Communication Foundation (WCF) Hizmetleri, bu nedenle, ya da kullanma seçeneği <xref:System.Runtime.Serialization.DataContractSerializer> (varsayılan) veya <xref:System.Xml.Serialization.XmlSerializer>. Kullanılacak serileştirici tür olmayan iş akışı yazma, hizmetleri, hizmet veya işlemi sözleşme belirtilir. WCF iş akışı hizmetleri oluştururken bu sözleşme kodu belirtmeyin, ancak bunlar sözleşme çıkarımı tarafından çalışma zamanında yerine oluşturulur. Sözleşme çıkarımı hakkında daha fazla bilgi için bkz: [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Seri hale getirici kullanarak belirtilen <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği. Bu tasarımcıda aşağıdaki çizimde gösterildiği gibi ayarlanabilir.  
  
 ![SerializerOption özelliği, Özellikler penceresinde ayarlanıyor.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Seri hale getirici aşağıdaki örnekte gösterildiği gibi kodda de ayarlanabilir,  
  
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
  
  Bilinen türler, iş akışı hizmetlerinde de belirtilebilir. Bilinen türleri hakkında daha fazla bilgi için bkz. [veri sözleşme bilinen türleri](data-contract-known-types.md). Bilinen türler Tasarımcısı'nda veya kod içinde belirtilebilir. Tasarımcıda bilinen türler belirtmek için KnownTypes özelliğin yanındaki üç nokta düğmesine tıklayın. **Özellikler penceresi** için bir <xref:System.ServiceModel.Activities.Receive> aşağıdaki çizimde gösterildiği gibi etkinlik.   
  
 ![KnownTypes özellik iletişim kutusunun ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Bu, aramak ve bilinen türlerini belirtmek izin veren türü koleksiyonları Düzenleyici görüntüler.  
  
 ![Tür Koleksiyonu Düzenleyicisi ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
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
