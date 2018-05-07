---
title: Koleksiyon etkinlikleri kullanma
ms.date: 03/30/2017
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
ms.openlocfilehash: 3c30a7fb46d9b155ec645a7b6845715d808d63b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-collection-activities"></a>Koleksiyon etkinlikleri kullanma
Bu örnek, koleksiyon etkinlikleri kullanılacak gösterilmiştir (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, ve <xref:System.Activities.Statements.RemoveFromCollection%601>) uygulayan bir sınıf ile <xref:System.Collections.ICollection> arabirimi ve bir koleksiyon üzerinden yineleme özel bir etkinlik oluşturma koleksiyondaki her öğe içeriklerinin yazdırmak. Adlı özel etkinlik `PrintCollection`, adlı bir koleksiyon öğesi üyeleri konsola yazdırır `Numbers`.  
  
 Aşağıdaki tabloda, iş akışları için koleksiyon işleme sağlamak dört etkinliklerini açıklar.  
  
|Etkinlik adı|Açıklama|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|Bir öğeyi koleksiyona ekler.|  
|<xref:System.Activities.Statements.ClearCollection%601>|Bir koleksiyondaki tüm öğeleri temizler|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|Döndürür `true` belirtilmişse öğe koleksiyonda yok.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|Bir öğeyi koleksiyondan kaldırır.|  
  
 Örnek CodedWorkflow dizin ve DesignerWorkflow dizini altındaki diğer altında iki çözümleri oluşur. Bunlar aynı amacıyla etkinlikleri kullanarak iki farklı yolu gösterilmektedir.  
  
|Çözüm|Açıklama|Ana dosyaları|  
|-|-|-|  
|CodedWorkflow|Koleksiyon etkinlikleri programlı olarak çağırmak nasıl gösteren örnek istemci uygulaması.|**PrintCollection.cs**: yardımcı etkinliği bir koleksiyondaki her öğe konsola yazdırabilirsiniz.<br /><br /> **Program.cs**: program aracılığıyla bir dizi koleksiyon etkinlikler içeren ve yürütülmeden dizisi etkinlik oluşturur.|  
|DesignerWorkflow|Koleksiyon etkinlikler iş akışı Tasarımcısı'nda bildirimli olarak nasıl gösteren bir örnek istemci uygulama.|**CollectionWorkflow.xaml**: bildirimli olarak koleksiyonu etkinlikleri kullanan Tasarımcısı ile oluşturulan bir iş akışı.<br /><br /> **PrintCollection.cs**: yardımcı etkinliği bir koleksiyondaki her öğe konsola yazdırabilirsiniz.<br /><br /> **Program.cs**: CollectionWorkflow.xaml içinde açıklanan iş akışını çağırır.|  
  
 Koleksiyon öğesi üyeleri serilerinden `Numbers` adlı özel tanımlanmış bir etkinlik kullanıldığında konsola yazdırılır `PrintCollection`.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Collection.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`