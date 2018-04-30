---
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47c66077da051fd70300e1961593e906fe8e77aa
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
İş akışı Hizmetleri [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri ve bu nedenle olması ya da kullanma seçeneğini <xref:System.Runtime.Serialization.DataContractSerializer> (varsayılan) veya <xref:System.Xml.Serialization.XmlSerializer>. Kullanılacak serileştirici tür olmayan iş akışı yazma, hizmetleri hizmet veya işlemi sözleşmenin belirtilir. Oluştururken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yok belirttiğiniz bu iş akışı hizmetleri kod sözleşmeleri, ancak bunlar sözleşme çıkarım tarafından çalışma zamanında yerine oluşturulur. Sözleşme çıkarım hakkında daha fazla bilgi için bkz: [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Seri hale getirici kullanarak belirtilen <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği. Bu tasarımcıda aşağıdaki çizimde gösterildiği gibi ayarlanabilir.  
  
 ![Seri hale getirici ayarı](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 Seri hale getirici aşağıdaki örnekte gösterildiği gibi kodunda da ayarlanabilir,  
  
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
  
 Bilinen türler iş akışı hizmetleri üzerinde de belirtilebilir. Bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Bilinen türler Tasarımcısı'nda veya kod belirtilebilir. Bilinen türler Tasarımcısı'nda belirtmek için için Özellikler penceresini KnownTypes özelliğinde yanındaki üç nokta düğmesini tıklatın bir <xref:System.ServiceModel.Activities.Receive> aşağıdaki çizimde gösterildiği gibi etkinlik.  
  
 ![KnownTypes özelliği](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 Bu, aramak ve bilinen türleri belirtmenize olanak sağlayacak türü koleksiyon Düzenleyicisi'ni görüntüler.  
  
 ![Bilinen türleri ekleme](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 Tıklatın **yeni türü eklemek** bağlantı ve bilinen türleri koleksiyona eklemek için seçin ya da arama türü için aşağı açılan kullanın. Bilinen türler kodu kullanımda belirtmek için <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> aşağıdaki örnekte gösterildiği gibi özelliği.  
  
```  
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
  
 Bkz: seri hale getirme iş akışı hizmeti için yapılandırma gösteren tam bir kod örneğini görmek için [iş akışı hizmetleri iletilerinde biçimlendirme](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).
