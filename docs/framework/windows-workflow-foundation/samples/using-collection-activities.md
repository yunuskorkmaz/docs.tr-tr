---
title: Koleksiyon etkinlikleri kullanma
ms.date: 03/30/2017
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
ms.openlocfilehash: a92208583ddf1c0d5d85b5af6a250a15ac8851b9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422633"
---
# <a name="using-collection-activities"></a>Koleksiyon etkinlikleri kullanma
Bu örnek koleksiyon etkinlikleri kullanma işlemini gösterir (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, ve <xref:System.Activities.Statements.RemoveFromCollection%601>) uygulayan bir sınıf ile <xref:System.Collections.ICollection> arabirimi ve için bir koleksiyon üzerinden yineleme özel bir etkinlik oluşturma koleksiyondaki her öğenin içeriğini yazdırın. Olarak adlandırılan özel etkinlik `PrintCollection`, adlı bir koleksiyon öğesi üyelerinin konsola yazdırır `Numbers`.  
  
 Aşağıdaki tabloda, iş akışları için koleksiyon işleme sağlayan dört etkinliklerini açıklar.  
  
|Etkinlik adı|Açıklama|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|Öğe bir koleksiyona ekler.|  
|<xref:System.Activities.Statements.ClearCollection%601>|Bir koleksiyondaki tüm öğelerin temizler|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|Döndürür `true` belirtilmişse öğe koleksiyonda yok.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|Bir öğeyi koleksiyondan kaldırır.|  
  
 Örnek CodedWorkflow dizin ve diğer DesignerWorkflow dizininin altında altında iki çözümü oluşur. Bunlar aynı amacıyla etkinlikleri kullanarak iki farklı yolu gösterilmektedir.  
  
|Çözüm|Açıklama|Ana dosyaları|  
|-|-|-|  
|CodedWorkflow|Koleksiyon etkinlikleri programlı olarak çağırmak nasıl erişileceğini gösteren örnek istemci uygulaması.|**PrintCollection.cs**: Yardımcısı etkinliği bir koleksiyondaki her öğe konsola yazdırın.<br /><br /> **Program.cs**: program aracılığıyla bir dizi koleksiyon etkinlikleri içeren ve yürütülmeden bir sıralama etkinliği oluşturur.|  
|DesignerWorkflow|Koleksiyon etkinlikleri iş akışı Tasarımcısı'nda bildirimli yapmayı gösteren örnek istemci uygulaması.|**CollectionWorkflow.xaml**: Koleksiyon etkinlikleri kullanan tasarımcı ile bildirimli olarak oluşturulmuş bir iş akışı.<br /><br /> **PrintCollection.cs**: Yardımcısı etkinliği bir koleksiyondaki her öğe konsola yazdırın.<br /><br /> **Program.cs**: CollectionWorkflow.xaml içinde açıklanan iş akışı çağırır.|  
  
 Koleksiyonun öğe üyelerini serilerinden `Numbers` olarak adlandırılan özel tanımlı bir etkinlik kullanılarak konsolda yazdırılır `PrintCollection`.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Collection.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`